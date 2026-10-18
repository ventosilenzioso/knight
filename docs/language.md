# Knight — Language Guide

Knight is a small, statically-typed language. A gamemode is one `.sa` file
(plus optional includes). The validator resolves includes, parses the file,
and type-checks every handler and native call against the engine API.

---

## 1. Files and includes

- A gamemode may be a **single self-contained `.sa` file**.
- `#include <knight>` is **optional**; all `sa.*` natives and object types are
  built in.
- Custom includes: `#include <path/to/file.sa>`, resolved relative to the
  including file. Circular includes are rejected with an error.
- Comments use `// line` and `/* block */`.

---

## 2. Declarations

Top-level declarations are:

```knight
system::config() { ... };          // server.cfg configuration
namespace::event(params) { ... };  // engine event handler
function name(params) { ... }      // plain helper function
let name = expr;                   // module-level variable
```

Handlers declared as events (`player::connect`, etc.) are dispatched by the
server. `function` helpers are ordinary callables, also reachable by name from
async database callbacks and timers.

> The trailing `;` after an event/function body **is required**.

---

## 3. Types

| Type | Description |
|---|---|
| `int` | 64-bit signed integer |
| `float` | 64-bit float |
| `string` | UTF-8 text |
| `bool` | `true` / `false` |
| `Player`, `Vehicle`, `Object`, `TextDraw` | engine object handles |
| `null` | absence of a value |

Types are inferred for `let` bindings; you may annotate explicitly:

```knight
let score: int = 0;
let speed = 1.5;          // inferred float
let name = "CJ";          // inferred string
```

`null` comparisons are allowed against object handles and nullable results:

```knight
if (killer != null) {
    self.message("Killed by {killer.name}");
}
```

---

## 4. Variables and scope

```knight
let hp = 100;        // immutable binding
let count = 0;
count = count + 1;   // reassignment
count += 1;          // compound assignment (+= -= *= /=)
```

Module-level `let` variables are shared across handlers and persist for the
lifetime of the server — the usual place for per-gamemode state.

---

## 5. Operators

| Operators | Notes |
|---|---|
| `+ - * / %` | arithmetic |
| `== != ~=` | equality; `~=` is an alias for `!=` |
| `< <= > >=` | comparison |
| `and or not` | logical, also `&&`, `\|\|`, `!` |
| `+= -= *= /=` | compound assignment |

Arithmetic on `int`/`float` is checked by the resolver; mixing types where it
would be ambiguous is a compile error.

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

while (cond) {
    ...
}

for (let i = 0; i < 10; i += 1) {
    ...
}
```

A block is a `{ ... }` sequence of statements. `return expr;` returns from the
current function/handler. Handlers with a `bool` return type use it as a veto
(for example `player::request_spawn()` returning `false` blocks the spawn).

---

## 7. Strings and interpolation

```knight
let who = "CJ";
self.message("Welcome, {who}!");          // any expression inside { }
self.message("Score: {player.score}");    // member access works too
self.message("Literal braces: \{ \}");     // escaped
```

`+` concatenates strings. `{...}` interpolates the value of any expression.

---

## 8. Objects, fields, methods

Engine objects expose typed fields and methods:

```knight
player::spawn() {
    self.health = 100.0;          // field write
    self.set_position(1958.4, 1343.2, 15.4);
    let x = self.x;               // field read
    self.message("x = {x}");
};

world::object_create(int model, float x, float y, float z) {
    // factory: returns an Object
    let obj = sa.CreateObject(model, x, y, z, 0.0, 0.0, 0.0, 200.0);
    obj.set_rotation(0.0, 0.0, 90.0);
    return obj;
};
```

See [`natives.md`](natives.md) for the full field/method catalogue per object
type. The `sa.*` namespace exposes the raw engine native set alongside the
typed surface.

---

## 9. Configuration block

`system::config()` writes `server.cfg` keys at load time:

```knight
system::config() {
    server.name = "My Server";
    server.max_players = 100;
    server.port = 7777;
    server.gamemode = "mygm 1";
    server.weather = 10;
    server.world_time = 12;
    server.gravity = 0.008;
    server.stream_distance = 300.0;
    server.announce = true;
};
```

The mapping from keys to `server.cfg` entries is listed in
[`natives.md`](natives.md#systemconfig-keys).

---

## 10. Events

An event handler is called by the engine. `self` is bound to the event's
subject. The complete list, with parameters and `self` type, is in
[`events.md`](events.md). Examples:

```knight
system::start() { ... };

player::connect() { ... };
player::chat(string message) { return true; };   // true = relay as chat
player::command("/heal") { self.health = 100.0; };
dialog::response(int id, bool accepted, string input, int listitem) { ... };

timer::every() { ... };                           // periodic callback context
```

`player::command("/name", int a, float b, string c)` binds command
arguments by declared type.

---

## 11. Timers and async results

Named `function` helpers can be invoked by the engine as callbacks:

```knight
function onDbResult(result, err) {
    if (err == "") {
        let rows = sa.cache_get_row_count(result);
        self.message("rows={rows}");
    }
}

let db = sa.sqlite_open("scriptfiles/data.db");
sa.sqlite_query_async(db, "onDbResult", "SELECT ...");
```

---

## 12. Errors

- Parse/type errors are reported with `file:line:column` and a message; the
  validator exits non-zero.
- `-check` performs the full resolve/type-check pass; `-ast` prints the parsed
  syntax tree for tooling.

```bash
knight -check examples/full.sa
knight -ast examples/minimal.sa
```
