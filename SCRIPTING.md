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
