# Knight — Configuration Reference

`system::config()` writes `server.cfg` keys when the gamemode loads.
Only assignments are allowed inside the block.

```knight
system::config() {
    server.name = "My Server";
    server.max_players = 100;
    server.port = 7777;
};
```

| Field | Type | server.cfg key |
|---|---|---|
| `server.announce` | `bool` | `announce` |
| `server.bind` | `string` | `bind` |
| `server.gamemode` | `string` | `gamemode0` |
| `server.gravity` | `float` | `gravity` |
| `server.hostname` | `string` | `hostname` |
| `server.language` | `string` | `language` |
| `server.map_name` | `string` | `mapname` |
| `server.max_players` | `int` | `maxplayers` |
| `server.name` | `string` | `hostname` |
| `server.password` | `string` | `password` |
| `server.port` | `int` | `port` |
| `server.rcon_password` | `string` | `rcon_password` |
| `server.stream_distance` | `float` | `stream_distance` |
| `server.weather` | `int` | `weather` |
| `server.web_url` | `string` | `weburl` |
| `server.world_time` | `int` | `worldtime` |
