# Knight — Event Reference

Every event handler is declared as `namespace::name(params) { ... };`.
`self` is implicit for handlers with a subject. Boolean-returning handlers
(`player::chat`, `player::request_class`, `player::request_spawn`) use the
return value as a veto (fail-open on runtime error).

## Summary

| Event | self | Returns | Description |
|---|---|---|---|
| `dialog::response` | `Player` | `—` | A player responded to a dialog; `accepted` is false on cancel, `listitem` is the selected row. |
| `player::aim` | `Player` | `—` | A player is aiming; exposes camera mode/zoom and weapon state. |
| `player::chat` | `Player` | `bool` | A player sent chat text; return true to relay it, false to swallow it. |
| `player::command` | `Player` | `bool` | A player ran a command declared as `player::command("/name", ...)`. |
| `player::connect` | `Player` | `—` | A player has connected; send a welcome, open a login dialog or set the camera. |
| `player::death` | `Player` | `—` | A player died; `killer` is null when there is no attacker. |
| `player::disconnect` | `Player` | `—` | A player has disconnected; clean up per-player state. |
| `player::enter_vehicle` | `Player` | `—` | A player entered a vehicle (as driver or passenger). |
| `player::exit_vehicle` | `Player` | `—` | A player exited a vehicle. |
| `player::key_state_change` | `Player` | `—` | A player's key state changed; compare newkeys/oldkeys for press/release. |
| `player::pickup` | `Player` | `—` | A player picked up a pickup. |
| `player::request_class` | `Player` | `bool` | A player requested a class; return false to veto the selection. |
| `player::request_class_done` | `Player` | `—` | The class response was sent to the client; apply the chosen skin/camera here. |
| `player::request_spawn` | `Player` | `bool` | A player requested to spawn; return false to veto the spawn. |
| `player::select_object` | `Player` | `—` | A player selected an object in the map editor. |
| `player::spawn` | `Player` | `—` | A player has spawned; reset health/armour and initialise gameplay state. |
| `player::state_change` | `Player` | `—` | A player's state changed (on foot, driving, dead, ...). |
| `player::stats` | `Player` | `—` | A player's money/drunk statistics changed. |
| `player::trailer_sync` | `Player` | `—` | A trailer synced to a vehicle. |
| `player::unoccupied_sync` | `Player` | `—` | An unoccupied vehicle synced; raw vehicle health sample. |
| `player::update` | `Player` | `—` | A player sync update arrived; raw position for anticheat and logic. |
| `player::weapon_shot` | `Player` | `—` | A player fired a weapon; reports the hit type, target and coordinates. |
| `system::start` | `—` | `—` | Fires once when the gamemode loads; set up globals, classes and world state here. |
| `system::stop` | `—` | `—` | Fires when the server shuts down; release resources and persist state here. |
| `textdraw::click` | `Player` | `—` | A player clicked a selectable text draw (65535 = cancel/empty area). |
| `textdraw::create` | `—` | `TextDraw` | Factory event to construct a text draw; return the created TextDraw. |
| `timer::every` | `Broadcast` | `—` | Periodic timer callback context; use with the timer natives. |
| `vehicle::create` | `—` | `Vehicle` | Factory event to construct a vehicle; return the created Vehicle. |
| `vehicle::damage_status_update` | `—` | `—` | A vehicle's panel/door/light/tyre damage changed. |
| `vehicle::death` | `—` | `—` | A vehicle was destroyed; `killer` is the responsible player id. |
| `vehicle::spawn` | `—` | `—` | A vehicle respawned. |
| `world::actor_damage` | `—` | `—` | An actor took damage; reports attacker, amount, weapon and body part. |
| `world::area_enter` | `Player` | `—` | A player entered a dynamic area. |
| `world::area_leave` | `Player` | `—` | A player left a dynamic area. |
| `world::checkpoint` | `Player` | `—` | A player entered their checkpoint. |
| `world::checkpoint_leave` | `Player` | `—` | A player left their checkpoint. |
| `world::object_create` | `—` | `Object` | Factory event to construct an object; return the created Object. |
| `world::race_checkpoint_enter` | `Player` | `—` | A player entered their race checkpoint. |
| `world::race_checkpoint_leave` | `Player` | `—` | A player left their race checkpoint. |

## Details

### `dialog::response`

A player responded to a dialog; `accepted` is false on cancel, `listitem` is the selected row.

```knight
dialog::response(int id, bool accepted, string input, int listitem) { ... };
```

