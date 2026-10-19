# Knight Scripting API Reference

Knight is native-first: call native functions directly by name, e.g.
`SetPlayerHealth(playerid, 100.0)`. Callbacks receive `playerid` as their
first argument. There is no `sa.` prefix and no `self`.

See the full references shipped with the language:

- Native functions: `docs/natives.md`
- Callbacks: `docs/callbacks.md`
- Language: `docs/language.md`
- Built-ins: `docs/builtins.md`
- Configuration: `docs/configuration.md`

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

Put them in the folder named by `artpath` in `server.cfg` (default `Models`,
next to `server.cfg`):

```
core/
├── server.cfg        # useartwork 1 / artpath Models
├── Models/           # <-- custom.dff, custom.txd, veh.dff, veh.txd, ...
└── Gamemodes/
```

File arguments work like C++ includes — pass any path you like:

```knight
AddSimpleModel(-1, 19379, -2000, "veh.dff", "veh.txd");                 // bare name -> artpath/veh.dff
AddSimpleModel(-1, 19379, -2001, "assets/veh.dff", "assets/veh.txd");  // relative to the server CWD
AddSimpleModel(-1, 19379, -2002, "/srv/models/veh.dff", "/srv/models/veh.txd"); // absolute
```

A bare file name is looked up under `artpath`; a path containing `/` or `\`
(relative) or an absolute path is used verbatim. Download URLs use the file
name (`basename`), so serve the folder named in the URL, not the original
nested path. `artpath` is resolved against the server's working directory; on
Linux names are case-sensitive (`Models` != `models`).
At startup the server logs the resolved folder, or a warning if it is missing.
