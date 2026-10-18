# Knight

**Knight** is a statically-typed scripting language for the **Knight** SA-MP
0.3.7 server (written in Go). Gamemodes are authored as a single `.sa` file: you
declare typed event handlers, configure the server, and call engine natives
through the `sa.*` namespace.

This repository is the **public language distribution**: the language
reference, a set of runnable examples, and prebuilt copies of the standalone
`knight` validator. It intentionally does **not** contain the compiler
implementation.

```
bin/       prebuilt knight validator (linux/macos/windows)
docs/      language, events, natives, built-ins, configuration
examples/  runnable .sa gamemodes
```

## Documentation

| Document | Contents |
|---|---|
| [`docs/language.md`](docs/language.md) | Syntax: declarations, types, operators, literals, strings, objects, commands |
| [`docs/builtins.md`](docs/builtins.md) | Standard library: conversions, math, strings, arrays, maps |
| [`docs/events.md`](docs/events.md) | Every event: when it fires, parameters, `self` type and return |
| [`docs/natives.md`](docs/natives.md) | Object fields/methods/factories with descriptions, `server.*`, and all 498 natives explained |
| [`docs/configuration.md`](docs/configuration.md) | `system::config()` fields and their `server.cfg` keys |

## The validator

`knight` checks a `.sa` file without running a server. It resolves
`#include`s, lexes, parses, and type-checks against the engine's native API.

```bash
./bin/knight-linux-amd64 -check examples/full.sa
# ok: 18 events, 1 config blocks

./bin/knight-linux-amd64 -ast examples/minimal.sa   # dump the parsed AST
```

Every shipped `examples/*.sa` passes `-check`.

## Hello, Knight

```knight
player::connect() {
    self.message("Welcome, {self.name}!");
};

player::spawn() {
    self.health = 100.0;
};
```

Events are declared as `namespace::name(params) { ... };` — the trailing `;`
is required. `self` is bound to the event's subject (e.g. the `Player` for
`player::*` handlers). String literals interpolate expressions with `{...}`.

## Language at a glance

- **Statically typed** — `int`, `float`, `string`, `bool`, engine object
  handles (`Player`, `Vehicle`, `Object`, `TextDraw`), plus `array` and `map`.
- **Typed bindings** — `let x = 1;`, optional annotation `let x: float = 1.0;`,
  reassignable and shared at module scope.
- **Operators** — `and/or/not` or `&&/||/!`; `~=` and `!=` both mean "not
  equal"; compound assignment (`+=`, `-=`, `*=`, `/=`, `%=`).
- **Literals** — hex ints (`0xFF`), durations (`500ms`, `2s`), arrays
  (`[1,2,3]`), maps (`{ name: "CJ" }`).
- **String interpolation** — `"score={player.score}"`, nested calls and strings
  allowed, escape braces with `\{` / `\}`.
- **Includes** — `#include <knight>` is optional; custom files with
  `#include <path.sa>` (cycles are detected).
- **Commands** — `player::command("/give", int amount) { ... };`.
- **Config block** — `system::config() { server.name = "..."; ... };`.

## Built-in functions

A standard library ships with every gamemode — conversions (`int`, `float`,
`str`, `bool`, `typeof`), type predicates, math (`abs`, `min`, `max`, `clamp`,
`sqrt`, `pow`, `random`), strings (`upper`, `lower`, `trim`, `substr`, `split`,
`join`, `replace`, `contains`), collections (`array`, `map`, `push`, `pop`,
`at`, `keys`, `values`, `has`, `del`), and utilities (`format`, `distance`).
See [`docs/builtins.md`](docs/builtins.md).

## Events

Handlers are the entry points the server calls. The complete list is in
[`docs/events.md`](docs/events.md); the namespaces are:

| Namespace | Purpose |
|---|---|
| `system` | `start`, `stop`, `config` |
| `player` | connect/spawn/death/chat/command, vehicles, sync, aim, combat, class/spawn requests |
| `vehicle` | factory `create`, `spawn`, `death`, `damage_status_update` |
| `world` | checkpoints, objects, areas, actors, pickups, actor damage |
| `dialog` | `response` |
| `textdraw` | factory `create`, `click` |
| `timer` | `every` |

## Native API

Inside any handler you can call the engine directly as `sa.<Native>(...)`.
The full SA-MP native set (498 functions) is available — players, vehicles,
objects, pickups, dialogs, textdraws, gang zones, 3D labels, actors,
checkpoints, database, crypto, streamer, formatting. The typed object surface
(`player.health`, `vehicle.repair()`, `player.show_dialog(...)`) is documented
in [`docs/natives.md`](docs/natives.md) alongside the native index.

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

## Verifying

```bash
for f in examples/*.sa; do ./bin/knight-linux-amd64 -check "$f" || exit 1; done
```

## License

The examples and documentation in this repository are provided for use with
Knight. The `knight` binaries are distributed as prebuilt tools.
