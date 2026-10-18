# Knight — Event Reference

Every event handler is declared as `namespace::name(params) { ... };`.
`self` is implicit for handlers with a subject.

### `dialog::response`

- self: `Player`
- returns: `—`
- params: `int id, bool accepted, string input, int listitem`

```knight
dialog::response(int id, bool accepted, string input, int listitem) { ... };
```

### `player::aim`

- self: `Player`
- returns: `—`
- params: `int camMode, int camZoom, int weaponState`

```knight
player::aim(int camMode, int camZoom, int weaponState) { ... };
```

### `player::chat`

- self: `Player`
- returns: `bool`
- params: `string message`

```knight
player::chat(string message) { ... };
```

### `player::command`

- self: `Player`
- returns: `bool`
- params: none

```knight
player::command() { ... };
```

### `player::connect`

- self: `Player`
- returns: `—`
- params: none

```knight
player::connect() { ... };
```

### `player::death`

- self: `Player`
- returns: `—`
- params: `Player killer`

```knight
player::death(Player killer) { ... };
```

### `player::disconnect`

- self: `Player`
- returns: `—`
- params: none

```knight
player::disconnect() { ... };
```

### `player::enter_vehicle`

- self: `Player`
- returns: `—`
- params: `Vehicle car`

```knight
player::enter_vehicle(Vehicle car) { ... };
```

### `player::exit_vehicle`

- self: `Player`
- returns: `—`
- params: `Vehicle car`

```knight
player::exit_vehicle(Vehicle car) { ... };
```

### `player::key_state_change`

- self: `Player`
- returns: `—`
- params: `int newkeys, int oldkeys`

```knight
player::key_state_change(int newkeys, int oldkeys) { ... };
```

### `player::pickup`

- self: `Player`
- returns: `—`
- params: `int pickupid`

```knight
player::pickup(int pickupid) { ... };
```

### `player::request_class`

- self: `Player`
- returns: `bool`
- params: `int classid`

```knight
player::request_class(int classid) { ... };
```

### `player::request_class_done`

- self: `Player`
- returns: `—`
- params: `int classid, int skin`

```knight
player::request_class_done(int classid, int skin) { ... };
```

### `player::request_spawn`

- self: `Player`
- returns: `bool`
- params: none

```knight
player::request_spawn() { ... };
```

### `player::select_object`

- self: `Player`
- returns: `—`
- params: `int objecttype, int objectid, int modelid, float x, float y, float z`

```knight
player::select_object(int objecttype, int objectid, int modelid, float x, float y, float z) { ... };
```

### `player::spawn`

- self: `Player`
- returns: `—`
- params: none

```knight
player::spawn() { ... };
```

### `player::state_change`

- self: `Player`
- returns: `—`
- params: `int newstate, int oldstate`

```knight
player::state_change(int newstate, int oldstate) { ... };
```

### `player::stats`

- self: `Player`
- returns: `—`
- params: `int money, int drunk`

```knight
player::stats(int money, int drunk) { ... };
```

### `player::trailer_sync`

- self: `Player`
- returns: `—`
- params: `int vid`

```knight
player::trailer_sync(int vid) { ... };
```

### `player::unoccupied_sync`

- self: `Player`
- returns: `—`
- params: `int vid, float health`

```knight
player::unoccupied_sync(int vid, float health) { ... };
```

### `player::update`

- self: `Player`
- returns: `—`
- params: `float x, float y, float z`

```knight
player::update(float x, float y, float z) { ... };
```

### `player::weapon_shot`

- self: `Player`
- returns: `—`
- params: `int weaponid, int hittype, int hitid, float hx, float hy, float hz`

```knight
player::weapon_shot(int weaponid, int hittype, int hitid, float hx, float hy, float hz) { ... };
```

### `system::start`

- self: `—`
- returns: `—`
- params: none

```knight
system::start() { ... };
```

### `system::stop`

- self: `—`
- returns: `—`
- params: none

```knight
system::stop() { ... };
```

### `textdraw::click`

- self: `Player`
- returns: `—`
- params: `TextDraw td`

```knight
textdraw::click(TextDraw td) { ... };
```

### `textdraw::create`

- self: `—`
- returns: `TextDraw`
- params: `int x, int y, string text`

```knight
textdraw::create(int x, int y, string text) { ... };
```

### `timer::every`

- self: `Broadcast`
- returns: `—`
- params: none

```knight
timer::every() { ... };
```

### `vehicle::create`

- self: `—`
- returns: `Vehicle`
- params: `int model, float x, float y, float z`

```knight
vehicle::create(int model, float x, float y, float z) { ... };
```

### `vehicle::damage_status_update`

- self: `—`
- returns: `—`
- params: `int vid, int pid, int panels, int doors, int lights, int tyres`

```knight
vehicle::damage_status_update(int vid, int pid, int panels, int doors, int lights, int tyres) { ... };
```

### `vehicle::death`

- self: `—`
- returns: `—`
- params: `int vid, int killer`

```knight
vehicle::death(int vid, int killer) { ... };
```

### `vehicle::spawn`

- self: `—`
- returns: `—`
- params: none

```knight
vehicle::spawn() { ... };
```

### `world::actor_damage`

- self: `—`
- returns: `—`
- params: `int actorid, int playerid, float amount, int weaponid, int bodypart`

```knight
world::actor_damage(int actorid, int playerid, float amount, int weaponid, int bodypart) { ... };
```

### `world::area_enter`

- self: `Player`
- returns: `—`
- params: `int area`

```knight
world::area_enter(int area) { ... };
```

### `world::area_leave`

- self: `Player`
- returns: `—`
- params: `int area`

```knight
world::area_leave(int area) { ... };
```

### `world::checkpoint`

- self: `Player`
- returns: `—`
- params: `float x, float y, float z`

```knight
world::checkpoint(float x, float y, float z) { ... };
```

### `world::checkpoint_leave`

- self: `Player`
- returns: `—`
- params: none

```knight
world::checkpoint_leave() { ... };
```

### `world::object_create`

- self: `—`
- returns: `Object`
- params: `int model, float x, float y, float z`

```knight
world::object_create(int model, float x, float y, float z) { ... };
```

### `world::race_checkpoint_enter`

- self: `Player`
- returns: `—`
- params: none

```knight
world::race_checkpoint_enter() { ... };
```

### `world::race_checkpoint_leave`

- self: `Player`
- returns: `—`
- params: none

```knight
world::race_checkpoint_leave() { ... };
```

