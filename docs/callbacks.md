# Knight — Callback Reference

Callbacks receive `playerid` (int) first.

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

## Signatures

- `dialog::response(int playerid, int id, bool accepted, string input, int listitem)`
- `player::aim(int playerid, int camMode, int camZoom, int weaponState)`
- `player::chat(int playerid, string message)`
- `player::command(int playerid)`
- `player::connect(int playerid)`
- `player::death(int playerid, Player killer)`
- `player::disconnect(int playerid)`
- `player::enter_vehicle(int playerid, Vehicle car)`
- `player::exit_vehicle(int playerid, Vehicle car)`
- `player::finished_downloading(int playerid, int virtualworld)`
- `player::key_state_change(int playerid, int newkeys, int oldkeys)`
- `player::pickup(int playerid, int pickupid)`
- `player::request_class(int playerid, int classid)`
- `player::request_class_done(int playerid, int classid, int skin)`
- `player::request_download(int playerid, int type, int crc)`
- `player::request_spawn(int playerid)`
- `player::select_object(int playerid, int objecttype, int objectid, int modelid, float x, float y, float z)`
- `player::spawn(int playerid)`
- `player::state_change(int playerid, int newstate, int oldstate)`
- `player::stats(int playerid, int money, int drunk)`
- `player::trailer_sync(int playerid, int vid)`
- `player::unoccupied_sync(int playerid, int vid, float health)`
- `player::update(int playerid, float x, float y, float z)`
- `player::weapon_shot(int playerid, int weaponid, int hittype, int hitid, float hx, float hy, float hz)`
- `system::start()`
- `system::stop()`
- `textdraw::click(int playerid, TextDraw td)`
- `textdraw::create(int x, int y, string text)`
- `timer::every()`
- `vehicle::create(int model, float x, float y, float z)`
- `vehicle::damage_status_update(int vid, int pid, int panels, int doors, int lights, int tyres)`
- `vehicle::death(int vid, int killer)`
- `vehicle::spawn()`
- `world::actor_damage(int actorid, int playerid, float amount, int weaponid, int bodypart)`
- `world::area_enter(int playerid, int area)`
- `world::area_leave(int playerid, int area)`
- `world::checkpoint(int playerid, float x, float y, float z)`
- `world::checkpoint_leave(int playerid)`
- `world::object_create(int model, float x, float y, float z)`
- `world::race_checkpoint_enter(int playerid)`
- `world::race_checkpoint_leave(int playerid)`
