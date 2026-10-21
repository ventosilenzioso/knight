# Knight — Language Guide

Knight is a small, statically-typed language. A gamemode is one `.sa` file
(plus optional includes). The validator resolves includes, lexes, parses and
type-checks the file.

The API is **native-first**: gameplay calls are plain global functions like
`SetPlayerHealth(playerid, 100.0)` and `GetPlayerMoney(playerid)`. Callbacks
receive `playerid` explicitly; there is no `self`, no `sa.` prefix, and no
method syntax.

---

## 1. Files and includes

- A gamemode may be a **single self-contained `.sa` file**.
- `#include <knight>` is **optional**; all natives and types are built in.
- Custom includes: `#include <path/to/file.sa>`, resolved relative to the
  including file. Circular includes are rejected.
- Comments: `// line` and `/* block */`.

---

## 2. Declarations

```knight
system::config() { ... };          // server configuration (server.cfg is optional)
namespace::callback(params) { ... }; // engine callback
on namespace::callback(params) { ... }; // same callback, declarative form
function name(params) { ... };     // helper function
export function name(params) { ... }; // helper callable across modules
const NAME = expr;                 // constant (reassignment is an error)
let name = expr;                   // variable
```

### Function parameters

Parameters are typed and checked at compile time. Trailing parameters may have
default values, and a final `...rest` parameter collects extra arguments:

```knight
function heal(Player target, float hp = 100.0, int times = 1) { ... }
function total(int first, ...rest) {
    let sum = first;
    for (let n in rest) { sum += n; }
    return sum;
}

heal(playerid);                  // hp = 100.0, times = 1
total(1, 2, 3, 4);               // 10
```

Supported parameter types: `int`, `float`, `string`, `bool`, `array`, `map`,
`Player`, `Vehicle`, `Object`, `TextDraw`. Defaults are evaluated when the
function is called. Passing the wrong type, too few arguments or too many
arguments is a compile error. A `Player` parameter also accepts an integer id.

### Constants

```knight
const MAX_HP = 100;
const RATIO: float = 0.5;
```

A `const` can be declared at module level or inside a function. Assigning to it
is rejected at compile time.

### Modules

```knight
// modules/economy.sa
module "economy" { version: "1.0.0"; author: "Knight"; };

let balances = {};

function economyAdd(int id, int amount) { balances[id] = at(balances, id) + amount; }
export function economyBalance(int id) { return at(balances, id); }
```

```knight
// Gamemodes/main.sa
import "economy";

player::command("/bal") {
    SendClientMessage(playerid, "Saldo: {economyBalance(playerid)}");
};
```

An `import` loads a module once; circular imports are rejected. Every top-level
`function` in the program is callable from any file; `export` is documentation
for readers. See [`plugins.md`](plugins.md).

> The trailing `;` after a callback/function/config block **is required**.

The alternate callback form is also accepted:

```knight
if (player::connect(int playerid)) {
    SendClientMessage(playerid, "Hello!");
};
```

---

## 3. Types

| Type | Description |
|---|---|
| `int` | 64-bit signed integer (decimal or `0x` hex) |
| `float` | 64-bit float |
| `string` | UTF-8 text |
| `bool` | `true` / `false` |
| `Player`, `Vehicle`, `Object`, `TextDraw` | engine handle types (parameters) |
| `array`, `map` | ordered list / string-keyed dictionary |
| `null` | absence of a value |

`playerid` is an `int`. Handle types (`Player`, `Vehicle`, ...) are used to
type callback parameters; natives take and return plain ids.

```knight
let score: int = 0;
let speed = 1.5;
let name = "CJ";
let classid = 0x10;
```

---

## 4. Variables and scope

```knight
let hp = 100;
hp = 90;
hp += 5;      // also -= *= /= %=
```

`let` creates a reassignable binding. Module-level variables are shared across
callbacks and live for the whole server lifetime.

```knight
let totalPlayers = 0;
player::connect(int playerid) { totalPlayers += 1; };
player::disconnect(int playerid) { totalPlayers -= 1; };
```

---

## 5. Expressions and operators

| Operators | Notes |
|---|---|
| `+ - * / %` | arithmetic (`+` also concatenates strings) |
| `== != ~=` | equality; `~=` is an alias for `!=` |
| `< <= > >=` | comparison |
| `and or not` | logical, also `&&`, `\|\|`, `!` |
| `& \| ^ ~ << >>` | bitwise and/or/xor/not and shifts |
| `? :` | ternary (`hp > 50 ? "ok" : "low"`) |
| `+= -= *= /= %=` | compound assignment |
| `&= \|= ^= <<= >>=` | compound bitwise assignment |

Precedence, highest first: unary (`! ~ - +`) → `* / %` → `+ -` → `<< >>` →
comparisons → equality → `&` → `^` → `\|` → `and` → `or` → `?:`.

---

## 6. Control flow

```knight
if (cond) {
    ...
} else if (other) {
    ...
} else {
    ...
}
```

`return expr;` returns from the callback. Boolean callbacks use the return
value as a veto — `player::request_spawn` returning `false` blocks the spawn.

### Loops

```knight
// while
let i = 0;
while (i < 10) {
    i += 1;
}

// do..while: runs at least once
do {
    i -= 1;
} while (i > 0);

// C-style for
for (let n = 0; n < 5; n += 1) {
    if (n == 3) { break; }
}

// iterate an array
let names = ["amy", "bob"];
for (let name in names) { ... }

// array with index
for (let index, name in names) { ... }

// map: keys in sorted order
let scores = { "amy": 10, "bob": 20 };
for (let key in scores) {
    SendClientMessage(playerid, "{key} = {scores[key]}");
}

// map with value
for (let key, value in scores) { ... }

// skip iterations
for (let n = 0; n < 20; n += 1) {
    if (n % 2 == 0) { continue; }
}
```

