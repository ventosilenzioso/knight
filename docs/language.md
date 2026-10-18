# Knight — Language Guide

Knight is a small, statically-typed language. A gamemode is one `.sa` file
(plus optional includes). The validator resolves includes, lexes, parses and
type-checks every handler and native call against the engine API.

---

## 1. Files and includes

- A gamemode may be a **single self-contained `.sa` file**.
- `#include <knight>` is **optional**; all `sa.*` natives and object types are
  built in.
- Custom includes: `#include <path/to/file.sa>`, resolved relative to the
  including file. Circular includes are rejected with an error.
- Comments: `// line` and `/* block */`.

---

## 2. Declarations

Top-level declarations:

```knight
system::config() { ... };          // server.cfg configuration
namespace::event(params) { ... };  // engine event handler
function name(params) { ... };     // plain helper function
let name = expr;                   // module-level variable
```

Event handlers are dispatched by the server; `function` helpers are ordinary
callables that can also be invoked by name from async database callbacks and
timers.

> The trailing `;` after an event/function/config block **is required**.

The alternate event form is also accepted:

```knight
if (player::connect()) {
    ...
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
| `Player`, `Vehicle`, `Object`, `TextDraw` | engine object handles |
| `array`, `map` | ordered list / string-keyed dictionary |
| `null` | absence of a value |

Types are inferred for `let`; annotate explicitly when needed:

```knight
let score: int = 0;
let speed = 1.5;     // float
let name = "CJ";     // string
let classid = 0x10;  // 16
```

---

## 4. Variables and scope

```knight
let hp = 100;        // declare
hp = 90;             // reassign
hp += 5;             // compound assignment (+= -= *= /= %=)
```

`let` creates a variable that **can be reassigned** (it is a binding, not a
constant). Module-level variables are shared across handlers and live for the
whole server lifetime — the usual place for gamemode state.

```knight
let totalPlayers = 0;

player::connect() { totalPlayers += 1; };
player::disconnect() { totalPlayers -= 1; };
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

The resolver checks operand/assignment types; assigning a `string` to an
`int` field is a compile error.

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

`return expr;` returns from the current function/handler. Handlers with a
`bool` return type use it as a veto — for example `player::request_spawn()`
returning `false` blocks the spawn.

> There is no `while`/`for` loop in the current language version. Iterate over
> collections with the built-ins `len`, `at` and hand-written counters (see
> `builtins.md`).

---

## 7. Literals

```knight
let n = 42;              // int
let h = 0xFF00FF00;      // hex int
let f = 3.14;            // float
let b = true;            // bool
let z = null;            // null
let ms = 500ms;          // duration literal (500ms, 2s, 3m, 1h) -> milliseconds int
let a = [1, 2, 3];       // array
let m = { "hp": 100, name: "CJ" };  // map (bare ident keys are strings)
```

Array and map literals can be indexed and assigned:

```knight
a[0] = 10;
m["score"] = 5;
let first = a[0];
```

---

## 8. Strings and interpolation

```knight
let who = "CJ";
self.message("Welcome, {who}!");           // any expression inside { }
self.message("Score: {player.score}");     // member access
self.message("Uppercase: {upper(who)}");   // nested calls and "nested strings"
self.message("Literal braces: \{ \}");      // escaped
```

Escapes: `\n`, `\t`, `\r`, `\\`, `\"`, `\{`, `\}`. Interpolation may contain
parentheses and nested string literals.

---

## 9. Objects, fields, methods, factories

Engine objects expose typed fields and methods:

```knight
player::spawn() {
    self.health = 100.0;                 // field write
    self.set_position(1958.4, 1343.2, 15.4);
    let x = self.x;                      // field read
    self.message("x = {x}");
};

world::object_create(int model, float x, float y, float z) {
    let obj = Object.create(model, x, y, z, 0.0, 0.0, 0.0, 200.0);
    obj.set_rotation(0.0, 0.0, 90.0);
    return obj;
};
```

The full field/method catalogue is in [`natives.md`](natives.md). The raw
`sa.*` native set is available alongside the typed surface, e.g.
`sa.SetPlayerHealth(self.id, 100.0)`.

---

## 10. Commands

Declare a command handler with a leading `/name` literal and typed arguments:

```knight
player::command("/heal") {
    self.health = 100.0;
};

player::command("/give", int amount, string reason) {
    self.money += amount;
    self.message("Got {amount}: {reason}");
};
```

Command arguments are parsed and bound by declared type (`int`, `float`,
`string`).

---

## 11. Configuration

`system::config()` writes `server.cfg` keys at load time:

```knight
system::config() {
    server.name = "My Server";
    server.max_players = 100;
    server.port = 7777;
    server.weather = 10;
    server.world_time = 12;
};
```

All supported keys are listed in [`configuration.md`](configuration.md).

---

## 12. Built-in functions

A standard library is available without any include — conversions, predicates,
math, string and collection helpers. See [`builtins.md`](builtins.md).

```knight
let parts = split(player.name, "_");
player.message("Hello {upper(join(parts, " "))}, roll {random(1,6)}");
```

---

## 13. Events

The complete event list with parameters and `self` type is in
[`events.md`](events.md). Examples:

```knight
system::start() { ... };
player::connect() { ... };
player::chat(string message) { return true; };   // true = relay as chat
dialog::response(int id, bool accepted, string input, int listitem) { ... };
```

---

## 14. Helpers, timers and async results

Named `function` helpers can be invoked by the engine as callbacks:

```knight
function onDbResult(result, err) {
    if (err == "") {
        let rows = sa.cache_get_row_count(result);
        sa.Log("rows=" + str(rows));
    }
}

let db = sa.sqlite_open("scriptfiles/data.db");
sa.sqlite_query_async(db, "onDbResult", "SELECT * FROM accounts");
```

---

## 15. Errors

- Parse/type errors are reported as `line:column: message`; the validator exits
  non-zero.
- `-check` runs the full preprocess/parse/resolve pass.
- `-ast` prints the parsed syntax tree for tooling.

```bash
knight -check examples/full.sa
knight -ast examples/minimal.sa
```
