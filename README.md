# Knight

**Knight** is the statically-typed scripting language used by **Knight**, the
from-scratch SA-MP 0.3.7 server written in Go. Gamemodes are authored as a
single `.sa` file: you declare typed event handlers, configure the server, and
call engine natives through the `sa.*` namespace.

This repository is the **public language distribution**: the language
reference, a set of runnable examples, and prebuilt copies of the standalone
`knight` validator. It intentionally does **not** contain the compiler
implementation.

```
bin/       prebuilt knight validator (linux/macos/windows)
examples/  runnable .sa gamemodes
docs/      language reference
```

## The validator

`knight` checks a `.sa` file without running a server. It resolves
`#include`s, lexes, parses, and type-checks against the engine's native API.

```bash
./bin/knight-linux-amd64 -check examples/full.sa
# ok: 12 events, 1 config blocks

./bin/knight-linux-amd64 -ast examples/minimal.sa   # dump the parsed AST
```

Every shipped `examples/*.sa` passes `-check`.

## Hello, Knight

```knight
player::connect() {
    self.message("Welcome, {self.name}!");
};

player::spawn() {
    self.set_health(100.0);
};
```

Events are declared as `namespace::name(params) { ... };` — the trailing `;`
is required. `self` is bound to the event's subject (e.g. the `Player` for
`player::*` handlers). String literals interpolate expressions with `{...}`.

## Language at a glance

- **Statically typed** — `int`, `float`, `string`, `bool`, and engine object
  handles `Player`, `Vehicle`, `Object`, `TextDraw`.
- **Typed bindings** — `let x = 1;`, optional annotation `let x: float = 1.0;`.
- **Operators** — `and/or/not` or `&&/||/!`; `~=` and `!=` both mean "not
  equal"; compound assignment (`+=`, `-=`, `*=`, `/=`) for numeric fields.
- **String interpolation** — `"score={player.score}"`, escape braces with
  `\{` / `\}`.
- **Includes** — `#include <knight>` is optional; custom files with
  `#include <path.sa>` (cycles are detected).
- **Config block** — `system::config() { server.name = "..."; ... };` writes
  `server.cfg` fields.

See [`docs/language.md`](docs/language.md) for the full syntax, the event
catalogue, object fields/methods, and configuration keys. The standard library
is documented in [`docs/builtins.md`](docs/builtins.md).

## Events

Handlers are the entry points the server calls. The complete set is documented
in [`docs/events.md`](docs/events.md); the namespaces are:

| Namespace | Purpose |
|---|---|
| `system` | `start`, `stop`, `config` |
| `player` | connect/spawn/death/chat/command, vehicle, sync, aim, combat, input, class/spawn requests |
| `vehicle` | factory `create`, `spawn`, `death`, `damage_status_update` |
| `world` | checkpoints, objects, areas, actors, pickups |
| `dialog` | `response` |
| `textdraw` | factory `create`, `click` |
| `timer` | `every` |

## Native API

Inside any handler you can call the engine directly as `sa.<Native>(...)`
(the full SA-MP native set — players, vehicles, objects, pickups, dialogs,
textdraws, gang zones, 3D labels, actors, checkpoints, database, crypto,
streamer, formatting). See [`docs/natives.md`](docs/natives.md).

Prefer the typed surface where it exists — `player.health`,
`vehicle.repair()`, `player.show_dialog(...)` — and fall back to `sa.*` for the
long tail.

## Examples

| File | What it shows |
|---|---|
| `examples/minimal.sa` | Smallest loadable gamemode |
| `examples/full.sa` | Config block, classes, chat, commands, death handling |
| `examples/bare.sa` | Realistic gamemode: SQLite auth, dialogs, anticheat, admin commands |
| `examples/builtins.sa` | Standard library: strings, math, arrays and maps |

Run any of them with the Knight server:

```bash
knight-server -cfg server.cfg -gamemode examples/full.sa
```

## Built-in functions

Knight ships a standard library of language-level helpers — conversions
(`int`, `float`, `str`, `bool`), type predicates, math (`abs`, `min`, `max`,
`clamp`, `sqrt`, `pow`, `random`), string helpers (`upper`, `lower`, `trim`,
`substr`, `split`, `join`, `replace`), and collections (`array`, `map`, `push`,
`pop`, `at`, `keys`, `values`, `has`, `del`). See
[`docs/builtins.md`](docs/builtins.md).

## Verifying

```bash
for f in examples/*.sa; do ./bin/knight-linux-amd64 -check "$f" || exit 1; done
```

## License

The examples and documentation in this repository are provided for use with
Knight. The `knight` binaries are distributed as prebuilt tools.