`break` leaves the nearest loop or `switch`; `continue` jumps to the next
iteration. Using them outside a loop is a compile error.

### switch

```knight
switch (classid) {
    case 0:
        SendClientMessage(playerid, "Medic");
    case 1:
        SendClientMessage(playerid, "Police");
    default:
        SendClientMessage(playerid, "Civilian");
}
```

There is **no fall-through**: the first matching arm runs, then the switch ends.
`case` values may be numbers, strings or `null`.

---

## 7. Literals

```knight
let n = 42;
let h = 0xFF00FF00;
let f = 3.14;
let b = true;
let z = null;
let ms = 500ms;                  // duration -> milliseconds
let a = [1, 2, 3];               // array
let m = { "hp": 100, name: "CJ" }; // map
let c = a[1:3];                  // slice -> [2, 3]
let d = "Knight"[1:4];           // slice -> "nig"
let e = a[:2];                   // from the start
let f = a[1:];                   // to the end
let g = "Knight"[2];             // single character -> "i"

let x = 0;
let y = 0;
x, y = 7;                        // comma assignment: both become 7
a[0] = 10;
m["score"] = 5;
```

Engine constants are bare integers: `SPECIAL_ACTION_DANCE1`, `BONE_HEAD`,
`MAX_PLAYERS`, `INVALID_PLAYER_ID` (see [`natives.md`](natives.md)).

---

## 8. Strings and interpolation

```knight
let who = PlayerName(playerid);
SendClientMessage(playerid, "Welcome, {who}!");
SendClientMessage(playerid, "Uppercase: {upper(who)}");
SendClientMessage(playerid, "Literal braces: \{ \}");
```

Escapes: `\n`, `\t`, `\r`, `\\`, `\"`, `\{`, `\}`. Interpolation may contain
calls, parentheses and nested string literals.

---

## 9. Calling natives

Natives are global functions:

```knight
player::spawn(int playerid) {
    SetPlayerHealth(playerid, 100.0);
    SetPlayerArmour(playerid, 50.0);
    SendClientMessage(playerid, "HP {GetPlayerHealth(playerid)}");
};

player::command("/give", int amount) {
    GivePlayerMoney(playerid, amount);
};
```

The full list is in [`natives.md`](natives.md).

Plugin natives (for example the bundled JSON plugin) are called the same way:

```knight
let doc = JsonParse("\{\"name\":\"CJ\"\}");
let name = JsonGetString(doc, "name");
JsonFree(doc);
```

Functions contributed by a script plugin or an imported module are also plain
calls: `economyBalance(playerid)`.

### Calling a function by name

```knight
function add(int a, int b) { return a + b; }

let sum = CallRemoteFunction("add", 2, 3);   // 5
let big = CallLocalFunction("isBig", 50);    // 1
```

The result is always an int: numbers truncate, `true`/`false` become `1`/`0`, a
string returns its length, and `null` returns `0`. An unknown name is logged and
returns `0`.

---

## 10. Commands

```knight
player::command("/heal") {
    SetPlayerHealth(playerid, 100.0);
};

player::command("/give", int amount, string reason) {
    GivePlayerMoney(playerid, amount);
    SendClientMessage(playerid, "Got {amount}: {reason}");
};
```

Arguments are parsed and bound by declared type.

---

## 11. Configuration

`system::config()` configures the server at load time. `server.cfg` is optional:
values declared here always win, and code can be the only configuration source.

```knight
system::config() {
    server.name = "My Server";
    server.max_players = 100;
    server.port = 7777;
    server.connect_timeout = 20;
    server.plugins = ["plugins", "modules/anticheat.sa"];
};
```

The values are readable at runtime (`"{server.name}"`). All keys, precedence and
the `-cfg ""` flag are in [`configuration.md`](configuration.md).

---

## 12. Built-in functions

Language helpers (conversions, math, strings, arrays, maps) are available
without any include. See [`builtins.md`](builtins.md).

```knight
let parts = split(PlayerName(playerid), "_");
SendClientMessage(playerid, "Hello {upper(join(parts, " "))}!");
```

---

## 13. Callbacks

The complete callback list with parameters is in
[`callbacks.md`](callbacks.md).

```knight
system::start() { ... };
player::connect(int playerid) { SendClientMessage(playerid, "Hi!"); };
player::chat(int playerid, string message) { return true; }; // relay chat
dialog::response(int playerid, int id, bool accepted, string input, int listitem) { ... };
```

---

## 14. Helpers, timers and async results

```knight
function onDbResult(result, err) {
    if (err == "") {
        let rows = cache_get_row_count(result);
        Log("rows=" + str(rows));
    }
}

let db = sqlite_open("scriptfiles/data.db");
sqlite_query_async(db, "onDbResult", "SELECT * FROM accounts");
```

---

## 15. Errors

A runtime failure on one line of a callback is logged (`script error at
LINE:COL: ...`) and skipped; the rest of the callback still runs and the server
keeps processing that player. `return`, `break` and `continue` are unaffected.
Unknown natives and type errors are caught before the server starts.

- Parse/type errors are reported as `line:column: message`; the validator exits
  non-zero.
- `-check` runs the full preprocess/parse/resolve pass.
- `-ast` prints the parsed syntax tree.

```bash
knight -check examples/full.sa
knight -ast examples/minimal.sa
```
