# Knight

**Knight** is a from-scratch **SA-MP 0.3.7 / 0.3.DL server** written in Go, with
its own statically-typed scripting language. Gamemodes are `.sa` files: you
declare callbacks, configure the server, and call native functions directly by
name. No Pawn, no Lua VM, no `#include` bookkeeping.

This repository is the **public distribution**: prebuilt server binaries, the
language reference, runnable examples and the standalone `knight` validator.
The engine source is maintained separately.

```
Bin/            knight-server binaries (linux / windows)
Gamemodes/      ready-to-run .sa gamemodes (with a modules/ example)
server.cfg      default server configuration (optional — see below)
tools/          prebuilt knight validator (linux / macos / windows)
docs/           language, callbacks, natives, built-ins, configuration
examples/       runnable .sa gamemodes
```

---

## Quick start

```bash
./Bin/knight-server -cfg server.cfg
# Windows: Bin\knight-server.exe -cfg server.cfg
```

The default config loads `Gamemodes/bare.sa`. To run a specific gamemode:

```bash
./Bin/knight-server -cfg "" -gamemode Gamemodes/minimal.sa
```

### server.cfg is optional

Every setting can live in `system::config()` inside the gamemode, including the
port. Values declared in code win; `server.cfg`, when present, only fills the
fields the gamemode leaves out.

```knight
system::config() {
    server.name = "Euporia RP";
    server.port = 7777;
    server.max_players = 200;
    server.language = "Indonesian";
    server.weather = 10;
    server.world_time = 12;
    server.gravity = 0.008;
    server.connect_timeout = 20;
};
```

---

## What's in this release

### Language

| Feature | Details |
|---|---|
| Types | `int`, `float`, `string`, `bool`, handle types, `array`, `map` |
| Variables | `let`, optional annotation (`let x: float = 1.0`), reassignable |
| Constants | `const NAME = value;` — reassignment is a compile error |
| Functions | `function name(params) { ... }` with typed parameters, **default values** (`int n = 10`) and **rest parameters** (`...rest`) |
| Control flow | `if/else if/else`, `while`, `do..while`, C-style `for`, `for..in` (arrays and maps), `switch/case/default`, `break`, `continue`, `return` |
| Expressions | ternary `? :`, bitwise `& \| ^ ~ << >>`, array/string slices (`arr[1:4]`), comma assignment (`a, b = v`) |
| Literals | hex ints, durations (`500ms`, `2s`), arrays, maps |
| Strings | interpolation with `{expr}`, nested calls and strings, `\{` / `\}` escapes |
| Config | `system::config()` block, usable as the only configuration source |

### Modules and plugins

```knight
// Gamemodes/modules/economy.sa
module "economy" { version: "1.0.0"; };
export function economyBalance(int id) { return at(balances, id); };
on player::chat(string message) { return true; };
```

```knight
// Gamemodes/main.sa
import "economy";
system::config() { server.plugins = ["plugins", "mods/anticheat.sa"]; };
```

- `module`, `import`, `export` split a gamemode across files; modules are
  type-checked as one program and loaded once (cycles are rejected).
- `on ns::name(...)` is the declarative hook form; returning `false` vetoes the
  event for every later handler.
- **Plugins from a path**: `server.plugins` takes folders or `.sa` files. A
  folder loads every `.sa` in it plus every immediate subfolder containing
  `plugin.go`; script plugins need no rebuild.
- A JSON plugin ships with this distribution (`plugins/json`): 14 natives
  (`JsonParse`, `JsonGetInt`, `JsonSaveFile`, …).

See [`docs/plugins.md`](docs/plugins.md).

### Engine

- **RakNet / SA-MP 0.3.7 protocol** from scratch, plus 0.3.DL custom models and
  crafted custom vehicles.
- **559 natives** and **41 callbacks**, all documented with signatures.
- **Configurable connection timeout** (`connect_timeout`, default 20 s) so
  mobile clients survive network stalls.
- Chat policy, anticheat hooks and commands are owned by the gamemode; the core
  only relays state.
- A runtime error on one line of a callback is logged and skipped — the rest of
  the callback still runs and the player keeps being processed.

---

## Documentation

| Document | Contents |
|---|---|
| [`docs/language.md`](docs/language.md) | Syntax: declarations, types, operators, loops, switch, strings, commands |
| [`docs/natives.md`](docs/natives.md) | All native functions with signatures and descriptions |
| [`docs/callbacks.md`](docs/callbacks.md) | Every callback: when it fires, parameters and return |
| [`docs/builtins.md`](docs/builtins.md) | Standard library: conversions, math, strings, arrays, maps |
| [`docs/configuration.md`](docs/configuration.md) | `system::config()` fields, `server.cfg` keys and precedence |
| [`docs/plugins.md`](docs/plugins.md) | Modules, script plugins, Go plugins, the JSON plugin |

---

## Hello, Knight

Natives are global functions — no namespace, no `self`:

