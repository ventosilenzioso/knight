# Knight — Configuration Reference

`server.cfg` is **optional**. Everything can be declared in the gamemode's
`system::config()` block, which is the recommended setup for a single-gamemode
server.

```knight
system::config() {
    server.name = "My Server";
    server.port = 7777;
    server.max_players = 100;
    server.language = "English";
    server.weather = 10;
    server.world_time = 12;
    server.gravity = 0.008;
    server.stream_distance = 300.0;
    server.connect_timeout = 20;
    server.announce = true;
    server.map_name = "San Andreas";
    server.plugins = ["plugins", "modules/anticheat.sa"];
};
```

Start without a config file:

```bash
./Bin/knight-server -cfg "" -gamemode Gamemodes/minimal.sa
```

With `-cfg ""` nothing is read from disk; the server starts from built-in
defaults and the gamemode defines everything, including the port. Without the
flag a `server.cfg` is read when present.

## Precedence

| Source | Wins? |
|---|---|
| `system::config()` in the gamemode | Always, for fields it declares |
| `server.cfg` | For fields the gamemode does not declare |
| Built-in defaults | When neither declares a field |

Only declared fields are overridden: a gamemode that sets just `server.name`
keeps every other value from `server.cfg` or the defaults.

## Fields

| Field | Type | server.cfg key | Default |
|---|---|---|---|
| `server.name` | `string` | `hostname` | `Knight Server` |
| `server.hostname` | `string` | `hostname` | alias of `name` |
| `server.port` | `int` | `port` | `7777` |
| `server.max_players` | `int` | `maxplayers` | `50` |
| `server.gamemode` | `string` | `gamemode0` | `bare 1` |
| `server.language` | `string` | `language` | `English` |
| `server.password` | `string` | `password` | empty |
| `server.rcon_password` | `string` | `rcon_password` | empty |
| `server.weather` | `int` | `weather` | `10` |
| `server.world_time` | `int` | `worldtime` | `12` |
| `server.gravity` | `float` | `gravity` | `0.008` |
| `server.stream_distance` | `float` | `stream_distance` | `200` |
| `server.connect_timeout` | `int` (seconds) | `connect_timeout` | `20` |
| `server.announce` | `bool` | `announce` | `true` |
| `server.map_name` | `string` | `mapname` | empty |
| `server.web_url` | `string` | `weburl` | empty |
| `server.bind` | `string` | `bind` | empty |
| `server.plugins` | `array` / `string` | `plugins` | empty |

Out-of-range values are ignored and reported in the log: `max_players` 1..1000,
`port` 1..65535, `connect_timeout` 1..300 seconds.

## Reading values at runtime

The same names work outside `system::config()`:

```knight
player::command("/info") {
    SendClientMessage(playerid, "{server.name} | max {server.max_players} | port {server.port}");
};
```

Also available as natives: `GetMaxPlayers()`, `GetGravity()`,
`PlayerCount()`.

## Connection timeout

`connect_timeout` is how long a peer may stay silent before the engine drops it.
Mobile networks stall for several seconds while switching towers, so the default
is 20 seconds. Raise it if players on mobile data disconnect while moving.

```cfg
connect_timeout 20    # seconds; range 1..300
```

## Plugins

```knight
server.plugins = ["plugins", "mods/anticheat.sa"];
```

A path is a folder or a single `.sa` file. A folder loads every `.sa` inside it
plus every immediate subfolder containing `plugin.go`. See
[`plugins.md`](plugins.md).

## Custom models (SA-MP 0.3.DL)

```cfg
useartwork 1
# artpath models                 # optional: only for bare file names
# artwork_cdn https://cdn/models
# artwork_port 7777
custom_invisible_vehicle_model 570
```

`useartwork` is an opt-out switch: custom models are enabled by default.
