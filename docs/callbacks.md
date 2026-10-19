# Knight — Callback Reference

Callbacks receive `playerid` (int) as their first argument. Use global natives.

## Summary

| Callback | `playerid` | Returns | Description |
|---|---|---|---|
| `dialog::response` | yes | `—` | A player responded to a dialog; `accepted` is false on cancel, `listitem` is the selected row. |
| `player::aim` | yes | `—` | A player is aiming; exposes camera mode/zoom and weapon state. |
| `player::chat` | yes | `bool` | A player sent chat text; return true to relay it, false to swallow it. |
| `player::command` | yes | `bool` | A player ran a command declared as `player::command("/name", ...)`. |
| `player::connect` | yes | `—` | A player has connected; send a welcome, open a login dialog or set the camera. |
| `player::death` | yes | `—` | A player died; `killer` is null when there is no attacker. |
| `player::disconnect` | yes | `—` | A player has disconnected; clean up per-player state. |
| `player::enter_vehicle` | yes | `—` | A player entered a vehicle (as driver or passenger). |
| `player::exit_vehicle` | yes | `—` | A player exited a vehicle. |
| `player::finished_downloading` | yes | `—` | A 0.3.DL client finished downloading custom models for a virtual world. |
| `player::key_state_change` | yes | `—` | A player's key state changed; compare newkeys/oldkeys for press/release. |
| `player::pickup` | yes | `—` | A player picked up a pickup. |
| `player::request_class` | yes | `bool` | A player requested a class; return false to veto the selection. |
| `player::request_class_done` | yes | `—` | The class response was sent to the client; apply the chosen skin/camera here. |
| `player::request_download` | yes | `bool` | A 0.3.DL client requested a custom model/texture; return false to deny, or call RedirectDownload. |
| `player::request_spawn` | yes | `bool` | A player requested to spawn; return false to veto the spawn. |
| `player::select_object` | yes | `—` | A player selected an object in the map editor. |
| `player::spawn` | yes | `—` | A player has spawned; reset health/armour and initialise gameplay state. |
| `player::state_change` | yes | `—` | A player's state changed (on foot, driving, dead, ...). |
| `player::stats` | yes | `—` | A player's money/drunk statistics changed. |
| `player::trailer_sync` | yes | `—` | A trailer synced to a vehicle. |
| `player::unoccupied_sync` | yes | `—` | An unoccupied vehicle synced; raw vehicle health sample. |
| `player::update` | yes | `—` | A player sync update arrived; raw position for anticheat and logic. |
| `player::weapon_shot` | yes | `—` | A player fired a weapon; reports the hit type, target and coordinates. |
| `system::start` | — | `—` | Fires once when the gamemode loads; set up globals, classes and world state here. |
| `system::stop` | — | `—` | Fires when the server shuts down; release resources and persist state here. |
| `textdraw::click` | yes | `—` | A player clicked a selectable text draw (65535 = cancel/empty area). |
| `textdraw::create` | — | `TextDraw` | Factory event to construct a text draw; return the created TextDraw. |
| `timer::every` | — | `—` | Periodic timer callback context; use with the timer natives. |
| `vehicle::create` | — | `Vehicle` | Factory event to construct a vehicle; return the created Vehicle. |
| `vehicle::damage_status_update` | — | `—` | A vehicle's panel/door/light/tyre damage changed. |
| `vehicle::death` | — | `—` | A vehicle was destroyed; `killer` is the responsible player id. |
| `vehicle::spawn` | — | `—` | A vehicle respawned. |
| `world::actor_damage` | — | `—` | An actor took damage; reports attacker, amount, weapon and body part. |
| `world::area_enter` | yes | `—` | A player entered a dynamic area. |
| `world::area_leave` | yes | `—` | A player left a dynamic area. |
| `world::checkpoint` | yes | `—` | A player entered their checkpoint. |
| `world::checkpoint_leave` | yes | `—` | A player left their checkpoint. |
| `world::object_create` | — | `Object` | Factory event to construct an object; return the created Object. |
| `world::race_checkpoint_enter` | yes | `—` | A player entered their race checkpoint. |
| `world::race_checkpoint_leave` | yes | `—` | A player left their race checkpoint. |

## Details

### `dialog::response`

A player responded to a dialog; `accepted` is false on cancel, `listitem` is the selected row.

```knight
dialog::response(int playerid, int id, bool accepted, string input, int listitem) { ... };
```

Returns: `—`

### `player::aim`

A player is aiming; exposes camera mode/zoom and weapon state.

```knight
player::aim(int playerid, int camMode, int camZoom, int weaponState) { ... };
```

Returns: `—`

### `player::chat`

A player sent chat text; return true to relay it, false to swallow it.

```knight
player::chat(int playerid, string message) { ... };
```

Returns: `bool`

### `player::command`

A player ran a command declared as `player::command("/name", ...)`.

```knight
player::command(int playerid) { ... };
```

Returns: `bool`

### `player::connect`

A player has connected; send a welcome, open a login dialog or set the camera.

```knight
player::connect(int playerid) { ... };
```

Returns: `—`

### `player::death`

A player died; `killer` is null when there is no attacker.

```knight
player::death(int playerid, Player killer) { ... };
```

Returns: `—`

### `player::disconnect`

A player has disconnected; clean up per-player state.

```knight
player::disconnect(int playerid) { ... };
```

Returns: `—`

### `player::enter_vehicle`

A player entered a vehicle (as driver or passenger).

```knight
player::enter_vehicle(int playerid, Vehicle car) { ... };
```

Returns: `—`

### `player::exit_vehicle`

