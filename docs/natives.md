# Knight — Native API Reference

Inside any handler call engine natives as `sa.<Native>(...)`.
The typing surface below is what the validator checks; `sa.*` accepts
the full engine native set.

## `Broadcast`

### Methods

- `log(string)`
- `message(string)`

## `Object`

### Fields

| Field | Type | Access |
|---|---|---|
| `id` | `int` | read |
| `model` | `int` | read |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

- `destroy()`
- `move(float, float, float, float, float, float, float)`
- `set_material(int, int, string, string, int)`
- `set_position(float, float, float)`
- `set_rotation(float, float, float)`
- `stop()`

Factory: `CreateObject(int, float, float, float, float, float, float, float) -> Object`

## `Player`

### Fields

| Field | Type | Access |
|---|---|---|
| `armor` | `float` | read/write |
| `armour` | `float` | read/write |
| `color` | `int` | read/write |
| `colour` | `int` | read/write |
| `connected` | `bool` | read |
| `facing_angle` | `float` | read/write |
| `health` | `float` | read/write |
| `id` | `int` | read |
| `interior` | `int` | read/write |
| `ip` | `string` | read |
| `money` | `int` | read/write |
| `name` | `string` | read/write |
| `ping` | `int` | read |
| `score` | `int` | read/write |
| `skin` | `int` | read/write |
| `team` | `int` | read/write |
| `vehicle` | `int` | read |
| `virtual_world` | `int` | read/write |
| `weapon` | `int` | read/write |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

- `apply_animation(string, string, float, bool, bool, bool, bool, int)`
- `apply_animation2(string, string, float, bool, bool, bool, bool, int)`
- `ban()`
- `ban_with_reason(string)`
- `clear_animations()`
- `disable_checkpoint()`
- `distance_to(Player) -> float`
- `force_class_selection()`
- `get_position() -> array`
- `give_weapon(int, int)`
- `hide_textdraw(TextDraw)`
- `is_admin() -> bool`
- `kick()`
- `kick_with_reason(string)`
- `message(string, int)`
- `reset_money()`
- `reset_weapons()`
- `send_message(string)`
- `send_score(int)`
- `set_admin(bool)`
- `set_armor(float)`
- `set_armour(float)`
- `set_camera_behind()`
- `set_camera_look_at(float, float, float, int)`
- `set_camera_pos(float, float, float)`
- `set_checkpoint(float, float, float, float)`
- `set_color(int)`
- `set_health(float)`
- `set_interior(int)`
- `set_map_icon(int, float, float, float, int, int, int)`
- `set_money(int)`
- `set_position(float, float, float)`
- `set_skin(int)`
- `set_special_action(int)`
- `set_team(int)`
- `set_virtual_world(int)`
- `show_dialog(int, int, string, string, string, string)`
- `show_textdraw(TextDraw)`

## `TextDraw`

### Fields

| Field | Type | Access |
|---|---|---|
| `id` | `int` | read |

### Methods

- `destroy()`
- `set_string(string)`
- `show()`

Factory: `TextDrawCreate(int, int, string) -> TextDraw`

## `Vehicle`

### Fields

| Field | Type | Access |
|---|---|---|
| `angle` | `float` | read/write |
| `health` | `float` | read/write |
| `id` | `int` | read |
| `model` | `int` | read |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

- `destroy()`
- `repair()`
- `set_color(int, int)`
- `set_health(float)`
- `set_number_plate(string)`
- `set_position(float, float, float)`

Factory: `CreateVehicle(int, float, float, float, float, int, int) -> Vehicle`

## `server`

### Runtime methods

- `server.disable_interior_enter_exits()`
- `server.game_mode_exit()`
- `server.get_gravity() -> float`
- `server.get_max_players() -> int`
- `server.get_player_count() -> int`
- `server.log(string)`
- `server.send_rcon(string)`
- `server.set_gamemode_text(string)`
- `server.set_gravity(float)`
- `server.set_team_count(int)`
- `server.set_weather(int)`
- `server.set_world_time(int)`
- `server.show_name_tags(bool)`
- `server.show_player_markers(int)`

### `system::config()` keys

| Key | Type | server.cfg |
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

### Namespace helpers

- `player.add_class(int, float, float, float, float, int, int, int, int, int, int)` -> `sa.AddPlayerClass`
- `player.add_class_ex(int, int, float, float, float, float, int, int, int, int, int, int)` -> `sa.AddPlayerClassEx`
- `server.set_gamemode_text(string)` -> `sa.SetGameModeText`
- `server.set_weather(int)` -> `sa.SetWeather`
- `server.set_world_time(int)` -> `sa.SetWorldTime`

---

498 engine natives are recognised by the validator.
