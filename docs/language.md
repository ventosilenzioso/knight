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
system::config() { ... };          // server.cfg configuration
namespace::callback(params) { ... }; // engine callback
function name(params) { ... };     // helper function
let name = expr;                   // variable
```

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
| `+= -= *= /= %=` | compound assignment |

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

> There is no `while`/`for` loop in this version. Iterate with `len`/`at` and a
> counter (see [`builtins.md`](builtins.md)).

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

`system::config()` writes `server.cfg` keys at load time:

```knight
system::config() {
    server.name = "My Server";
    server.max_players = 100;
    server.port = 7777;
};
```

All keys are in [`configuration.md`](configuration.md).

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

- Parse/type errors are reported as `line:column: message`; the validator exits
  non-zero.
- `-check` runs the full preprocess/parse/resolve pass.
- `-ast` prints the parsed syntax tree.

```bash
knight -check examples/full.sa
knight -ast examples/minimal.sa
```