| Parameter | Type |
|---|---|
| `id` | `int` |
| `accepted` | `bool` |
| `input` | `string` |
| `listitem` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::aim`

A player is aiming; exposes camera mode/zoom and weapon state.

```knight
player::aim(int camMode, int camZoom, int weaponState) { ... };
```

| Parameter | Type |
|---|---|
| `camMode` | `int` |
| `camZoom` | `int` |
| `weaponState` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::chat`

A player sent chat text; return true to relay it, false to swallow it.

```knight
player::chat(string message) { ... };
```

| Parameter | Type |
|---|---|
| `message` | `string` |

| self | Returns |
|---|---|
| `Player` | `bool` |

### `player::command`

A player ran a command declared as `player::command("/name", ...)`.

```knight
player::command() { ... };
```

| self | Returns |
|---|---|
| `Player` | `bool` |

### `player::connect`

A player has connected; send a welcome, open a login dialog or set the camera.

```knight
player::connect() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::death`

A player died; `killer` is null when there is no attacker.

```knight
player::death(Player killer) { ... };
```

| Parameter | Type |
|---|---|
| `killer` | `Player` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::disconnect`

A player has disconnected; clean up per-player state.

```knight
player::disconnect() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::enter_vehicle`

A player entered a vehicle (as driver or passenger).

```knight
player::enter_vehicle(Vehicle car) { ... };
```

| Parameter | Type |
|---|---|
| `car` | `Vehicle` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::exit_vehicle`

A player exited a vehicle.

```knight
player::exit_vehicle(Vehicle car) { ... };
```

| Parameter | Type |
|---|---|
| `car` | `Vehicle` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::key_state_change`

A player's key state changed; compare newkeys/oldkeys for press/release.

```knight
player::key_state_change(int newkeys, int oldkeys) { ... };
```

| Parameter | Type |
|---|---|
| `newkeys` | `int` |
| `oldkeys` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::pickup`

A player picked up a pickup.

```knight
player::pickup(int pickupid) { ... };
```

| Parameter | Type |
|---|---|
| `pickupid` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::request_class`

A player requested a class; return false to veto the selection.

```knight
player::request_class(int classid) { ... };
```

| Parameter | Type |
|---|---|
| `classid` | `int` |

| self | Returns |
|---|---|
| `Player` | `bool` |

### `player::request_class_done`

The class response was sent to the client; apply the chosen skin/camera here.

```knight
player::request_class_done(int classid, int skin) { ... };
```

| Parameter | Type |
|---|---|
| `classid` | `int` |
| `skin` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::request_spawn`

A player requested to spawn; return false to veto the spawn.

```knight
player::request_spawn() { ... };
```

| self | Returns |
|---|---|
| `Player` | `bool` |

### `player::select_object`

A player selected an object in the map editor.

```knight
player::select_object(int objecttype, int objectid, int modelid, float x, float y, float z) { ... };
```

| Parameter | Type |
|---|---|
| `objecttype` | `int` |
| `objectid` | `int` |
| `modelid` | `int` |
| `x` | `float` |
| `y` | `float` |
| `z` | `float` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::spawn`

A player has spawned; reset health/armour and initialise gameplay state.

```knight
player::spawn() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::state_change`

A player's state changed (on foot, driving, dead, ...).

```knight
player::state_change(int newstate, int oldstate) { ... };
```

| Parameter | Type |
|---|---|
| `newstate` | `int` |
| `oldstate` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::stats`

A player's money/drunk statistics changed.

```knight
player::stats(int money, int drunk) { ... };
```

| Parameter | Type |
|---|---|
| `money` | `int` |
| `drunk` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::trailer_sync`

A trailer synced to a vehicle.

```knight
player::trailer_sync(int vid) { ... };
```

| Parameter | Type |
|---|---|
| `vid` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::unoccupied_sync`

An unoccupied vehicle synced; raw vehicle health sample.

```knight
player::unoccupied_sync(int vid, float health) { ... };
```

