# Knight — Modules and Plugins

Knight has two extension kinds that share one registry. Most server owners only
ever use the first.

## Script modules (`.sa`)

No Go, no rebuild. A module is a normal `.sa` file with a `module` header that a
gamemode imports.

```knight
// Gamemodes/modules/mute.sa
module "mute" { version: "1.0.0"; };

let muted = {};

export function mutePlayer(int id) { muted[id] = true; }
export function unmutePlayer(int id) { del(muted, id); }

on player::chat(string message) {
    if (has(muted, playerid)) {
        SendClientMessage(playerid, "Kamu dibisukan.");
        return false;          // veto: no relay
    }
    return true;
};
```

```knight
// Gamemodes/main.sa
import "mute";

player::command("/mute") {
    mutePlayer(playerid);
    SendClientMessage(playerid, "Dibisukan.");
};
```

Module search order:

1. `Gamemodes/<name>.sa`
2. `Gamemodes/modules/<name>.sa`
3. `modules/<name>.sa` (one level above the gamemode)
4. `modules/<name>.sa` in the working directory

Modules load once, are type-checked together with the gamemode, and a boolean
handler returning `false` vetoes the event for every later handler.

## Loading plugins from a path

A gamemode can declare plugins directly, without blank imports:

```knight
system::config() {
    server.plugins = ["plugins", "mods/anticheat.sa"];
};
```

A path is either a folder or a single `.sa` file:

- a folder loads every `*.sa` inside it and every immediate subfolder that
  contains `plugin.go` (a Go plugin package)
- a `.sa` file loads as a script plugin
- a missing path is a startup error

Go plugins must still be compiled into the binary (`import _ "knight/plugins/x"`
in `cmd/knight-server/plugins_enabled.go`); naming their folder is what
activates them. Script plugins need no rebuild.

## Go plugins

For features that need sockets, files or drivers. A plugin is compiled into the
server:

```go
package discord

import "knight/pkg/plugin"

type discord struct{ api plugin.API }

func init() { plugin.Register(func() plugin.Plugin { return &discord{} }) }

func (d *discord) Info() plugin.Info { return plugin.Info{Name: "discord", Version: "1.0.0"} }

func (d *discord) Init(api plugin.API) error {
    d.api = api
    api.RegisterNative("DiscordSend", d.send)                    // .sa: DiscordSend(...)
    api.Hook("player::connect", plugin.PriorityEarly, d.onConnect)
    return nil
}

func (d *discord) send(ctx plugin.Ctx, args []plugin.Value) plugin.Value {
    return plugin.IntV(1)
}

func (d *discord) onConnect(ctx plugin.Ctx) bool {
    ctx.Log("player %d connected", ctx.Int(0))
    return true
}

func (d *discord) Shutdown() {}
```

Activate it with a blank import in the server entry point:

```go
import _ "knight/plugins/discord"
```

Plugin natives are visible to the type checker, so gamemodes call them like any
other native. Plugin hooks run before script handlers, in priority order
(`PriorityEarly` < `PriorityNormal` < `PriorityLate`).

Reference implementation: `examples/plugins/welcome`.

## Bundled JSON plugin

`plugins/json` ships with the distribution and is compiled into
`Bin/knight-server`. Activate it from a gamemode:

```knight
system::config() { server.plugins = ["plugins/json"]; };
```

| Native | Returns |
|---|---|
| `JsonParse(string text)` | document id, or `""` on error |
| `JsonParseFile(string path)` | document id, or `""` |
| `JsonStringify(id, int indent)` | string |
| `JsonFree(id)` | bool |
| `JsonGetString(id, path)` | string |
| `JsonGetInt(id, path)` | int |
| `JsonGetFloat(id, path)` | float |
| `JsonGetBool(id, path)` | bool |
| `JsonHas(id, path)` | bool |
| `JsonType(id, path)` | `object` / `array` / `string` / `number` / `bool` / `null` / `missing` |
| `JsonCount(id, path)` | int |
| `JsonKeys(id, path)` | comma-separated keys, sorted |
| `JsonEscape(string text)` | quoted, escaped string |
| `JsonSaveFile(id, path, indent)` | bool |

Paths walk nested values with dots: `"bag.items"`, `"tags.1"`, `""` (whole
document). File natives are confined to `scriptfiles` (or `KNIGHT_JSON_ROOT`)
and reject absolute paths and `..` traversal.

> Escape `{` and `}` as `\\{` and `\\}` inside JSON string literals, or load the
> document from a file with `JsonParseFile`.

Documents stay in memory until `JsonFree(id)` or shutdown — always free what you
no longer need.
