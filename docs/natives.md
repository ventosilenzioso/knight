# Knight — Native Function Reference

Natives are global functions: call them by name, with no `sa.` prefix and no `self`.

There are **559** natives.

| Native | Description |
|---|---|
| `AddCharModel(int baseid, int newid, string dffname, string txdname) -> bool` | Register a custom character model (skin). |
| `AddMenuItem(int menuid, int column, string text) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `AddPlayerClass(int model, float x, float y, float z, float angle, int weapon1, int ammo1, int weapon2, int ammo2, int weapon3, int ammo3) -> int` | Add a spawn class (skin, position, angle, optional weapons). |
| `AddPlayerClassEx(int team, int model, float x, float y, float z, float angle, int weapon1, int ammo1, int weapon2, int ammo2, int weapon3, int ammo3) -> int` | Add a spawn class for a specific team. |
| `AddSimpleModel(int virtualworld, int baseid, int newid, string dffname, string txdname) -> bool` | Register an object model for custom objects. |
| `AddSimpleModelTimed(int virtualworld, int baseid, int newid, string dffname, string txdname, int timeon, int timeoff) -> bool` | Register a time-limited custom object model. |
| `AddStaticPickup(int model, int typ, float x, float y, float z, int virtualWorld) -> bool` | Create a static pickup (engine-managed). |
| `AddStaticVehicle(int model, float x, float y, float z, float angle, int colour1, int colour2) -> int` | Create a static vehicle (engine-managed). |
| `AddStaticVehicleEx(int model, float x, float y, float z, float angle, int colour1, int colour2, int respawnDelay, bool addsiren) -> int` | Create a static vehicle with respawn delay. |
| `AddVehicleComponent(int vehicleID, int componentID) -> bool` | Attach a visual component to a vehicle. |
| `AllowAdminTeleport(bool allow) -> bool` | Allow admins to teleport with the map. |
| `AllowInteriorWeapons(bool allow) -> bool` | Allow weapons inside interiors. |
| `AllowPlayerTeleport(bool allow) -> bool` | Allow the player to teleport via the map. |
| `ApplyActorAnimation(int id, string animLib, string animName, float delta, bool loop, bool lockX, bool lockY, bool freeze, int time) -> bool` | Play an animation on an actor. |
| `ApplyAnimation()` | Play a library/name animation on a player. |
| `ApplyDynamicActorAnimation(int id, string animLib, string animName, float delta, bool loop, bool lockX, bool lockY, bool freeze, int time) -> bool` | Play an animation on a dynamic actor. |
| `ApplyPlayerAnimation(int playerID, string animLib, string animName, float delta, bool loop, bool lockX, bool lockY, bool freeze, int timeMS) -> bool` | Play an animation on a player. |
| `Attach3DTextLabelToPlayer(int id, int playerID, float offsetX, float offsetY, float offsetZ) -> bool` | Attach a 3D text label to a player. |
| `Attach3DTextLabelToVehicle(int id, int vehicleID, float offsetX, float offsetY, float offsetZ) -> bool` | Attach a 3D text label to a vehicle. |
| `AttachCameraToObject(int playerID, int objectID) -> bool` | Attach the player camera to an object. |
| `AttachCameraToPlayerObject(int playerID, int objectID) -> bool` | Attach the camera to a player object. |
| `AttachDynamicObjectToPlayer(int id, int playerID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach a dynamic object to a player. |
| `AttachDynamicObjectToVehicle(int id, int vehicleID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach a dynamic object to a vehicle. |
| `AttachObjectToObject(int id, int attachToID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ, bool syncRotation) -> bool` | Attach an object to another object. |
| `AttachObjectToPlayer(int id, int playerID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach an object to a player bone. |
| `AttachObjectToVehicle(int id, int vehicleID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach an object to a vehicle. |
| `AttachPlayerObjectToPlayer(int objectID, int playerID, int targetID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach a player object to a player. |
| `AttachPlayerObjectToVehicle(int objectID, int playerID, int vehicleID, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ) -> bool` | Attach a player object to a vehicle. |
| `AttachTrailerToVehicle(int trailerID, int vehicleID) -> bool` | Attach a trailer to a vehicle. |
| `Ban(int playerID) -> bool` | Ban a player by id. |
| `BanEx()` | Ban a player with a reason. |
| `BanPlayer(int playerID, string reason) -> bool` | Ban a player with an optional reason. |
| `BlockIpAddress(string ip, int time_ms) -> bool` | Block an IP address for a duration. |
| `CallLocalFunction(string function, ...args) -> int` | Call a top-level function by name and return its value as an int. |
| `CallRemoteFunction(string function, ...args) -> int` | Alias of CallLocalFunction: call a top-level function by name. |
| `CancelEdit(int playerID) -> bool` | Cancel object editing for a player. |
| `CancelSelectTextDraw()` | Cancel text draw selection mode. |
| `ChangeVehicleColor(int vehicleID, int color1, int color2) -> bool` | Change a vehicle's colours. |
| `ChangeVehiclePaintjob(int vehicleID, int paintjob) -> bool` | Change a vehicle's paintjob. |
| `ClearActorAnimation()` | Stop an actor's animation. |
| `ClearActorAnimations(int id) -> bool` | Stop all animations on an actor. |
| `ClearAnimations()` | Stop a player's animation. |
| `ClearDynamicActorAnimations(int id) -> bool` | Stop all animations on a dynamic actor. |
| `ClearPlayerAnimation(int playerID) -> bool` | Stop a player's animation. |
| `ConnectNPC(string name, string script) -> bool` | Connect an NPC into the world. |
| `Create3DTextLabel(string text, int colour, float x, float y, float z, float drawDistance, int testLOS, int virtualWorld) -> int` | Create a 3D text label in the world. |
| `Create3DTextLabelAttachedToPlayer(string text, int colour, float x, float y, float z, float drawDistance, int testLOS, int attachToPlayerID) -> int` | Create a 3D label attached to a player. |
| `Create3DTextLabelAttachedToVehicle(string text, int colour, float x, float y, float z, float drawDistance, int testLOS, int attachToVehicleID) -> int` | Create a 3D label attached to a vehicle. |
| `CreateActor(int skin, float x, float y, float z, float angle) -> int` | Create a static actor. |
| `CreateCustomVehicle(int baseModel, int objModel, float x, float y, float z, float angle, int colour1, int colour2, bool invisible) -> int` | Create a drivable base vehicle with a custom object model attached (0.3.DL). |
| `CreateDynamic3DTextLabel(string text, int colour, float x, float y, float z, float drawDistance, int attachedPlayer, int attachedVehicle, bool testLOS, int world, int interior, int playerid, float streamDistance) -> int` | Create a streamed 3D text label. |
| `CreateDynamicActor(int model, float x, float y, float z, float angle, bool invulnerable, float health, int world, int interior, int playerid, float streamDistance) -> int` | Create a streamed dynamic actor. |
| `CreateDynamicCP(float x, float y, float z, float radius, int world, int interior, int playerid, float streamDistance) -> int` | Create a streamed checkpoint. |
| `CreateDynamicCircle(float x, float y, float radius, int world) -> int` | Create a streamed circular area. |
| `CreateDynamicMapIcon(float x, float y, float z, int typ, int colour, int world, int interior, int playerid, float streamDistance, int style) -> int` | Create a streamed radar map icon. |
| `CreateDynamicObject(int playerID, int model, float x, float y, float z, float rx, float ry, float rz, int world, int interior, int owner, float streamDistance) -> int` | Create a streamed object. |
| `CreateDynamicPickup(int model, int typ, float x, float y, float z, int world, int interior, int playerid, float streamDistance) -> int` | Create a streamed pickup. |
| `CreateDynamicRaceCP(int cpType, float x, float y, float z, float nextX, float nextY, float nextZ, float radius, int world, int interior, int playerid, float streamDistance) -> int` | Create a streamed race checkpoint. |
| `CreateDynamicRectangle(float minX, float minY, float maxX, float maxY, int world) -> int` | Create a streamed rectangular area. |
| `CreateExplosion(float x, float y, float z, int typ, float radius) -> bool` | Create an explosion in the world. |
| `CreateExplosionForPlayer(int playerID, float x, float y, float z, int typ, float radius) -> bool` | Create an explosion visible to one player. |
| `CreateMenu(string title, int columns, float x, float y, float col1width, float col2width) -> int` | Menu emulation: returns -1. Use dialogs for real UI. |
| `CreateObject(int model, float x, float y, float z, float rotX, float rotY, float rotZ, float drawDistance) -> int` | Create a global object. |
| `CreatePickup(int model, int typ, float x, float y, float z) -> int` | Create a pickup. |
| `CreatePlayer3DTextLabel(int playerID, string text, int colour, float x, float y, float z, float drawDistance, int attachedPlayer, int attachedVehicle, int testLOS) -> int` | Create a player-local 3D text label. |
| `CreatePlayerObject(int playerID, int model, float x, float y, float z, float rotX, float rotY, float rotZ, float drawDistance) -> int` | Create a player-local object. |
| `CreatePlayerTextDraw(int playerid, float x, float y, string text) -> int` | Create a per-player text draw and return its id. |
| `CreatePlayerVehicle(int playerid, int model, float x, float y, float z, float angle, int colour1, int colour2) -> int` | Create a vehicle owned by a player (ownership is bookkeeping for GetPlayerVehicleCount). |
| `CreateVehicle(int model, float x, float y, float z, float angle, int colour1, int colour2) -> int` | Create a vehicle; returns its id. |
| `Delete3DTextLabel(int id) -> bool` | Delete a 3D text label. |
| `DeletePVar(int playerID, string name) -> bool` | Delete a player variable. |
| `DeletePlayer3DTextLabel(int playerID, int id) -> bool` | Delete a player 3D text label. |
| `DeleteSVar(string name) -> bool` | Delete a server variable. |
| `DestroyActor(int id) -> bool` | Destroy a static actor. |
| `DestroyCustomVehicle(int vehicleID) -> bool` | Destroy a custom vehicle and its attached object. |
| `DestroyDynamic3DTextLabel(int id) -> bool` | Destroy a streamed 3D text label. |
| `DestroyDynamicActor(int id) -> bool` | Destroy a dynamic actor. |
| `DestroyDynamicArea(int id) -> bool` | Destroy a dynamic area. |
| `DestroyDynamicCP(int id) -> bool` | Destroy a streamed checkpoint. |
| `DestroyDynamicMapIcon(int id) -> bool` | Destroy a streamed map icon. |
| `DestroyDynamicObject(int id) -> bool` | Destroy a streamed object. |
| `DestroyDynamicPickup(int id) -> bool` | Destroy a streamed pickup. |
| `DestroyDynamicRaceCP(int id) -> bool` | Destroy a streamed race checkpoint. |
| `DestroyMenu(int menuid) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `DestroyObject(int id) -> bool` | Destroy a global object. |
| `DestroyPickup(int id) -> bool` | Destroy a pickup. |
| `DestroyPlayerObject(int playerID, int id) -> bool` | Destroy a player object. |
| `DestroyVehicle(int id) -> bool` | Destroy a vehicle. |
| `DetachTrailerFromVehicle(int vehicleID) -> bool` | Detach a trailer from a vehicle. |
| `DisableInteriorEnterExits() -> bool` | Remove interior entrance markers from the map. |
| `DisableMenu(int menuid) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `DisableMenuRow(int menuid, int row) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `DisableNameTagLOS() -> bool` | Remove line-of-sight checks for name tags. |
| `DisablePlayerCheckpoint(int playerID) -> bool` | Remove the player's checkpoint. |
| `DisablePlayerRaceCheckpoint(int playerID) -> bool` | Remove the player's race checkpoint. |
| `DisableRemoteVehicleCollisions(int playerID, bool disable) -> bool` | Disable collisions with remote vehicles. |
| `EditAttachedObject(int playerID, int index) -> bool` | Open the attached-object editor. |
| `EditDynamicObject(int playerID, int id) -> bool` | Open the object editor for a dynamic object. |
| `EditObject(int playerID, int id) -> bool` | Open the object editor. |
| `EditPlayerObject(int playerID, int id) -> bool` | Open the editor for a player object. |
| `EnablePlayerCameraTarget(int playerID, bool enable) -> bool` | Enable camera target queries for a player. |
| `EnableStuntBonusForAll(bool enable) -> bool` | Enable stunt bonuses for everyone. |
| `EnableStuntBonusForPlayer(int playerID, bool enable) -> bool` | Enable stunt bonuses for a player. |
| `EnableTirePopping(bool enable) -> bool` | Enable tyre popping. |
| `EnableVehicleFriendlyFire(bool enable) -> bool` | Allow players in the same team to damage vehicles. |
| `EnableZoneNames(bool enable) -> bool` | Show zone names above the radar. |
| `FindModelFileNameFromCRC(int crc) -> string` | Resolve a model file name from its CRC. |
| `FindTextureFileNameFromCRC(int crc) -> string` | Resolve a texture file name from its CRC. |
| `ForceClassSelection(int playerID) -> bool` | Force the class-selection screen. |
| `GameModeExit() -> bool` | Shut the server down cleanly. |
| `GameTextForAll(int style, int timeMS, string text)` | Show game text to all players. |
| `GameTextForPlayer(int playerID, int style, int timeMS, string text) -> bool` | Show game text to one player. |
| `GangZoneCreate(float minX, float minY, float maxX, float maxY) -> int` | Create a gang zone rectangle. |
| `GangZoneDestroy(int id) -> bool` | Destroy a gang zone. |
| `GangZoneFlashForAll(int id, int colour) -> bool` | Flash a gang zone for all players. |
| `GangZoneFlashForPlayer(int playerID, int id, int colour) -> bool` | Flash a gang zone for one player. |
| `GangZoneHideForAll(int id) -> bool` | Hide a gang zone from all players. |
| `GangZoneHideForPlayer(int playerID, int id) -> bool` | Hide a gang zone from one player. |
| `GangZoneShowForAll(int id, int colour) -> bool` | Show a gang zone to all players. |
| `GangZoneShowForPlayer(int playerID, int id, int colour) -> bool` | Show a gang zone to one player. |
| `GangZoneStopFlashForAll(int id) -> bool` | Stop flashing a gang zone for all players. |
| `GangZoneStopFlashForPlayer(int playerID, int id) -> bool` | Stop flashing a gang zone for one player. |
| `GetActorFacingAngle(int actorID) -> float` | Get an actor's facing angle. |
| `GetActorHealth(int actorID) -> float` | Get an actor's health. |
| `GetActorPoolSize() -> int` | Highest allocated actor id. |
| `GetActorPos(int actorID) -> array` | Get an actor's position. |
| `GetActorVirtualWorld(int actorID) -> int` | Get an actor's virtual world. |
| `GetAnimationName(int index) -> array` | Resolve an animation index to library/name. |
| `GetConsoleVarAsBool()` | Read a boolean console variable. |
| `GetConsoleVarAsInt()` | Read an integer console variable. |
| `GetConsoleVarAsString()` | Read a string console variable. |
| `GetCustomVehicleObject(int vehicleID) -> int` | Get the object id attached to a custom vehicle, or -1. |
| `GetDistanceBetweenPlayers(int player1, int player2) -> float` | Distance between two players. |
| `GetDistanceFromMeToPoint(int playerid, float x, float y, float z) -> float` | Distance from the player to x, y, z. |
| `GetDynamicObjectPos(int id) -> array` | Get a dynamic object's position. |
| `GetDynamicObjectRot(int id) -> array` | Get a dynamic object's rotation. |
| `GetGravity() -> float` | Get the world gravity. |
| `GetMaxPlayers() -> int` | Get the configured player slot count. |
| `GetMyFacingAngle(int playerid) -> float` | Return the player's facing angle (degrees). |
| `GetMyPos(int playerid) -> array` | Return the player's position as an array [x, y, z]. |
| `GetNetworkStats() -> string` | Get network statistics for a player. |
| `GetObjectModel(int objectID) -> int` | Get an object's model id. |
| `GetObjectPos(int objectID) -> array` | Get an object's position. |
| `GetObjectPosX()` | Get an object's X coordinate. |
| `GetObjectPosY()` | Get an object's Y coordinate. |
| `GetObjectPosZ()` | Get an object's Z coordinate. |
| `GetObjectRot(int objectID) -> array` | Get an object's rotation. |
| `GetPVarFloat(int playerID, string name) -> float` | Read a float player variable. |
| `GetPVarInt(int playerID, string name) -> int` | Read an integer player variable. |
| `GetPVarNameAtIndex(int playerID, int index) -> string` | Get a player variable name at an index. |
| `GetPVarString(int playerID, string name) -> string` | Read a string player variable. |
| `GetPVarType(int playerID, string name) -> int` | Get a player variable's type. |
| `GetPVarsUpperIndex(int playerID) -> int` | Highest player variable index. |
| `GetPlayerAmmo(int playerID) -> int` | Get a player's ammo. |
| `GetPlayerAnimationIndex(int playerID) -> int` | Get the current animation index. |
| `GetPlayerArmedWeapon(int playerid) -> int` | Return the weapon the player has armed (currently selected). |
| `GetPlayerArmour(int playerID) -> float` | Get a player's armour. |
| `GetPlayerCameraAspectRatio(int playerID) -> float` | Get the camera aspect ratio. |
| `GetPlayerCameraFrontVector(int playerID) -> array` | Get the camera forward vector. |
| `GetPlayerCameraMode(int playerID) -> int` | Get the camera mode. |
| `GetPlayerCameraPos(int playerID) -> array` | Get the camera position. |
| `GetPlayerCameraTargetActor(int playerID) -> int` | Get the actor the camera targets. |
| `GetPlayerCameraTargetObject(int playerID) -> int` | Get the object the camera targets. |
| `GetPlayerCameraTargetPlayer(int playerID) -> int` | Get the player the camera targets. |
| `GetPlayerCameraTargetVehicle(int playerID) -> int` | Get the vehicle the camera targets. |
| `GetPlayerCameraZoom(int playerID) -> float` | Get the camera zoom. |
| `GetPlayerColor(int playerID) -> int` | Get a player's colour. |
| `GetPlayerCustomSkin(int playerID) -> int` | Get a player's custom skin id. |
| `GetPlayerDistanceFromPoint(int playerID, float x, float y, float z) -> float` | Distance from a player to a point. |
| `GetPlayerDrunkLevel(int playerID) -> int` | Get a player's drunk level. |
| `GetPlayerFacingAngle(int playerID) -> float` | Get a player's facing angle. |
| `GetPlayerFightingStyle(int playerID) -> int` | Get a player's fighting style. |
| `GetPlayerHealth(int playerID) -> float` | Get a player's health. |
| `GetPlayerInterior(int playerID) -> int` | Get a player's interior. |
| `GetPlayerIp(int playerID) -> string` | Get a player's IP address. |
| `GetPlayerKeys(int playerID) -> array` | Get a player's keys, up/down and left/right state. |
| `GetPlayerLastShotVectors(int playerID) -> array` | Get the last shot origin and hit vectors. |
| `GetPlayerMenu(int playerid) -> int` | Return the player's open menu id; always 0 because Knight uses dialogs instead of menus. |
| `GetPlayerMoney(int playerID) -> int` | Get a player's money. |
| `GetPlayerName(int playerid) -> string` | Return the player's name. Alias for PlayerName; the 3-argument Pawn form is accepted and returns the name. |
| `GetPlayerNetworkStats(int playerID) -> string` | Get a player's network statistics. |
| `GetPlayerObjectModel(int playerID, int id) -> int` | Get a player object's model. |
| `GetPlayerObjectPos(int playerID, int id) -> array` | Get a player object's position. |
| `GetPlayerObjectRot(int playerID, int id) -> array` | Get a player object's rotation. |
| `GetPlayerPing(int playerID) -> int` | Get a player's ping. |
| `GetPlayerPoolSize() -> int` | Highest allocated player id. |
| `GetPlayerPos(int playerID) -> array` | Get a player's position. |
| `GetPlayerPosX()` | Get a player's X coordinate. |
| `GetPlayerPosY()` | Get a player's Y coordinate. |
| `GetPlayerPosZ()` | Get a player's Z coordinate. |
| `GetPlayerScore(int playerID) -> int` | Get a player's score. |
| `GetPlayerSkin(int playerID) -> int` | Get a player's skin. |
| `GetPlayerSpecialAction(int playerID) -> int` | Get a player's special action. |
| `GetPlayerState(int playerID) -> int` | Get a player's state. |
| `GetPlayerSurfingObjectID(int playerID) -> int` | Get the object the player is surfing. |
| `GetPlayerSurfingVehicleID(int playerID) -> int` | Get the vehicle the player is surfing. |
| `GetPlayerTargetActor(int playerID) -> int` | Get the actor a player is targeting. |
| `GetPlayerTargetPlayer(int playerID) -> int` | Get the player a player is targeting. |
| `GetPlayerTeam(int playerID) -> int` | Get a player's team. |
| `GetPlayerTime(int playerID) -> array` | Get a player's local time. |
| `GetPlayerVehicleCount(int playerid) -> int` | Number of live vehicles owned by a player. |
| `GetPlayerVehicleID(int playerID) -> int` | Get the vehicle id a player is in. |
| `GetPlayerVehicleSeat(int playerID) -> int` | Get the seat a player occupies. |
| `GetPlayerVehicles(int playerid) -> array` | Array of live vehicle ids owned by a player. |
| `GetPlayerVelocity(int playerID) -> array` | Get a player's velocity. |
| `GetPlayerVersion(int playerID) -> string` | Get a player's client version string. |
| `GetPlayerVirtualWorld(int playerID) -> int` | Get a player's virtual world. |
| `GetPlayerWantedLevel(int playerID) -> int` | Get a player's wanted level. |
| `GetPlayerWeapon(int playerID) -> int` | Get a player's current weapon. |
| `GetPlayerWeaponData(int playerID, int slot) -> array` | Get weapon/ammo for a weapon slot. |
| `GetPlayerWeaponState(int playerID) -> int` | Get the weapon state. |
| `GetSVarFloat(string name) -> float` | Read a float server variable. |
| `GetSVarInt(string name) -> int` | Read an integer server variable. |
| `GetSVarNameAtIndex(int index) -> string` | Get a server variable name at an index. |
| `GetSVarString(string name) -> string` | Read a string server variable. |
| `GetSVarType(string name) -> int` | Get a server variable's type. |
| `GetSVarsUpperIndex() -> int` | Highest server variable index. |
| `GetServerTickRate() -> int` | Get the server tick rate. |
| `GetServerVarAsBool(string name)` | Read a boolean server variable. |
| `GetServerVarAsInt(string name) -> int` | Read an integer server variable. |
| `GetServerVarAsString(string name) -> string` | Read a string server variable. |
| `GetTickCount() -> int` | Milliseconds since server start. |
| `GetVehicleComponentInSlot(int vehicleID, int slot) -> int` | Get the component in a vehicle slot. |
| `GetVehicleComponentType(int component) -> int` | Get a component's type. |
| `GetVehicleDamageStatus(int id) -> array` | Get vehicle panel/door/light/tyre damage. |
| `GetVehicleDistanceFromPoint(int vehicleID, float x, float y, float z) -> float` | Distance from a vehicle to a point. |
| `GetVehicleHealth(int id) -> float` | Get a vehicle's health. |
| `GetVehicleModel(int vehicleID) -> int` | Get a vehicle's model id. |
| `GetVehicleModelInfo(int model, int infoType) -> array` | Get model info (size, seats, ...). |
| `GetVehicleParamsCarDoors(int vehicleID) -> array` | Get vehicle door open states. |
| `GetVehicleParamsCarWindows(int vehicleID) -> array` | Get vehicle window open states. |
| `GetVehicleParamsEx(int vehicleID) -> array` | Get vehicle params (engine, lights, ...). |
| `GetVehicleParamsSirenState(int vehicleID) -> int` | Get the siren state. |
| `GetVehiclePoolSize() -> int` | Highest allocated vehicle id. |
| `GetVehiclePos(int vehicleID) -> array` | Get a vehicle's position. |
| `GetVehiclePosX()` | Get a vehicle's X coordinate. |
| `GetVehiclePosY()` | Get a vehicle's Y coordinate. |
| `GetVehiclePosZ()` | Get a vehicle's Z coordinate. |
| `GetVehicleRotationQuat(int vehicleID) -> array` | Get a vehicle's rotation quaternion. |
| `GetVehicleTrailer(int vehicleID) -> int` | Get a vehicle's attached trailer. |
| `GetVehicleVelocity(int vehicleID) -> array` | Get a vehicle's velocity. |
| `GetVehicleVirtualWorld(int vehicleID) -> int` | Get a vehicle's virtual world. |
| `GetVehicleZAngle(int vehicleID) -> float` | Get a vehicle's Z angle. |
| `GetWeaponName(int weaponid) -> string` | Resolve a weapon id to its name. |
| `GetWorldTime() -> int` | Get the world time. |
| `GivePlayerMoney(int playerID, int amount) -> bool` | Give (or take) money. |
| `GivePlayerWeapon(int playerID, int weaponID, int ammo) -> bool` | Give a weapon with ammo. |
| `HideMenuForPlayer(int menuid, int playerid) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `HidePlayerDialog(int playerID) -> bool` | Close the player's current dialog. |
| `InterpolateCameraLookAt(int playerID, float fromX, float fromY, float fromZ, float toX, float toY, float toZ, int time, int cutType) -> bool` | Interpolate the camera look-at point. |
| `InterpolateCameraPos(int playerID, float fromX, float fromY, float fromZ, float toX, float toY, float toZ, int time, int cutType) -> bool` | Interpolate the camera position. |
| `IsActorInvulnerable(int actorID) -> bool` | Whether an actor is invulnerable. |
| `IsActorStreamedIn(int actorID, int forPlayerID) -> bool` | Whether an actor is streamed to a player. |
| `IsCustomVehicle(int vehicleID) -> bool` | Whether a vehicle was created by CreateCustomVehicle. |
| `IsObjectMoving(int objectID) -> bool` | Whether an object is moving. |
| `IsPlayerAdmin(int playerID) -> bool` | Whether a player is an admin. |
| `IsPlayerAttachedObjectSlotUsed(int playerID, int index) -> bool` | Whether an attached-object slot is used. |
| `IsPlayerCamFrozen(int playerid) -> bool` | Report whether the player's camera is frozen. Always false in Knight. |
| `IsPlayerConnected(int playerID) -> bool` | Whether a player id is connected. |
| `IsPlayerInAnyVehicle(int playerID) -> bool` | Whether a player is in any vehicle. |
| `IsPlayerInCheckpoint(int playerID) -> bool` | Whether a player is in their checkpoint. |
| `IsPlayerInDynamicArea(int playerID, int id) -> bool` | Whether a player is in a dynamic area. |
| `IsPlayerInDynamicCP(int playerID, int id) -> bool` | Whether a player is in a dynamic checkpoint. |
| `IsPlayerInDynamicRaceCP(int playerID, int id) -> bool` | Whether a player is in a dynamic race checkpoint. |
| `IsPlayerInRaceCheckpoint(int playerID) -> bool` | Whether a player is in a race checkpoint. |
| `IsPlayerInRangeOfPoint(int playerID, float radius, float x, float y, float z) -> bool` | Whether a player is within range of a point. |
| `IsPlayerInVehicle(int playerID, int vehicleID) -> bool` | Whether a player is in a specific vehicle. |
| `IsPlayerNPC(int playerID) -> bool` | Whether a player is an NPC. |
| `IsPlayerObjectMoving(int playerID, int id) -> bool` | Whether a player object is moving. |
| `IsPlayerStreamedIn(int playerID, int forPlayerID) -> bool` | Whether a player is streamed to another. |
| `IsTrailerAttachedToVehicle(int vehicleID) -> bool` | Whether a trailer is attached. |
| `IsValidActor(int actorID) -> bool` | Whether an actor id is valid. |
| `IsValidCustomModel()` | Whether an id is a registered custom skin or object id. |
| `IsValidDynamic3DTextLabel(int id) -> bool` | Whether a dynamic 3D label is valid. |
| `IsValidDynamicActor(int id) -> bool` | Whether a dynamic actor is valid. |
| `IsValidDynamicArea(int id) -> bool` | Whether a dynamic area is valid. |
| `IsValidDynamicMapIcon(int id) -> bool` | Whether a dynamic map icon is valid. |
| `IsValidDynamicObject(int id) -> bool` | Whether a dynamic object is valid. |
| `IsValidDynamicPickup(int id) -> bool` | Whether a dynamic pickup is valid. |
| `IsValidMenu(int menuid) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `IsValidObject(int objectID) -> bool` | Whether an object id is valid. |
| `IsValidPlayerObject(int playerID, int id) -> bool` | Whether a player object is valid. |
| `IsValidVehicle(int vehicleID) -> bool` | Whether a vehicle id is valid. |
| `IsVehicleStreamedIn(int vehicleID, int forPlayerID) -> bool` | Whether a vehicle is streamed to a player. |
| `Kick(int playerID) -> bool` | Kick a player. |
| `KickPlayer(int playerID, string reason) -> bool` | Kick a player with an optional reason. |
| `KillTimer(int timerid) -> bool` | Cancel a timer. |
| `LimitGlobalChatRadius(float radius) -> bool` | Limit global chat to a radius. |
| `LimitPlayerMarkerRadius(float radius) -> bool` | Limit player marker radius. |
| `LinkVehicleToInterior(int vehicleID, int interiorID) -> bool` | Link a vehicle to an interior. |
| `Log(string text)` | Write a line to the server log. |
| `ManualVehicleEngineAndLights() -> bool` | Require manual engine/light control. |
| `MaxAttachedObjectSlots() -> int` | Return the number of attached-object slots a player has. |
| `MoveDynamicObject(int id, float x, float y, float z, float speed, float rx, float ry, float rz) -> bool` | Move a dynamic object over time. |
| `MoveObject(int id, float toX, float toY, float toZ, float speed, float toRX, float toRY, float toRZ) -> bool` | Move an object over time. |
| `MovePlayerObject(int playerID, int id, float toX, float toY, float toZ, float speed, float toRX, float toRY, float toRZ) -> bool` | Move a player object over time. |
| `MySQLFormat(int handle, string format, ...args) -> string` | Format a query string with %s/%d/%f placeholders (legacy alias). |
| `MySQLQueryAsync(int handle, string query, string callback, bool parallel) -> bool` | Run a query asynchronously against an open MySQL handle. |
| `NetStats_BytesReceived(int playerID) -> int` | Bytes received for a player. |
| `NetStats_BytesSent(int playerID) -> int` | Bytes sent for a player. |
| `NetStats_ConnectionStatus(int playerID) -> int` | Connection status for a player. |
| `NetStats_GetConnectedTime(int playerID) -> int` | Connected time in milliseconds. |
| `NetStats_GetIpPort(int playerID) -> string` | IP and port for a player. |
| `NetStats_MessagesReceived(int playerID) -> int` | Messages received for a player. |
| `NetStats_MessagesRecvPerSecond(int playerID) -> int` | Messages received per second. |
| `NetStats_MessagesSent(int playerID) -> int` | Messages sent for a player. |
| `NetStats_PacketLossPercent(int playerID) -> float` | Packet loss percentage. |
| `PauseRecordingPlayback() -> bool` | Recording playback is not supported; returns false. |
| `PlayAudioStreamForPlayer(int playerID, string url, float x, float y, float z, float distance, bool usePos) -> bool` | Play an audio stream URL. |
| `PlayCrimeReportForPlayer(int playerID, int suspectID, int inVehicle, int vehicleModel, int vehicleColour, int crime, float x, float y, float z) -> bool` | Play a crime report sound. |
| `PlayerCount() -> int` | Number of connected players. |
| `PlayerName(int playerID) -> string` | Get a player's name. |
| `PlayerPlaySound(int playerID, int soundID, float x, float y, float z) -> bool` | Play a sound for a player. |
| `PlayerSpectatePlayer(int playerID, int targetID, int mode) -> bool` | Make a player spectate another player. |
| `PlayerSpectateVehicle(int playerID, int vehicleID, int mode) -> bool` | Make a player spectate a vehicle. |
| `PlayerTextDrawAlignment()` | Set a player text draw alignment. |
| `PlayerTextDrawBackgroundColor()` | Set a player text draw background colour. |
| `PlayerTextDrawBoxColor()` | Set a player text draw box colour. |
| `PlayerTextDrawColor()` | Set a player text draw text colour. |
| `PlayerTextDrawCreate()` | Create a player text draw. |
| `PlayerTextDrawDestroy()` | Destroy a player text draw. |
| `PlayerTextDrawFont()` | Set a player text draw font. |
| `PlayerTextDrawHide(int playerID, int id) -> bool` | Hide a player text draw. |
| `PlayerTextDrawLetterSize()` | Set player text draw letter size. |
| `PlayerTextDrawSetOutline()` | Set player text draw outline. |
| `PlayerTextDrawSetPreviewModel()` | Set the model preview for a player text draw. |
| `PlayerTextDrawSetPreviewRot()` | Set the rotation of a model preview. |
| `PlayerTextDrawSetPreviewVehCol()` | Set preview vehicle colours. |
| `PlayerTextDrawSetProportional()` | Toggle proportional spacing. |
| `PlayerTextDrawSetSelectable()` | Make a player text draw selectable. |
| `PlayerTextDrawSetShadow()` | Set player text draw shadow. |
| `PlayerTextDrawSetString()` | Set player text draw string. |
| `PlayerTextDrawShow(int playerID, int id) -> bool` | Show a player text draw. |
| `PlayerTextDrawTextSize()` | Set player text draw text size. |
| `PlayerTextDrawUseBox()` | Toggle the player text draw box. |
| `PutPlayerInVehicle(int playerID, int vehicleID, int seatID) -> bool` | Put a player into a vehicle seat. |
| `RedirectDownload(int playerID, string url) -> bool` | Redirect a client download URL. |
| `RemoveBuildingForPlayer(int playerID, int modelID, float x, float y, float z, float radius) -> bool` | Remove a map building for a player. |
| `RemovePlayerAttachedObject(int playerID, int index) -> bool` | Remove an attached object from a player. |
| `RemovePlayerFromVehicle(int playerID) -> bool` | Remove a player from their vehicle. |
| `RemovePlayerMapIcon(int playerID, int iconID) -> bool` | Remove a radar map icon. |
| `RemoveVehicleComponent(int vehicleID, int componentID) -> bool` | Remove a vehicle component. |
| `RepairVehicle(int vehicleID) -> bool` | Repair a vehicle. |
| `ResetPlayerMoney(int playerID) -> bool` | Reset a player's money to zero. |
| `ResetPlayerWeapons(int playerID) -> bool` | Remove all of a player's weapons. |
| `ResumeRecordingPlayback() -> bool` | Recording playback is not supported; returns false. |
| `SHA256_PassHash(string password, string salt) -> string` | Hash a password with SHA-256 and salt. |
| `SelectObject(int playerID) -> bool` | Open object selection for a player. |
| `SelectTextDraw(int playerID, bool enable, int color) -> bool` | Enable text draw selection mode. |
| `SendChat(int playerid, string message) -> bool` | Send a chat line to the player. |
| `SendClientCheck(int playerID, int typ, int address, int offset, int count) -> bool` | Send an integrity check request to a client. |
| `SendClientMessage(int playerID, int color, string text) -> bool` | Send a chat message to a player. |
| `SendClientMessageToAll(int color, string text)` | Send a chat message to everyone. |
| `SendCommand(int playerid, string command) -> bool` | Run a /command as the player. Returns whether a handler handled it. |
| `SendDeathMessage(int killerID, int killeeID, int reason) -> bool` | Add a death to the kill feed. |
| `SendDeathMessageToPlayer(int playerID, int killerID, int killeeID, int reason) -> bool` | Add a death to one player's kill feed. |
| `SendPlayerMessageToAll(int senderID, string text)` | Send a message to everyone from a player. |
| `SendPlayerMessageToPlayer(int playerID, int senderID, string text) -> bool` | Send a message from one player to another. |
| `SendRconCommand(string command) -> bool` | Execute an RCON command. |
| `SetActorFacingAngle(int id, float angle) -> bool` | Set an actor's facing angle. |
| `SetActorHealth(int id, float health) -> bool` | Set an actor's health. |
| `SetActorInvulnerable(int actorID, bool invuln) -> bool` | Make an actor invulnerable. |
| `SetActorPos(int id, float x, float y, float z) -> bool` | Set an actor's position. |
| `SetActorVirtualWorld(int actorID, int world) -> bool` | Set an actor's virtual world. |
| `SetCameraBehindPlayer(int playerID) -> bool` | Restore the camera behind the player. |
| `SetDeathDropAmount(int amount) -> bool` | Set the money dropped on death. |
| `SetDynamicActorFacingAngle(int id, float angle) -> bool` | Set a dynamic actor's facing angle. |
| `SetDynamicActorPos(int id, float x, float y, float z) -> bool` | Set a dynamic actor's position. |
| `SetDynamicObjectMaterial(int id, int materialIndex, int modelID, string txdName, string textureName, int colour) -> bool` | Set a dynamic object material. |
| `SetDynamicObjectMaterialText(int id, int materialIndex, string text, int materialSize, string fontName, int fontSize, bool bold, int fontColour, int backgroundColour, int alignment) -> bool` | Set dynamic object material text. |
| `SetDynamicObjectPos(int id, float x, float y, float z) -> bool` | Set a dynamic object's position. |
| `SetDynamicObjectRot(int id, float rx, float ry, float rz) -> bool` | Set a dynamic object's rotation. |
| `SetGameModeText(string text) -> bool` | Set the gamemode text shown in the browser. |
| `SetGravity(float gravity) -> bool` | Set the world gravity. |
| `SetMenuColumnHeader(int menuid, int column, string header) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `SetMyFacingAngle(int playerid, float angle) -> bool` | Set the player's facing angle (degrees). |
| `SetMyPos(int playerid, float x, float y, float z) -> bool` | Teleport the player to x, y, z. |
| `SetNameTagDrawDistance(float distance) -> bool` | Set the name tag draw distance. |
| `SetObjectMaterial(int id, int materialIndex, int modelID, string txdName, string textureName, int colour) -> bool` | Set an object material. |
| `SetObjectMaterialText(int id, int materialIndex, string text, int materialSize, string fontName, int fontSize, bool bold, int fontColour, int backgroundColour, int alignment) -> bool` | Set object material text. |
| `SetObjectNoCameraCol(int id) -> bool` | Disable camera collision for an object. |
| `SetObjectPos(int id, float x, float y, float z) -> bool` | Set an object's position. |
| `SetObjectRot()` | Set an object's rotation. |
| `SetObjectRotation(int id, float rx, float ry, float rz) -> bool` | Set an object's rotation. |
| `SetObjectsDefaultCameraCol(bool enable) -> bool` | Toggle default camera collision for objects. |
| `SetPVarFloat(int playerID, string name, float val) -> bool` | Set a float player variable. |
| `SetPVarInt(int playerID, string name, int val) -> bool` | Set an integer player variable. |
| `SetPVarString(int playerID, string name, string val) -> bool` | Set a string player variable. |
| `SetPlayerAdmin(int playerID, bool admin) -> bool` | Grant or revoke admin rights. |
| `SetPlayerAmmo(int playerID, int weaponID, int ammo) -> bool` | Set ammo for a weapon. |
| `SetPlayerArmedWeapon(int playerID, int weaponID) -> bool` | Set the armed weapon. |
| `SetPlayerArmour(int playerID, float armour) -> bool` | Set a player's armour. |
| `SetPlayerAttachedObject(int playerID, int index, int modelID, int bone, float offsetX, float offsetY, float offsetZ, float rotX, float rotY, float rotZ, float scaleX, float scaleY, float scaleZ, int colour1, int colour2) -> bool` | Attach an object model to a player bone. |
| `SetPlayerCameraBehindPlayer(int playerID) -> bool` | Restore the camera behind the player. |
| `SetPlayerCameraLookAt(int playerID, float x, float y, float z, int cutType) -> bool` | Point the camera at a position. |
| `SetPlayerCameraPos(int playerID, float x, float y, float z) -> bool` | Set the camera position. |
| `SetPlayerChatBubble(int playerID, string text, int color, float drawDistance, int expireMS) -> bool` | Show a chat bubble above a player. |
| `SetPlayerCheckpoint(int playerID, float x, float y, float z, float radius) -> bool` | Create a checkpoint for a player. |
| `SetPlayerColor(int playerID, int colour) -> bool` | Set a player's name/chat colour. |
| `SetPlayerDrunkLevel(int playerID, int level) -> bool` | Set a player's drunk level. |
| `SetPlayerFacingAngle(int playerID, float angle) -> bool` | Set a player's facing angle. |
| `SetPlayerFightingStyle(int playerID, int style) -> bool` | Set a player's fighting style. |
| `SetPlayerHealth(int playerID, float health) -> bool` | Set a player's health. |
| `SetPlayerInterior(int playerID, int interior) -> bool` | Set a player's interior. |
| `SetPlayerMapIcon(int playerID, int iconID, float x, float y, float z, int markerType, int colour, int style) -> bool` | Add a radar map icon for a player. |
| `SetPlayerMarkerForPlayer(int viewerID, int targetID, int colour) -> bool` | Show or hide another player's marker. |
| `SetPlayerName(int playerID, string name) -> bool` | Set a player's name. |
| `SetPlayerObjectMaterial(int playerID, int objectID, int materialIndex, int modelID, string txdName, string textureName, int colour) -> bool` | Set a player object material. |
| `SetPlayerObjectMaterialText(int playerID, int objectID, int materialIndex, string text, int materialSize, string fontName, int fontSize, bool bold, int fontColour, int backgroundColour, int alignment) -> bool` | Set player object material text. |
| `SetPlayerObjectNoCameraCol(int playerID, int id) -> bool` | Disable camera collision for a player object. |
| `SetPlayerObjectPos(int playerID, int id, float x, float y, float z) -> bool` | Set a player object's position. |
| `SetPlayerObjectRot(int playerID, int id, float rx, float ry, float rz) -> bool` | Set a player object's rotation. |
| `SetPlayerPos(int playerID, float x, float y, float z) -> bool` | Teleport a player. |
| `SetPlayerPosFindZ(int playerID, float x, float y, float z) -> bool` | Teleport a player and snap to ground Z. |
| `SetPlayerRaceCheckpoint(int playerID, int cpType, float x, float y, float z, float nextX, float nextY, float nextZ, float radius) -> bool` | Create a race checkpoint for a player. |
| `SetPlayerScore(int playerID, int score) -> bool` | Set a player's score. |
| `SetPlayerShopName(int playerID, string name) -> bool` | Set the shop name for a player's interior. |
| `SetPlayerSkillLevel(int playerID, int skillType, int level) -> bool` | Set a player's weapon skill level. |
| `SetPlayerSkin(int playerID, int skin) -> bool` | Set a player's skin. |
| `SetPlayerSpecialAction(int playerID, int action) -> bool` | Set a player's special action. |
| `SetPlayerTeam(int playerID, int team) -> bool` | Set a player's team. |
| `SetPlayerTime(int playerID, int hour, int minute) -> bool` | Set a player's local time. |
| `SetPlayerVelocity(int playerID, float x, float y, float z) -> bool` | Set a player's velocity. |
| `SetPlayerVirtualWorld(int playerID, int world) -> bool` | Set a player's virtual world. |
| `SetPlayerWantedLevel(int playerID, int level) -> bool` | Set a player's wanted level. |
| `SetPlayerWeather(int playerID, int weather) -> bool` | Set a player's weather. |
| `SetPlayerWorldBounds(int playerID, float maxX, float minX, float maxY, float minY) -> bool` | Set a player's world boundaries. |
| `SetSVarFloat(string name, float val) -> bool` | Set a float server variable. |
| `SetSVarInt(string name, int val) -> bool` | Set an integer server variable. |
| `SetSVarString(string name, string val) -> bool` | Set a string server variable. |
| `SetSpawnInfo(int playerID, int team, int skin, float x, float y, float z, float angle) -> bool` | Set the spawn information for the next spawn. |
| `SetTeamCount(int count) -> bool` | Set the number of teams. |
| `SetTimer(string callback, int interval, bool repeat) -> int` | Schedule a named function after a delay. |
| `SetTimerEx(string callback, int interval, bool repeat, string format, ...args) -> int` | Schedule a named function with arguments. |
| `SetVehicleAngularVelocity(int vehicleID, float x, float y, float z) -> bool` | Set a vehicle's angular velocity. |
| `SetVehicleDamageStatus(int id, int panels, int doors, int lights, int tyres) -> bool` | Set vehicle panel/door/light/tyre damage. |
| `SetVehicleHealth(int id, float health) -> bool` | Set a vehicle's health. |
| `SetVehicleNumberPlate(int vehicleID, string plate) -> bool` | Set a vehicle's number plate. |
| `SetVehicleParamsCarDoors(int vehicleID, int driver, int passenger, int backLeft, int backRight) -> bool` | Set vehicle door open states. |
| `SetVehicleParamsCarWindows(int vehicleID, int driver, int passenger, int backLeft, int backRight) -> bool` | Set vehicle window open states. |
| `SetVehicleParamsEx(int vehicleID, int engine, int lights, int alarm, int doors, int bonnet, int boot, int objective) -> bool` | Set vehicle params (engine, lights, ...). |
| `SetVehicleParamsForPlayer(int vehicleID, int playerID, int objective, int doorsLocked) -> bool` | Set vehicle params for one player. |
| `SetVehiclePos(int vehicleID, float x, float y, float z) -> bool` | Teleport a vehicle. |
| `SetVehicleToRespawn(int vehicleID) -> bool` | Respawn a vehicle. |
| `SetVehicleVelocity(int vehicleID, float x, float y, float z) -> bool` | Set a vehicle's velocity. |
| `SetVehicleVirtualWorld(int vehicleID, int world) -> bool` | Set a vehicle's virtual world. |
| `SetVehicleZAngle(int vehicleID, float angle) -> bool` | Set a vehicle's Z angle. |
| `SetWeather(int weather) -> bool` | Set the global weather. |
| `SetWorldTime(int hour) -> bool` | Set the global world time. |
| `ShowMenuForPlayer(int menuid, int playerid) -> bool` | Menu emulation: always returns false. Use dialogs for real UI. |
| `ShowNameTags(bool show) -> bool` | Toggle name tags globally. |
| `ShowPlayerDialog(int playerID, int dialogID, int style, string title, string body, string button1, string button2) -> bool` | Show a dialog to a player. |
| `ShowPlayerMarkers(int mode) -> bool` | Toggle player markers. |
| `ShowPlayerNameTagForPlayer(int viewerID, int targetID, bool show) -> bool` | Show or hide a name tag for one player. |
| `SpawnPlayer(int playerID) -> bool` | Spawn a player immediately. |
| `StartRecordingPlayback(int playbacktype, string recordname) -> bool` | Recording playback is not supported; returns false. |
| `StartRecordingPlayerData(int playerID, int recordType, string recordName) -> bool` | Start recording player data. |
| `StopAudioStreamForPlayer(int playerID) -> bool` | Stop a player's audio stream. |
| `StopDynamicObject(int id) -> bool` | Stop a dynamic object's move. |
| `StopObject(int id) -> bool` | Stop an object's move. |
| `StopPlayerObject(int playerID, int id) -> bool` | Stop a player object's move. |
| `StopRecordingPlayback() -> bool` | Recording playback is not supported; returns false. |
| `StopRecordingPlayerData(int playerID) -> bool` | Stop recording player data. |
| `Streamer_CountItems(int type, int playerid) -> int` | Count streamer items of a type. |
| `Streamer_DestroyAllVisibleItems(int playerid, int type, bool serverwide) -> int` | Destroy all visible streamer items. |
| `Streamer_GetArrayData(int type, int id, int data) -> int` | Read streamer array data. |
| `Streamer_MaxItems(int type, int items)` | Set the maximum streamed items. |
| `Streamer_SetArrayData(int type, int id, int data, int value, ...extra)` | Write streamer array data. |
| `Streamer_SetIntData(int type, int id, int data, int value)` | Set streamer integer data. |
| `Streamer_SetRadiusMultiplier(int type, float multiplier)` | Set the streamer radius multiplier. |
| `Streamer_SetVisibleItems(int type, int items)` | Set the visible item count. |
| `Streamer_ToggleIdleUpdate(int playerid, bool enable) -> bool` | Toggle idle streamer updates. |
| `Streamer_Update(int playerid, int type)` | Update the streamer for a player. |
| `Streamer_UpdateEx(int playerid, float x, float y, float z, int virtualworld, int interior)` | Update the streamer at a position. |
| `TextDrawAlignment(int player, int id, int alignment) -> bool` | Set text draw alignment. |
| `TextDrawBackgroundColor(int player, int id, int color) -> bool` | Set text draw background colour. |
| `TextDrawBoxColor(int player, int id, int color) -> bool` | Set text draw box colour. |
| `TextDrawColor(int player, int id, int color) -> bool` | Set text draw text colour. |
| `TextDrawCreate(int player, int id, float x, float y, string text) -> bool` | Create a global text draw. |
| `TextDrawDestroy(int player, int id) -> bool` | Destroy a global text draw. |
| `TextDrawFont(int player, int id, int font) -> bool` | Set text draw font. |
| `TextDrawHideForAll(int id) -> bool` | Hide a text draw from everyone. |
| `TextDrawHideForPlayer(int playerID, int id) -> bool` | Hide a text draw from a player. |
| `TextDrawLetterSize(int player, int id, float x, float y) -> bool` | Set text draw letter size. |
| `TextDrawSetOutline(int player, int id, int size) -> bool` | Set text draw outline. |
| `TextDrawSetPreviewModel(int player, int id, int model) -> bool` | Set a model preview for a text draw. |
| `TextDrawSetPreviewRot(int player, int id, float rx, float ry, float rz, float zoom) -> bool` | Set the rotation of a model preview. |
| `TextDrawSetPreviewVehCol(int player, int id, int color1, int color2) -> bool` | Set preview vehicle colours. |
| `TextDrawSetProportional(int player, int id, bool proportional) -> bool` | Toggle proportional spacing. |
| `TextDrawSetSelectable(int player, int id, bool selectable) -> bool` | Make a text draw selectable. |
| `TextDrawSetShadow(int player, int id, int size) -> bool` | Set text draw shadow. |
| `TextDrawSetString(int player, int id, string text) -> bool` | Set text draw string. |
| `TextDrawShowForAll(int id) -> bool` | Show a text draw to everyone. |
| `TextDrawShowForPlayer(int playerID, int id) -> bool` | Show a text draw to a player. |
| `TextDrawTextSize(int player, int id, float x, float y) -> bool` | Set text draw text size. |
| `TextDrawUseBox(int player, int id, bool use) -> bool` | Toggle the text draw box. |
| `TogglePlayerClock(int playerID, bool toggle) -> bool` | Toggle the in-game clock. |
| `TogglePlayerControllable(int playerID, bool controllable) -> bool` | Enable or disable player control. |
| `TogglePlayerSpectating(int playerID, bool toggle) -> bool` | Toggle spectate mode. |
| `TogglePlayerWidescreen(int playerID, bool enable) -> bool` | Toggle widescreen mode. |
| `UnBlockIpAddress(string ip) -> bool` | Unblock a previously blocked IP. |
| `Update3DTextLabelText(int id, int colour, string text) -> bool` | Update a 3D text label's text. |
| `UpdateDynamic3DTextLabelText(int id, int colour, string text) -> bool` | Update a dynamic 3D label's text. |
| `UpdatePlayer3DTextLabelText(int playerID, int id, int colour, string text) -> bool` | Update a player 3D label's text. |
| `UpdateVehicleDamageStatus(int vehicleID, int panels, int doors, int lights, int tyres) -> bool` | Update vehicle damage status. |
| `UsePlayerPedAnims() -> bool` | Use the player ped animation set. |
| `VectorSize(float x, float y, float z) -> float` | Length of a vector (x, y, z). |
| `acos(float value) -> float` | Arc cosine of a value. Returns radians. |
| `asin(float value) -> float` | Arc sine of a value. Returns radians. |
| `atan(float value) -> float` | Arc tangent of a value. Returns radians. |
| `atan2(float y, float x) -> float` | Arc tangent of y/x using both signs to pick the quadrant. Returns radians. |
| `cache_delete(int result) -> bool` | Delete a cached result set. |
| `cache_get_field_count(int result) -> int` | Number of fields in a cached result. |
| `cache_get_row_count(int result) -> int` | Number of rows in a cached result. |
| `cache_get_value_index_int(int result, int row, int column) -> int` | Read an integer field by row/column index. |
| `cache_get_value_name(int result, int row, string field) -> string` | Read a field value by column name. |
| `cache_get_value_name_float(int result, int row, string field) -> float` | Read a float field by column name. |
| `cache_get_value_name_int(int result, int row, string field) -> int` | Read an integer field by column name. |
| `cache_insert_id(int result) -> int` | Last inserted row id. |
| `floatabs(float value) -> float` | Absolute value of a float. |
| `floatcmp(float value1, float value2) -> int` | Compare two floats: -1, 0 or 1. |
| `floatcos(float angle) -> float` | Cosine of an angle in degrees. |
| `floatfract(float value) -> float` | Fractional part of a float. |
| `floatlog(float value, float base) -> float` | Natural logarithm, or logarithm in the given base. |
| `floatpower(float value, float exponent) -> float` | Raise a float to a power. |
| `floatround(float value, int method) -> int` | Round a float using a mode: 0 nearest, 1 floor, 2 ceil, 3 toward zero. |
| `floatsin(float angle) -> float` | Sine of an angle in degrees. |
| `floatsqroot(float value) -> float` | Square root of a float (0 for negative input). |
| `floattan(float angle) -> float` | Tangent of an angle in degrees. |
| `format(string format, ...args) -> string` | Format a string with placeholders. |
| `gpci(int playerid) -> string` | Get the player's client serial (GPCI). |
| `hash_password(string password) -> string` | Hash a password with bcrypt. |
| `mysql_close(int handle) -> bool` | Close a MySQL connection. |
| `mysql_errno(int handle) -> int` | Last MySQL error number. |
| `mysql_format(int handle, string format, ...args) -> string` | Format a MySQL query string. |
| `mysql_open(string dsn) -> int` | Open a MySQL connection. |
| `mysql_pquery(int handle, string query, string callback) -> bool` | Run a parallel MySQL query. |
| `mysql_tquery(int handle, string query, string callback) -> bool` | Run a threaded MySQL query. |
| `print(string text)` | Write a line to the server log. Alias for Log. |
| `printf(string format, ...args)` | Write a formatted line to the server log (%s, %d, %f, %v). |
| `random_token(int length) -> string` | Generate a random token string. |
| `sqlite_close(int handle) -> bool` | Close a SQLite connection. |
| `sqlite_exec(int handle, string query, ...params) -> string` | Run a SQLite statement (returns error or null). |
| `sqlite_exec_async(int handle, string callback, string query, ...params) -> bool` | Run a SQLite statement asynchronously. |
| `sqlite_open(string path) -> int` | Open a SQLite connection (returns handle or null). |
| `sqlite_query(int handle, string query, ...params) -> int` | Run a SQLite query (returns result index or null). |
| `sqlite_query_async(int handle, string callback, string query, ...params) -> bool` | Run a SQLite query asynchronously. |
| `sscanf(string input, string format) -> int` | Parse a string by format. |
| `strcat(string dest, string src) -> string` | Concatenate strings into a destination. |
| `strcmp(string a, string b) -> int` | Compare two strings. |
| `strdel(string s, int start, int end) -> string` | Delete part of a string. |
| `strfind(string s, string sub) -> int` | Find a substring. |
| `strins(string s, string insert, int pos) -> string` | Insert a string at an offset. |
| `strlen(string s) -> int` | String length. |
| `strmid(string s, int start, int end) -> string` | Extract a substring. |
| `strpack(string s) -> string` | Pack a string into a destination. |
| `strunpack(string s) -> string` | Unpack a string. |
| `strval(string s) -> int` | Parse a string to an integer. |
| `verify_password(string password, string hash) -> bool` | Verify a password against a bcrypt hash. |