| Parameter | Type |
|---|---|
| `vid` | `int` |
| `health` | `float` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::update`

A player sync update arrived; raw position for anticheat and logic.

```knight
player::update(float x, float y, float z) { ... };
```

| Parameter | Type |
|---|---|
| `x` | `float` |
| `y` | `float` |
| `z` | `float` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `player::weapon_shot`

A player fired a weapon; reports the hit type, target and coordinates.

```knight
player::weapon_shot(int weaponid, int hittype, int hitid, float hx, float hy, float hz) { ... };
```

| Parameter | Type |
|---|---|
| `weaponid` | `int` |
| `hittype` | `int` |
| `hitid` | `int` |
| `hx` | `float` |
| `hy` | `float` |
| `hz` | `float` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `system::start`

Fires once when the gamemode loads; set up globals, classes and world state here.

```knight
system::start() { ... };
```

| self | Returns |
|---|---|
| `—` | `—` |

### `system::stop`

Fires when the server shuts down; release resources and persist state here.

```knight
system::stop() { ... };
```

| self | Returns |
|---|---|
| `—` | `—` |

### `textdraw::click`

A player clicked a selectable text draw (65535 = cancel/empty area).

```knight
textdraw::click(TextDraw td) { ... };
```

| Parameter | Type |
|---|---|
| `td` | `TextDraw` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `textdraw::create`

Factory event to construct a text draw; return the created TextDraw.

```knight
textdraw::create(int x, int y, string text) { ... };
```

| Parameter | Type |
|---|---|
| `x` | `int` |
| `y` | `int` |
| `text` | `string` |

| self | Returns |
|---|---|
| `—` | `TextDraw` |

### `timer::every`

Periodic timer callback context; use with the timer natives.

```knight
timer::every() { ... };
```

| self | Returns |
|---|---|
| `Broadcast` | `—` |

### `vehicle::create`

Factory event to construct a vehicle; return the created Vehicle.

```knight
vehicle::create(int model, float x, float y, float z) { ... };
```

| Parameter | Type |
|---|---|
| `model` | `int` |
| `x` | `float` |
| `y` | `float` |
| `z` | `float` |

| self | Returns |
|---|---|
| `—` | `Vehicle` |

### `vehicle::damage_status_update`

A vehicle's panel/door/light/tyre damage changed.

```knight
vehicle::damage_status_update(int vid, int pid, int panels, int doors, int lights, int tyres) { ... };
```

| Parameter | Type |
|---|---|
| `vid` | `int` |
| `pid` | `int` |
| `panels` | `int` |
| `doors` | `int` |
| `lights` | `int` |
| `tyres` | `int` |

| self | Returns |
|---|---|
| `—` | `—` |

### `vehicle::death`

A vehicle was destroyed; `killer` is the responsible player id.

```knight
vehicle::death(int vid, int killer) { ... };
```

| Parameter | Type |
|---|---|
| `vid` | `int` |
| `killer` | `int` |

| self | Returns |
|---|---|
| `—` | `—` |

### `vehicle::spawn`

A vehicle respawned.

```knight
vehicle::spawn() { ... };
```

| self | Returns |
|---|---|
| `—` | `—` |

### `world::actor_damage`

An actor took damage; reports attacker, amount, weapon and body part.

```knight
world::actor_damage(int actorid, int playerid, float amount, int weaponid, int bodypart) { ... };
```

| Parameter | Type |
|---|---|
| `actorid` | `int` |
| `playerid` | `int` |
| `amount` | `float` |
| `weaponid` | `int` |
| `bodypart` | `int` |

| self | Returns |
|---|---|
| `—` | `—` |

### `world::area_enter`

A player entered a dynamic area.

```knight
world::area_enter(int area) { ... };
```

| Parameter | Type |
|---|---|
| `area` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `world::area_leave`

A player left a dynamic area.

```knight
world::area_leave(int area) { ... };
```

| Parameter | Type |
|---|---|
| `area` | `int` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `world::checkpoint`

A player entered their checkpoint.

```knight
world::checkpoint(float x, float y, float z) { ... };
```

| Parameter | Type |
|---|---|
| `x` | `float` |
| `y` | `float` |
| `z` | `float` |

| self | Returns |
|---|---|
| `Player` | `—` |

### `world::checkpoint_leave`

A player left their checkpoint.

```knight
world::checkpoint_leave() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

### `world::object_create`

Factory event to construct an object; return the created Object.

```knight
world::object_create(int model, float x, float y, float z) { ... };
```

| Parameter | Type |
|---|---|
| `model` | `int` |
| `x` | `float` |
| `y` | `float` |
| `z` | `float` |

| self | Returns |
|---|---|
| `—` | `Object` |

### `world::race_checkpoint_enter`

A player entered their race checkpoint.

```knight
world::race_checkpoint_enter() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

### `world::race_checkpoint_leave`

A player left their race checkpoint.

```knight
world::race_checkpoint_leave() { ... };
```

| self | Returns |
|---|---|
| `Player` | `—` |

