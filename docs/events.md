# Knight — Event Reference

Every event handler is declared as `namespace::name(params) { ... };`.
`self` is implicit for handlers with a subject. Boolean-returning handlers
(`player::chat`, `player::request_class`, `player::request_spawn`) use the
return value as a veto (fail-open on runtime error).

| Event | self | Returns | Parameters |
|---|---|---|---|
| `dialog::response` | `Player` | `—` | `int id, bool accepted, string input, int listitem` |
| `player::aim` | `Player` | `—` | `int camMode, int camZoom, int weaponState` |
| `player::chat` | `Player` | `bool` | `string message` |
| `player::command` | `Player` | `bool` | `—` |
| `player::connect` | `Player` | `—` | `—` |
| `player::death` | `Player` | `—` | `Player killer` |
| `player::disconnect` | `Player` | `—` | `—` |
| `player::enter_vehicle` | `Player` | `—` | `Vehicle car` |
| `player::exit_vehicle` | `Player` | `—` | `Vehicle car` |
| `player::key_state_change` | `Player` | `—` | `int newkeys, int oldkeys` |
| `player::pickup` | `Player` | `—` | `int pickupid` |
| `player::request_class` | `Player` | `bool` | `int classid` |
| `player::request_class_done` | `Player` | `—` | `int classid, int skin` |
| `player::request_spawn` | `Player` | `bool` | `—` |
| `player::select_object` | `Player` | `—` | `int objecttype, int objectid, int modelid, float x, float y, float z` |
| `player::spawn` | `Player` | `—` | `—` |
| `player::state_change` | `Player` | `—` | `int newstate, int oldstate` |
| `player::stats` | `Player` | `—` | `int money, int drunk` |
| `player::trailer_sync` | `Player` | `—` | `int vid` |
| `player::unoccupied_sync` | `Player` | `—` | `int vid, float health` |
| `player::update` | `Player` | `—` | `float x, float y, float z` |
| `player::weapon_shot` | `Player` | `—` | `int weaponid, int hittype, int hitid, float hx, float hy, float hz` |
| `system::start` | `—` | `—` | `—` |
| `system::stop` | `—` | `—` | `—` |
| `textdraw::click` | `Player` | `—` | `TextDraw td` |
| `textdraw::create` | `—` | `TextDraw` | `int x, int y, string text` |
| `timer::every` | `Broadcast` | `—` | `—` |
| `vehicle::create` | `—` | `Vehicle` | `int model, float x, float y, float z` |
| `vehicle::damage_status_update` | `—` | `—` | `int vid, int pid, int panels, int doors, int lights, int tyres` |
| `vehicle::death` | `—` | `—` | `int vid, int killer` |
| `vehicle::spawn` | `—` | `—` | `—` |
| `world::actor_damage` | `—` | `—` | `int actorid, int playerid, float amount, int weaponid, int bodypart` |
| `world::area_enter` | `Player` | `—` | `int area` |
| `world::area_leave` | `Player` | `—` | `int area` |
| `world::checkpoint` | `Player` | `—` | `float x, float y, float z` |
| `world::checkpoint_leave` | `Player` | `—` | `—` |
| `world::object_create` | `—` | `Object` | `int model, float x, float y, float z` |
| `world::race_checkpoint_enter` | `Player` | `—` | `—` |
| `world::race_checkpoint_leave` | `Player` | `—` | `—` |

## Signatures

### `dialog::response`

```knight
dialog::response(int id, bool accepted, string input, int listitem) { ... };
```

### `player::aim`

```knight
player::aim(int camMode, int camZoom, int weaponState) { ... };
```

### `player::chat`

```knight
player::chat(string message) { ... };
```

### `player::command`

```knight
player::command() { ... };
```

### `player::connect`

```knight
player::connect() { ... };
```

### `player::death`

```knight
player::death(Player killer) { ... };
```

### `player::disconnect`

```knight
player::disconnect() { ... };
```

### `player::enter_vehicle`

```knight
player::enter_vehicle(Vehicle car) { ... };
```

### `player::exit_vehicle`

```knight
player::exit_vehicle(Vehicle car) { ... };
```

### `player::key_state_change`

```knight
player::key_state_change(int newkeys, int oldkeys) { ... };
```

### `player::pickup`

```knight
player::pickup(int pickupid) { ... };
```

### `player::request_class`

```knight
player::request_class(int classid) { ... };
```

### `player::request_class_done`

```knight
player::request_class_done(int classid, int skin) { ... };
```

### `player::request_spawn`

```knight
player::request_spawn() { ... };
```

### `player::select_object`

```knight
player::select_object(int objecttype, int objectid, int modelid, float x, float y, float z) { ... };
```

### `player::spawn`

```knight
player::spawn() { ... };
```

### `player::state_change`

```knight
player::state_change(int newstate, int oldstate) { ... };
```

### `player::stats`

```knight
player::stats(int money, int drunk) { ... };
```

### `player::trailer_sync`

```knight
player::trailer_sync(int vid) { ... };
```

### `player::unoccupied_sync`

```knight
player::unoccupied_sync(int vid, float health) { ... };
```

### `player::update`

```knight
player::update(float x, float y, float z) { ... };
```

### `player::weapon_shot`

```knight
player::weapon_shot(int weaponid, int hittype, int hitid, float hx, float hy, float hz) { ... };
```

### `system::start`

```knight
system::start() { ... };
```

### `system::stop`

```knight
system::stop() { ... };
```

### `textdraw::click`

```knight
textdraw::click(TextDraw td) { ... };
```

### `textdraw::create`

```knight
textdraw::create(int x, int y, string text) { ... };
```

### `timer::every`

```knight
timer::every() { ... };
```

### `vehicle::create`

```knight
vehicle::create(int model, float x, float y, float z) { ... };
```

### `vehicle::damage_status_update`

```knight
vehicle::damage_status_update(int vid, int pid, int panels, int doors, int lights, int tyres) { ... };
```

### `vehicle::death`

```knight
vehicle::death(int vid, int killer) { ... };
```

### `vehicle::spawn`

```knight
vehicle::spawn() { ... };
```

### `world::actor_damage`

```knight
world::actor_damage(int actorid, int playerid, float amount, int weaponid, int bodypart) { ... };
```

### `world::area_enter`

```knight
world::area_enter(int area) { ... };
```

### `world::area_leave`

```knight
world::area_leave(int area) { ... };
```

### `world::checkpoint`

```knight
world::checkpoint(float x, float y, float z) { ... };
```

### `world::checkpoint_leave`

```knight
world::checkpoint_leave() { ... };
```

### `world::object_create`

```knight
world::object_create(int model, float x, float y, float z) { ... };
```

### `world::race_checkpoint_enter`

```knight
world::race_checkpoint_enter() { ... };
```

### `world::race_checkpoint_leave`

```knight
world::race_checkpoint_leave() { ... };
```

