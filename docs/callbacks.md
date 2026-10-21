# Knight — Callback Reference

Callbacks are declared as `namespace::name(params) { ... };` — the trailing `;`
is required. The declarative form `on namespace::name(params) { ... };` is
equivalent. Player-scoped callbacks receive `playerid` as a plain `int`.

A boolean return acts as a veto: `false` stops the event for every later
handler (and, for `player::chat`, the default relay).

There are **41** callbacks.

| Callback | Player-scoped | Returns | Parameters | Description |
|---|---|---|---|---|
| `dialog::response` | yes | — | `(int id, bool accepted, string input, int listitem)` | A player responded to a dialog; `accepted` is false on cancel, `listitem` is the selected row. |
| `player::aim` | yes | — | `(int camMode, int camZoom, int weaponState)` | A player is aiming; exposes camera mode/zoom and weapon state. |
| `player::chat` | yes | bool | `(string message)` | A player sent chat text; return true to relay it, false to swallow it. |
| `player::command` | yes | bool | `(/name, ...)` | A player ran a command declared as `player::command(\"/name\", ...)`. |
| `player::connect` | yes | — | `()` | A player has connected; send a welcome, open a login dialog or set the camera. |
| `player::death` | yes | — | `(player killer)` | A player died; `killer` is null when there is no attacker. |
| `player::disconnect` | yes | — | `()` | A player has disconnected; clean up per-player state. |
| `player::enter_vehicle` | yes | — | `(vehicle car)` | A player entered a vehicle (as driver or passenger). |
| `player::exit_vehicle` | yes | — | `(vehicle car)` | A player exited a vehicle. |
| `player::finished_downloading` | yes | — | `(int virtualworld)` | A 0.3.DL client finished downloading custom models for a virtual world. |
| `player::key_state_change` | yes | — | `(int newkeys, int oldkeys)` | A player's key state changed; compare newkeys/oldkeys for press/release. |
| `player::pickup` | yes | — | `(int pickupid)` | A player picked up a pickup. |
| `player::request_class` | yes | bool | `(int classid)` | A player requested a class; return false to veto the selection. |
| `player::request_class_done` | yes | — | `(int classid, int skin)` | The class response was sent to the client; apply the chosen skin/camera here. |
| `player::request_download` | yes | bool | `(int type, int crc)` | A 0.3.DL client requested a custom model/texture; return false to deny, or call RedirectDownload. |
| `player::request_spawn` | yes | bool | `()` | A player requested to spawn; return false to veto the spawn. |
| `player::select_object` | yes | — | `(int objecttype, int objectid, int modelid, float x, float y, float z)` | A player selected an object in the map editor. |
| `player::spawn` | yes | — | `()` | A player has spawned; reset health/armour and initialise gameplay state. |
| `player::state_change` | yes | — | `(int newstate, int oldstate)` | A player's state changed (on foot, driving, dead, ...). |
| `player::stats` | yes | — | `(int money, int drunk)` | A player's money/drunk statistics changed. |
| `player::trailer_sync` | yes | — | `(int vid)` | A trailer synced to a vehicle. |
| `player::unoccupied_sync` | yes | — | `(int vid, float health)` | An unoccupied vehicle synced; raw vehicle health sample. |
| `player::update` | yes | — | `(float x, float y, float z)` | A player sync update arrived; raw position for anticheat and logic. |
| `player::weapon_shot` | yes | — | `(int weaponid, int hittype, int hitid, float hx, float hy, float hz)` | A player fired a weapon; reports the hit type, target and coordinates. |
| `system::start` | — | — | `()` | Fires once when the gamemode loads; set up globals, classes and world state here. |
| `system::stop` | — | — | `()` | Fires when the server shuts down; release resources and persist state here. |
| `textdraw::click` | yes | — | `(textdraw td)` | A player clicked a selectable text draw (65535 = cancel/empty area). |
| `textdraw::create` | — | — | `(int x, int y, string text)` | Factory event to construct a text draw; return the created TextDraw. |
| `timer::every` | — | — | `()` | Periodic timer callback context; use with the timer natives. |
| `vehicle::create` | — | — | `(int model, float x, float y, float z)` | Factory event to construct a vehicle; return the created Vehicle. |
| `vehicle::damage_status_update` | — | — | `(int vid, int pid, int panels, int doors, int lights, int tyres)` | A vehicle's panel/door/light/tyre damage changed. |
| `vehicle::death` | — | — | `(int vid, int killer)` | A vehicle was destroyed; `killer` is the responsible player id. |
| `vehicle::spawn` | — | — | `()` | A vehicle respawned. |
| `world::actor_damage` | — | — | `(int actorid, int playerid, float amount, int weaponid, int bodypart)` | An actor took damage; reports attacker, amount, weapon and body part. |
| `world::area_enter` | yes | — | `(int area)` | A player entered a dynamic area. |
| `world::area_leave` | yes | — | `(int area)` | A player left a dynamic area. |
| `world::checkpoint` | yes | — | `(float x, float y, float z)` | A player entered their checkpoint. |
| `world::checkpoint_leave` | yes | — | `()` | A player left their checkpoint. |
| `world::object_create` | — | — | `(int model, float x, float y, float z)` | Factory event to construct an object; return the created Object. |
| `world::race_checkpoint_enter` | yes | — | `()` | A player entered their race checkpoint. |
| `world::race_checkpoint_leave` | yes | — | `()` | A player left their race checkpoint. |
