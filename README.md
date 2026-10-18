# Knight

**Knight** is a statically-typed scripting language for the **Knight** SA-MP
0.3.7 server. Gamemodes are authored as a single `.sa` file: you declare
callbacks, configure the server, and call native functions directly by name.

This repository is the **public language distribution**: the language
reference, runnable examples, and prebuilt copies of the standalone `knight`
validator. It intentionally does **not** contain the compiler implementation.

```
bin/       prebuilt knight validator (linux/macos/windows)
docs/      language, callbacks, natives, built-ins, configuration
examples/  runnable .sa gamemodes
```

## Documentation

| Document | Contents |
|---|---|
| [`docs/language.md`](docs/language.md) | Syntax: declarations, types, operators, literals, strings, commands |
| [`docs/natives.md`](docs/natives.md) | All native functions with descriptions and engine constants |
| [`docs/callbacks.md`](docs/callbacks.md) | Every callback: when it fires, parameters and return |
| [`docs/builtins.md`](docs/builtins.md) | Standard library: conversions, math, strings, arrays, maps |
| [`docs/configuration.md`](docs/configuration.md) | `system::config()` fields and their `server.cfg` keys |

## The validator

`knight` checks a `.sa` file without running a server. It resolves
`#include`s, lexes, parses, and type-checks.

```bash
./bin/knight-linux-amd64 -check examples/full.sa
# ok: 18 events, 1 config blocks

./bin/knight-linux-amd64 -ast examples/minimal.sa   # dump the parsed AST
```

Every shipped `examples/*.sa` passes `-check`.

## Hello, Knight

Natives are global functions — no namespace, no `self`:

```knight
player::connect(int playerid) {
    SendClientMessage(playerid, "Welcome, {PlayerName(playerid)}!");
};

player::spawn(int playerid) {
    SetPlayerHealth(playerid, 100.0);
};
```

Callbacks are declared as `namespace::name(params) { ... };` — the trailing `;`
is required. Player-scoped callbacks receive `playerid` as their first
argument. String literals interpolate expressions with `{...}`.

## Language at a glance

- **Statically typed** — `int`, `float`, `string`, `bool`, handle types, plus
  `array` and `map`.
- **Native-first API** — call `GetPlayerMoney(playerid)`,
  `SetPlayerHealth(playerid, 100.0)`, `CreateVehicle(...)` directly.
- **Typed bindings** — `let x = 1;`, optional annotation `let x: float = 1.0;`,
  reassignable and shared at module scope.
- **Operators** — `and/or/not` or `&&/||/!`; `~=` and `!=` mean "not equal";
  compound assignment (`+=`, `-=`, `*=`, `/=`, `%=`).
- **Literals** — hex ints (`0xFF`), durations (`500ms`, `2s`), arrays
  (`[1,2,3]`), maps (`{ name: "CJ" }`).
- **String interpolation** — `"score={GetPlayerScore(playerid)}"`, nested calls
  and strings allowed, escape braces with `\{` / `\}`.
- **Includes** — `#include <knight>` is optional; custom files with
  `#include <path.sa>` (cycles detected).
- **Commands** — `player::command("/give", int amount) { ... };`.
- **Config block** — `system::config() { server.name = "..."; ... };`.

## Built-in functions

A standard library ships with every gamemode — conversions (`int`, `float`,
`str`, `bool`, `typeof`), type predicates, math (`abs`, `min`, `max`, `clamp`,
`sqrt`, `pow`, `random`), strings (`upper`, `lower`, `trim`, `substr`, `split`,
`join`, `replace`, `contains`), collections (`array`, `map`, `push`, `pop`,
`at`, `keys`, `values`, `has`, `del`), and utilities (`format`, `distance`).
See [`docs/builtins.md`](docs/builtins.md).

## Callbacks

Callbacks are the entry points the engine invokes. The complete list is in
[`docs/callbacks.md`](docs/callbacks.md); the namespaces are:

| Namespace | Purpose |
|---|---|
| `system` | `start`, `stop`, `config` |
| `player` | connect/spawn/death/chat/command, vehicles, sync, aim, combat, class/spawn requests |
| `vehicle` | `create`, `spawn`, `death`, `damage_status_update` |
| `world` | checkpoints, objects, areas, actors, pickups, actor damage |
| `dialog` | `response` |
| `textdraw` | `create`, `click` |
| `timer` | `every` |

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