A player exited a vehicle.

```knight
player::exit_vehicle(int playerid, Vehicle car) { ... };
```

Returns: `—`

### `player::finished_downloading`

A 0.3.DL client finished downloading custom models for a virtual world.

```knight
player::finished_downloading(int playerid, int virtualworld) { ... };
```

Returns: `—`

### `player::key_state_change`

A player's key state changed; compare newkeys/oldkeys for press/release.

```knight
player::key_state_change(int playerid, int newkeys, int oldkeys) { ... };
```

Returns: `—`

### `player::pickup`

A player picked up a pickup.

```knight
player::pickup(int playerid, int pickupid) { ... };
```

Returns: `—`

### `player::request_class`

A player requested a class; return false to veto the selection.

```knight
player::request_class(int playerid, int classid) { ... };
```

Returns: `bool`

### `player::request_class_done`

The class response was sent to the client; apply the chosen skin/camera here.

```knight
player::request_class_done(int playerid, int classid, int skin) { ... };
```

Returns: `—`

### `player::request_download`

A 0.3.DL client requested a custom model/texture; return false to deny, or call RedirectDownload.

```knight
player::request_download(int playerid, int type, int crc) { ... };
```

Returns: `bool`

### `player::request_spawn`

A player requested to spawn; return false to veto the spawn.

```knight
player::request_spawn(int playerid) { ... };
```

Returns: `bool`

### `player::select_object`

A player selected an object in the map editor.

```knight
player::select_object(int playerid, int objecttype, int objectid, int modelid, float x, float y, float z) { ... };
```

Returns: `—`

### `player::spawn`

A player has spawned; reset health/armour and initialise gameplay state.

```knight
player::spawn(int playerid) { ... };
```

Returns: `—`

### `player::state_change`

A player's state changed (on foot, driving, dead, ...).

```knight
player::state_change(int playerid, int newstate, int oldstate) { ... };
```

Returns: `—`

### `player::stats`

A player's money/drunk statistics changed.

```knight
player::stats(int playerid, int money, int drunk) { ... };
```

Returns: `—`

### `player::trailer_sync`

A trailer synced to a vehicle.

```knight
player::trailer_sync(int playerid, int vid) { ... };
```

Returns: `—`

### `player::unoccupied_sync`

An unoccupied vehicle synced; raw vehicle health sample.

```knight
player::unoccupied_sync(int playerid, int vid, float health) { ... };
```

Returns: `—`

### `player::update`

A player sync update arrived; raw position for anticheat and logic.

```knight
player::update(int playerid, float x, float y, float z) { ... };
```

Returns: `—`

### `player::weapon_shot`

A player fired a weapon; reports the hit type, target and coordinates.

```knight
player::weapon_shot(int playerid, int weaponid, int hittype, int hitid, float hx, float hy, float hz) { ... };
```

Returns: `—`

### `system::start`

Fires once when the gamemode loads; set up globals, classes and world state here.

```knight
system::start() { ... };
```

Returns: `—`

### `system::stop`

Fires when the server shuts down; release resources and persist state here.

```knight
system::stop() { ... };
```

Returns: `—`

### `textdraw::click`

A player clicked a selectable text draw (65535 = cancel/empty area).

```knight
textdraw::click(int playerid, TextDraw td) { ... };
```

Returns: `—`

### `textdraw::create`

Factory event to construct a text draw; return the created TextDraw.

```knight
textdraw::create(int x, int y, string text) { ... };
```

Returns: `TextDraw`

### `timer::every`

Periodic timer callback context; use with the timer natives.

```knight
timer::every() { ... };
```

Returns: `—`

### `vehicle::create`

Factory event to construct a vehicle; return the created Vehicle.

```knight
vehicle::create(int model, float x, float y, float z) { ... };
```

Returns: `Vehicle`

### `vehicle::damage_status_update`

A vehicle's panel/door/light/tyre damage changed.

```knight
vehicle::damage_status_update(int vid, int pid, int panels, int doors, int lights, int tyres) { ... };
```

Returns: `—`

### `vehicle::death`

A vehicle was destroyed; `killer` is the responsible player id.

```knight
vehicle::death(int vid, int killer) { ... };
```

Returns: `—`

### `vehicle::spawn`

A vehicle respawned.

```knight
vehicle::spawn() { ... };
```

Returns: `—`

### `world::actor_damage`

An actor took damage; reports attacker, amount, weapon and body part.

```knight
world::actor_damage(int actorid, int playerid, float amount, int weaponid, int bodypart) { ... };
```

Returns: `—`

### `world::area_enter`

A player entered a dynamic area.

```knight
world::area_enter(int playerid, int area) { ... };
```

Returns: `—`

### `world::area_leave`

A player left a dynamic area.

```knight
world::area_leave(int playerid, int area) { ... };
```

Returns: `—`

### `world::checkpoint`

A player entered their checkpoint.

```knight
world::checkpoint(int playerid, float x, float y, float z) { ... };
```

Returns: `—`

### `world::checkpoint_leave`

A player left their checkpoint.

```knight
world::checkpoint_leave(int playerid) { ... };
```

Returns: `—`

### `world::object_create`

Factory event to construct an object; return the created Object.

```knight
world::object_create(int model, float x, float y, float z) { ... };
```

Returns: `Object`

### `world::race_checkpoint_enter`

A player entered their race checkpoint.

```knight
world::race_checkpoint_enter(int playerid) { ... };
```

Returns: `—`

### `world::race_checkpoint_leave`

A player left their race checkpoint.

```knight
world::race_checkpoint_leave(int playerid) { ... };
```

Returns: `—`