```knight
player::connect(int playerid) {
    SendClientMessage(playerid, "Welcome to {server.name}, {PlayerName(playerid)}!");
};

player::spawn(int playerid) {
    SetPlayerHealth(playerid, 100.0);
    SetPlayerArmour(playerid, 50.0);
};

player::command("/heal") {
    SetPlayerHealth(playerid, 100.0);
    SendClientMessage(playerid, "Healed.");
};
```

Callbacks are declared as `namespace::name(params) { ... };` — the trailing `;`
is required.

---

## Language at a glance

```knight
// loops
for (let i = 0; i < 5; i += 1) { ... }
for (let name in names) { ... }
for (let index, name in names) { ... }
while (condition) { ... }
do { ... } while (condition);

// switch (no fall-through)
switch (classid) {
    case 0: SendClientMessage(playerid, "Medic");
    case 1: SendClientMessage(playerid, "Police");
    default: SendClientMessage(playerid, "Civilian");
}

// functions with defaults and rest parameters
function greet(string name, string suffix = "!", int times = 1) { ... }
function total(int first, ...rest) { ... }

// constants and slices
const MAX_HP = 100;
let head = "Knight"[0:3];      // "Kni"
let part = nums[1:4];          // array slice
let label = hp > 50 ? "ok" : "low";
```

---

## Built-in functions

60 built-ins ship with the language: conversions (`int`, `float`, `str`,
`bool`, `typeof`), type predicates, math (`abs`, `min`, `max`, `clamp`, `sqrt`,
`pow`, `random`, `sign`), strings (`upper`, `lower`, `trim`, `substr`, `split`,
`join`, `replace`, `contains`, `repeat`, `pad_left`, `count`, …), collections
(`array`, `map`, `push`, `pop`, `at`, `keys`, `values`, `has`, `del`, `insert`,
`slice`, `index_of`, `reverse`, `sort`, `concat`, `unique`) and utilities
(`format`, `distance`). `push`, `pop`, `shift` and `del` mutate the container in
place. See [`docs/builtins.md`](docs/builtins.md).

---

## Callbacks

The complete list is in [`docs/callbacks.md`](docs/callbacks.md).

| Namespace | Purpose |
|---|---|
| `system` | `start`, `stop`, `config` |
| `player` | connect/spawn/death/chat/command, vehicles, sync, aim, combat, class/spawn requests, downloads |
| `vehicle` | `create`, `spawn`, `death`, `damage_status_update` |
| `world` | checkpoints, objects, areas, actors, pickups, actor damage |
| `dialog` | `response` |
| `textdraw` | `create`, `click` |
| `timer` | `every` |

---

## Examples

| File | What it shows |
|---|---|
| `examples/minimal.sa` | Smallest loadable, config-free gamemode |
| `examples/full.sa` | Config block, classes, chat, commands, death handling |
| `examples/bare.sa` | Realistic gamemode: SQLite auth, dialogs, anticheat, admin commands |
| `examples/builtins.sa` | Standard library: strings, math, arrays and maps |
| `Gamemodes/plugins.sa` | Modules + bundled JSON plugin (`server.plugins`) |
| `Gamemodes/modules/*.sa` | Module + hook example (`economy`, `anticheat`) |

```bash
./Bin/knight-server -cfg "" -gamemode Gamemodes/minimal.sa
```

---

## The validator

`knight` checks a `.sa` file without running a server. It resolves includes and
imports, lexes, parses, and type-checks — including plugin natives.

```bash
./tools/knight-linux-amd64 -check examples/full.sa
./tools/knight-linux-amd64 -ast examples/minimal.sa   # dump the parsed AST
```

Every shipped `examples/*.sa` and `Gamemodes/*.sa` passes `-check`.

---

## Custom models (SA-MP 0.3.DL)

0.3.DL clients can download custom skins (20001–30000) and objects
(−30000..−1000). Register them with `AddCharModel` / `AddSimpleModel`. Model
paths behave like C++ includes: any path with `/` is used verbatim; a bare file
name is looked up under the optional `artpath`. `useartwork 1` is the default.
0.3.7 clients never receive model data and fall back to the base model.

## Custom vehicles (crafted on 0.3.DL)

0.3.DL has no custom vehicle model, so Knight builds one from a drivable base
vehicle plus an attached custom object:

```knight
system::start() {
    AddSimpleModel(-1, 19379, -2000, "veh.dff", "veh.txd");
    let vid = CreateCustomVehicle(411, -2000, 1958.4, 1348.0, 15.4, 90.0, 3, 3, true);
};
```

`true` hides the chassis for 0.3.DL clients; 0.3.7 clients see the base vehicle
and a safe object fallback. See `examples/custom_vehicles.sa`.

---

## Verifying

```bash
for f in examples/*.sa Gamemodes/*.sa; do ./tools/knight-linux-amd64 -check "$f" || exit 1; done
```

---

## License

The examples and documentation in this repository are provided for use with
Knight. The `knight` binaries are distributed as prebuilt tools.
