# Knight Scripting API Reference

Knight is native-first: call native functions directly by name, e.g.
`SetPlayerHealth(playerid, 100.0)`. Callbacks receive `playerid` as their
first argument. There is no `sa.` prefix and no `self`.

See the full references shipped with the language:

- Native functions: `docs/natives.md` (559, with signatures)
- Callbacks: `docs/callbacks.md` (41)
- Language: `docs/language.md`
- Built-ins: `docs/builtins.md` (60)
- Configuration: `docs/configuration.md` (server.cfg is optional)
- Modules and plugins: `docs/plugins.md`

## Quick syntax tour

```knight
system::config() { server.name = "My Server"; };   // no server.cfg needed

const MAX_HP = 100;

function heal(Player target, float hp = MAX_HP) {  // typed + default args
    if (hp > MAX_HP) { hp = MAX_HP; }
    SetPlayerHealth(target, hp);
}

player::command("/top", int n) {
    let scores = {};
    for (let i = 0; i < PlayerCount(); i += 1) {
        if (!IsPlayerConnected(i)) { continue; }
        scores[i] = GetPlayerScore(i);
    }
    let shown = 0;
    for (let key in sort(keys(scores))) {
        if (shown >= n) { break; }
        SendClientMessage(playerid, "{key}: {scores[key]}");
        shown += 1;
    }
}

on player::chat(string message) {                  // declarative hook
    if (contains(lower(message), "cheat")) { return false; }
    return true;
};
```

## Modules and plugins

```knight
// Gamemodes/main.sa
import "economy";
system::config() { server.plugins = ["plugins", "mods/anticheat.sa"]; };
```

- `module "name" { ... };`, `import "x";`, `export function ...` split a
  gamemode across files; modules are type-checked together.
- A boolean handler returning `false` vetoes the event for later handlers.
- `server.plugins` accepts folders (Go plugins and `.sa` files) or a single
  `.sa` file. Script plugins need no rebuild.
- The JSON plugin ships compiled in: `JsonParse`, `JsonGetInt`, `JsonSaveFile`, …

See `docs/plugins.md`.

## SA-MP 0.3.DL custom models

Natives: `AddCharModel(baseid, newid, dff, txd)`, `AddSimpleModel(vw, baseid, newid, dff, txd)`,
`AddSimpleModelTimed(...)`, `FindModelFileNameFromCRC(crc)`,
`FindTextureFileNameFromCRC(crc)`, `RedirectDownload(playerid, url)`,
`GetPlayerCustomSkin(playerid)`, `IsValidCustomModel(id)`.

Callbacks: `player::request_download(type, crc)` (return false to deny) and
`player::finished_downloading(virtualworld)`.

Ranges: custom skins 20001–30000, custom objects −30000..−1000.
Server settings: `useartwork`, `artpath`, `artwork_cdn`, `artwork_port`.
0.3.7 clients never receive model RPCs and automatically fall back to base ids.

### Custom vehicles (0.3.DL)

0.3.DL has no vehicle model type. A custom vehicle is a drivable base vehicle
with a custom object attached:

```knight
let vid = CreateCustomVehicle(411, -2000, x, y, z, angle, c1, c2, true);
// true = hide the chassis for 0.3.DL clients; 0.3.7 keeps the base model
let obj = GetCustomVehicleObject(vid);
DestroyCustomVehicle(vid);
```

`custom_invisible_vehicle_model` (server.cfg, default 570) selects the hidden
chassis model.

### Where do .dff / .txd files go?

Anywhere you like — file arguments behave like C++ includes:

```knight
AddSimpleModel(-1, 19379, -2000, "/srv/models/veh.dff", "/srv/models/veh.txd"); // absolute
AddSimpleModel(-1, 19379, -2001, "assets/veh.dff", "assets/veh.txd");           // relative to CWD
AddSimpleModel(-1, 19379, -2002, "veh.dff", "veh.txd");                         // bare -> artpath
```

- A path containing `/` or `\` (or an absolute path) is used verbatim,
  relative to the server's working directory.
- A bare file name is looked up under the optional `artpath` setting. With no
  `artpath`, bare names are rejected with "give a full path (or set artpath...)".
- `useartwork 1` is the default; `useartwork 0` disables custom models entirely.
- Download URLs use the file name (`basename`). Point `artwork_cdn` at a folder
  that exposes those names (nested source paths are not mirrored automatically).
- Names are case-sensitive on Linux.
- There is no required `Models/` or `Scriptfiles/` folder in the distribution.
