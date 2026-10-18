# Knight — Native & Object Reference

Engine functions are called as `sa.<Native>(...)`. All 498 natives are
available from any handler. The tables below also document the typed object
surface (fields and methods) and namespace helpers.

## `Broadcast`

### Methods

| Method | Returns | Description |
|---|---|---|
| `log(string)` | `—` | Write a line to the server log. |
| `message(string)` | `—` | Send a chat message to the player (optional colour). |

## `Object`

**Factory:** `Object.create(int, float, float, float, float, float, float, float) -> Object`

### Fields

| Field | Type | Access | Description |
|---|---|---|---|
| `id` | `int` | read | Numeric handle id of the entity. |
| `model` | `int` | read | Model id (read-only for vehicles/objects). |
| `x` | `float` | read | World X coordinate. |
| `y` | `float` | read | World Y coordinate. |
| `z` | `float` | read | World Z coordinate. |

### Methods

| Method | Returns | Description |
|---|---|---|
| `destroy()` | `—` | Destroy the entity. |
| `move(float, float, float, float, float, float, float)` | `—` | Move the object to a position over time. |
| `set_material(int, int, string, string, int)` | `—` | Set an object material (index, model, txd, texture, colour). |
| `set_position(float, float, float)` | `—` | Teleport to the given coordinates. |
| `set_rotation(float, float, float)` | `—` | Set rotation (rx, ry, rz). |
| `stop()` | `—` | Stop an in-progress object move. |

## `Player`

### Fields

| Field | Type | Access | Description |
|---|---|---|---|
| `armor` | `float` | read/write | Armour value. |
| `armour` | `float` | read/write | Armour value. |
| `color` | `int` | read/write | Chat/name colour (RGBA). |
| `colour` | `int` | read/write | Chat/name colour (RGBA). |
| `connected` | `bool` | read | Whether the player is connected (read-only). |
| `facing_angle` | `float` | read/write | Facing angle in degrees. |
| `health` | `float` | read/write | Health value. |
| `id` | `int` | read | Numeric handle id of the entity. |
| `interior` | `int` | read/write | Interior id. |
| `ip` | `string` | read | Player IP address (read-only). |
| `money` | `int` | read/write | Player money (writes apply the delta). |
| `name` | `string` | read/write | Player name (read/write). |
| `ping` | `int` | read | Player ping in milliseconds (read-only). |
| `score` | `int` | read/write | Player score. |
| `skin` | `int` | read/write | Skin model id. |
| `team` | `int` | read/write | Team id. |
| `vehicle` | `int` | read | Vehicle id the player is in (read-only). |
| `virtual_world` | `int` | read/write | Virtual world id. |
| `weapon` | `int` | read/write | Armed weapon id. |
| `x` | `float` | read | World X coordinate. |
| `y` | `float` | read | World Y coordinate. |
| `z` | `float` | read | World Z coordinate. |

### Methods

| Method | Returns | Description |
|---|---|---|
| `apply_animation(string, string, float, bool, bool, bool, bool, int)` | `—` | Play a library/name animation. |
| `apply_animation2(string, string, float, bool, bool, bool, bool, int)` | `—` | Play a library/name animation. |
| `ban()` | `—` | Ban the player. |
| `ban_with_reason(string)` | `—` | Ban the player with a reason. |
| `clear_animations()` | `—` | Stop the current animation. |
| `disable_checkpoint()` | `—` | Remove the active checkpoint. |
| `distance_to(Player)` | `float` | Distance from this player to another. |
| `force_class_selection()` | `—` | Force the class-selection screen. |
| `get_position()` | `array` | Return position as an array [x, y, z]. |
| `give_weapon(int, int)` | `—` | Give a weapon with ammo. |
| `hide_textdraw(TextDraw)` | `—` | Hide a text draw from this player. |
| `is_admin()` | `bool` | Return whether the player is an admin. |
| `kick()` | `—` | Kick the player. |
| `kick_with_reason(string)` | `—` | Kick the player with a reason. |
| `message(string, int)` | `—` | Send a chat message to the player (optional colour). |
| `reset_money()` | `—` | Reset money to zero. |
| `reset_weapons()` | `—` | Remove all weapons. |
| `send_message(string)` | `—` | Send a chat message to the player. |
| `send_score(int)` | `—` | Set the score. |
| `set_admin(bool)` | `—` | Grant or revoke admin rights. |
| `set_armor(float)` | `—` | Set armour. |
| `set_armour(float)` | `—` | Set armour. |
| `set_camera_behind()` | `—` | Restore the camera behind the player. |
| `set_camera_look_at(float, float, float, int)` | `—` | Point the camera at a position. |
| `set_camera_pos(float, float, float)` | `—` | Set the camera position. |
| `set_checkpoint(float, float, float, float)` | `—` | Create a checkpoint at x,y,z with radius. |
| `set_color(int)` | `—` | Set the name/chat colour (RGBA). |
| `set_health(float)` | `—` | Set health. |
| `set_interior(int)` | `—` | Set the interior id. |
| `set_map_icon(int, float, float, float, int, int, int)` | `—` | Add a radar map icon. |
| `set_money(int)` | `—` | Give money (may be negative). |
| `set_position(float, float, float)` | `—` | Teleport to the given coordinates. |
| `set_skin(int)` | `—` | Set the skin model. |
| `set_special_action(int)` | `—` | Set the special action (dance, hands up, ...). |
| `set_team(int)` | `—` | Set the team id. |
| `set_virtual_world(int)` | `—` | Set the virtual world id. |
| `show_dialog(int, int, string, string, string, string)` | `—` | Show a dialog to the player. |
| `show_textdraw(TextDraw)` | `—` | Show a text draw to this player. |

## `TextDraw`

**Factory:** `TextDraw.create(int, int, string) -> TextDraw`

### Fields

| Field | Type | Access | Description |
|---|---|---|---|
| `id` | `int` | read | Numeric handle id of the entity. |

### Methods

| Method | Returns | Description |
|---|---|---|
| `destroy()` | `—` | Destroy the entity. |
| `set_string(string)` | `—` | Set the text draw string. |
| `show()` | `—` | Show the text draw. |

## `Vehicle`

**Factory:** `Vehicle.create(int, float, float, float, float, int, int) -> Vehicle`

### Fields

| Field | Type | Access | Description |
|---|---|---|---|
| `angle` | `float` | read/write | Z angle in degrees. |
| `health` | `float` | read/write | Health value. |
| `id` | `int` | read | Numeric handle id of the entity. |
| `model` | `int` | read | Model id (read-only for vehicles/objects). |
| `x` | `float` | read | World X coordinate. |
| `y` | `float` | read | World Y coordinate. |
| `z` | `float` | read | World Z coordinate. |

### Methods

| Method | Returns | Description |
|---|---|---|
| `destroy()` | `—` | Destroy the entity. |
| `repair()` | `—` | Repair the vehicle to full health. |
| `set_color(int, int)` | `—` | Set the name/chat colour (RGBA). |
| `set_health(float)` | `—` | Set health. |
| `set_number_plate(string)` | `—` | Set the number plate text. |
| `set_position(float, float, float)` | `—` | Teleport to the given coordinates. |

## `server` (runtime methods)

| Method | Returns | Description |
|---|---|---|
| `server.disable_interior_enter_exits()` | `—` | Calls `sa.DisableInteriorEnterExits`. |
| `server.game_mode_exit()` | `—` | Calls `sa.GameModeExit`. |
| `server.get_gravity()` | `float` | Calls `sa.GetGravity`. |
| `server.get_max_players()` | `int` | Calls `sa.GetMaxPlayers`. |
| `server.get_player_count()` | `int` | Calls `sa.PlayerCount`. |
| `server.log(string)` | `—` | Calls `sa.Log`. |
| `server.send_rcon(string)` | `—` | Calls `sa.SendRconCommand`. |
| `server.set_gamemode_text(string)` | `—` | Calls `sa.SetGameModeText`. |
| `server.set_gravity(float)` | `—` | Calls `sa.SetGravity`. |
| `server.set_team_count(int)` | `—` | Calls `sa.SetTeamCount`. |
| `server.set_weather(int)` | `—` | Calls `sa.SetWeather`. |
| `server.set_world_time(int)` | `—` | Calls `sa.SetWorldTime`. |
| `server.show_name_tags(bool)` | `—` | Calls `sa.ShowNameTags`. |
| `server.show_player_markers(int)` | `—` | Calls `sa.ShowPlayerMarkers`. |

## Namespace helpers

| Call | Maps to |
|---|---|
| `player.add_class(int, float, float, float, float, int, int, int, int, int, int)` | `sa.AddPlayerClass` |
| `player.add_class_ex(int, int, float, float, float, float, int, int, int, int, int, int)` | `sa.AddPlayerClassEx` |
| `server.set_gamemode_text(string)` | `sa.SetGameModeText` |
| `server.set_weather(int)` | `sa.SetWeather` |
| `server.set_world_time(int)` | `sa.SetWorldTime` |

## Native index

498 natives, grouped under `sa.*`.

| Native | Description |
|---|---|
| `sa.AddCharModel` | Register a custom character model (skin). |
| `sa.AddPlayerClass` | Add a spawn class (skin, position, angle, optional weapons). |
| `sa.AddPlayerClassEx` | Add a spawn class for a specific team. |
| `sa.AddSimpleModel` | Register an object model for custom objects. |
| `sa.AddSimpleModelTimed` | Register a time-limited custom object model. |
| `sa.AddStaticPickup` | Create a static pickup (engine-managed). |
| `sa.AddStaticVehicle` | Create a static vehicle (engine-managed). |
| `sa.AddStaticVehicleEx` | Create a static vehicle with respawn delay. |
| `sa.AddVehicleComponent` | Attach a visual component to a vehicle. |
| `sa.AllowAdminTeleport` | Allow admins to teleport with the map. |
| `sa.AllowInteriorWeapons` | Allow weapons inside interiors. |
| `sa.AllowPlayerTeleport` | Allow the player to teleport via the map. |
| `sa.ApplyActorAnimation` | Play an animation on an actor. |
| `sa.ApplyAnimation` | Play a library/name animation on a player. |
| `sa.ApplyDynamicActorAnimation` | Play an animation on a dynamic actor. |
| `sa.ApplyPlayerAnimation` | Play an animation on a player. |
| `sa.Attach3DTextLabelToPlayer` | Attach a 3D text label to a player. |
| `sa.Attach3DTextLabelToVehicle` | Attach a 3D text label to a vehicle. |
| `sa.AttachCameraToObject` | Attach the player camera to an object. |
| `sa.AttachCameraToPlayerObject` | Attach the camera to a player object. |
| `sa.AttachDynamicObjectToPlayer` | Attach a dynamic object to a player. |
| `sa.AttachDynamicObjectToVehicle` | Attach a dynamic object to a vehicle. |
| `sa.AttachObjectToObject` | Attach an object to another object. |
| `sa.AttachObjectToPlayer` | Attach an object to a player bone. |
| `sa.AttachObjectToVehicle` | Attach an object to a vehicle. |
| `sa.AttachPlayerObjectToPlayer` | Attach a player object to a player. |
| `sa.AttachPlayerObjectToVehicle` | Attach a player object to a vehicle. |
| `sa.AttachTrailerToVehicle` | Attach a trailer to a vehicle. |
| `sa.Ban` | Ban a player by id. |
| `sa.BanEx` | Ban a player with a reason. |
| `sa.BanPlayer` | Ban a player with an optional reason. |
| `sa.BlockIpAddress` | Block an IP address for a duration. |
| `sa.CallLocalFunction` | Call a gamemode function by name. |
| `sa.CallRemoteFunction` | Call a function in another script. |
| `sa.CancelEdit` | Cancel object editing for a player. |
| `sa.CancelSelectTextDraw` | Cancel text draw selection mode. |
| `sa.ChangeVehicleColor` | Change a vehicle's colours. |
| `sa.ChangeVehiclePaintjob` | Change a vehicle's paintjob. |
| `sa.ClearActorAnimation` | Stop an actor's animation. |
| `sa.ClearActorAnimations` | Stop all animations on an actor. |
| `sa.ClearAnimations` | Stop a player's animation. |
| `sa.ClearDynamicActorAnimations` | Stop all animations on a dynamic actor. |
| `sa.ClearPlayerAnimation` | Stop a player's animation. |
| `sa.ConnectNPC` | Connect an NPC into the world. |
| `sa.Create3DTextLabel` | Create a 3D text label in the world. |
| `sa.Create3DTextLabelAttachedToPlayer` | Create a 3D label attached to a player. |
| `sa.Create3DTextLabelAttachedToVehicle` | Create a 3D label attached to a vehicle. |
| `sa.CreateActor` | Create a static actor. |
| `sa.CreateDynamic3DTextLabel` | Create a streamed 3D text label. |
| `sa.CreateDynamicActor` | Create a streamed dynamic actor. |
| `sa.CreateDynamicCP` | Create a streamed checkpoint. |
| `sa.CreateDynamicCircle` | Create a streamed circular area. |
| `sa.CreateDynamicMapIcon` | Create a streamed radar map icon. |
| `sa.CreateDynamicObject` | Create a streamed object. |
| `sa.CreateDynamicPickup` | Create a streamed pickup. |
| `sa.CreateDynamicRaceCP` | Create a streamed race checkpoint. |
| `sa.CreateDynamicRectangle` | Create a streamed rectangular area. |
| `sa.CreateExplosion` | Create an explosion in the world. |
| `sa.CreateExplosionForPlayer` | Create an explosion visible to one player. |
| `sa.CreateObject` | Create a global object. |
| `sa.CreatePickup` | Create a pickup. |
| `sa.CreatePlayer3DTextLabel` | Create a player-local 3D text label. |
| `sa.CreatePlayerObject` | Create a player-local object. |
| `sa.CreateVehicle` | Create a vehicle; returns its id. |
| `sa.Delete3DTextLabel` | Delete a 3D text label. |
| `sa.DeletePVar` | Delete a player variable. |
| `sa.DeletePlayer3DTextLabel` | Delete a player 3D text label. |
| `sa.DeleteSVar` | Delete a server variable. |
| `sa.DestroyActor` | Destroy a static actor. |
| `sa.DestroyDynamic3DTextLabel` | Destroy a streamed 3D text label. |
| `sa.DestroyDynamicActor` | Destroy a dynamic actor. |
| `sa.DestroyDynamicArea` | Destroy a dynamic area. |
| `sa.DestroyDynamicCP` | Destroy a streamed checkpoint. |
| `sa.DestroyDynamicMapIcon` | Destroy a streamed map icon. |
| `sa.DestroyDynamicObject` | Destroy a streamed object. |
| `sa.DestroyDynamicPickup` | Destroy a streamed pickup. |
| `sa.DestroyDynamicRaceCP` | Destroy a streamed race checkpoint. |
| `sa.DestroyObject` | Destroy a global object. |
| `sa.DestroyPickup` | Destroy a pickup. |
| `sa.DestroyPlayerObject` | Destroy a player object. |
| `sa.DestroyVehicle` | Destroy a vehicle. |
| `sa.DetachTrailerFromVehicle` | Detach a trailer from a vehicle. |
| `sa.DisableInteriorEnterExits` | Remove interior entrance markers from the map. |
| `sa.DisableNameTagLOS` | Remove line-of-sight checks for name tags. |
| `sa.DisablePlayerCheckpoint` | Remove the player's checkpoint. |
| `sa.DisablePlayerRaceCheckpoint` | Remove the player's race checkpoint. |
| `sa.DisableRemoteVehicleCollisions` | Disable collisions with remote vehicles. |
| `sa.EditAttachedObject` | Open the attached-object editor. |
| `sa.EditDynamicObject` | Open the object editor for a dynamic object. |
| `sa.EditObject` | Open the object editor. |
| `sa.EditPlayerObject` | Open the editor for a player object. |
| `sa.EnablePlayerCameraTarget` | Enable camera target queries for a player. |
| `sa.EnableStuntBonusForAll` | Enable stunt bonuses for everyone. |
| `sa.EnableStuntBonusForPlayer` | Enable stunt bonuses for a player. |
| `sa.EnableTirePopping` | Enable tyre popping. |
| `sa.EnableVehicleFriendlyFire` | Allow players in the same team to damage vehicles. |
| `sa.EnableZoneNames` | Show zone names above the radar. |
| `sa.FindModelFileNameFromCRC` | Resolve a model file name from its CRC. |
| `sa.FindTextureFileNameFromCRC` | Resolve a texture file name from its CRC. |
| `sa.ForceClassSelection` | Force the class-selection screen. |
| `sa.GameModeExit` | Shut the server down cleanly. |
| `sa.GameTextForAll` | Show game text to all players. |
| `sa.GameTextForPlayer` | Show game text to one player. |
| `sa.GangZoneCreate` | Create a gang zone rectangle. |
| `sa.GangZoneDestroy` | Destroy a gang zone. |
| `sa.GangZoneFlashForAll` | Flash a gang zone for all players. |
| `sa.GangZoneFlashForPlayer` | Flash a gang zone for one player. |
| `sa.GangZoneHideForAll` | Hide a gang zone from all players. |
| `sa.GangZoneHideForPlayer` | Hide a gang zone from one player. |
| `sa.GangZoneShowForAll` | Show a gang zone to all players. |
| `sa.GangZoneShowForPlayer` | Show a gang zone to one player. |
| `sa.GangZoneStopFlashForAll` | Stop flashing a gang zone for all players. |
| `sa.GangZoneStopFlashForPlayer` | Stop flashing a gang zone for one player. |
| `sa.GetActorFacingAngle` | Get an actor's facing angle. |
| `sa.GetActorHealth` | Get an actor's health. |
| `sa.GetActorPoolSize` | Highest allocated actor id. |
| `sa.GetActorPos` | Get an actor's position. |
| `sa.GetActorVirtualWorld` | Get an actor's virtual world. |
| `sa.GetAnimationName` | Resolve an animation index to library/name. |
| `sa.GetConsoleVarAsBool` | Read a boolean console variable. |
| `sa.GetConsoleVarAsInt` | Read an integer console variable. |
| `sa.GetConsoleVarAsString` | Read a string console variable. |
| `sa.GetDistanceBetweenPlayers` | Distance between two players. |
| `sa.GetDynamicObjectPos` | Get a dynamic object's position. |
| `sa.GetDynamicObjectRot` | Get a dynamic object's rotation. |
| `sa.GetGravity` | Get the world gravity. |
| `sa.GetMaxPlayers` | Get the configured player slot count. |
| `sa.GetNetworkStats` | Get network statistics for a player. |
| `sa.GetObjectModel` | Get an object's model id. |
| `sa.GetObjectPos` | Get an object's position. |
| `sa.GetObjectRot` | Get an object's rotation. |
| `sa.GetPVarFloat` | Read a float player variable. |
| `sa.GetPVarInt` | Read an integer player variable. |
| `sa.GetPVarNameAtIndex` | Get a player variable name at an index. |
| `sa.GetPVarString` | Read a string player variable. |
| `sa.GetPVarType` | Get a player variable's type. |
| `sa.GetPVarsUpperIndex` | Highest player variable index. |
| `sa.GetPlayerAmmo` | Get a player's ammo. |
| `sa.GetPlayerAnimationIndex` | Get the current animation index. |
| `sa.GetPlayerArmour` | Get a player's armour. |
| `sa.GetPlayerCameraAspectRatio` | Get the camera aspect ratio. |
| `sa.GetPlayerCameraFrontVector` | Get the camera forward vector. |
| `sa.GetPlayerCameraMode` | Get the camera mode. |
| `sa.GetPlayerCameraPos` | Get the camera position. |
| `sa.GetPlayerCameraTargetActor` | Get the actor the camera targets. |
| `sa.GetPlayerCameraTargetObject` | Get the object the camera targets. |
| `sa.GetPlayerCameraTargetPlayer` | Get the player the camera targets. |
| `sa.GetPlayerCameraTargetVehicle` | Get the vehicle the camera targets. |
| `sa.GetPlayerCameraZoom` | Get the camera zoom. |
| `sa.GetPlayerColor` | Get a player's colour. |
| `sa.GetPlayerCustomSkin` | Get a player's custom skin id. |
| `sa.GetPlayerDistanceFromPoint` | Distance from a player to a point. |
| `sa.GetPlayerDrunkLevel` | Get a player's drunk level. |
| `sa.GetPlayerFacingAngle` | Get a player's facing angle. |
| `sa.GetPlayerFightingStyle` | Get a player's fighting style. |
| `sa.GetPlayerHealth` | Get a player's health. |
| `sa.GetPlayerInterior` | Get a player's interior. |
| `sa.GetPlayerIp` | Get a player's IP address. |
| `sa.GetPlayerKeys` | Get a player's keys, up/down and left/right state. |
| `sa.GetPlayerLastShotVectors` | Get the last shot origin and hit vectors. |
| `sa.GetPlayerMoney` | Get a player's money. |
| `sa.GetPlayerNetworkStats` | Get a player's network statistics. |
| `sa.GetPlayerObjectModel` | Get a player object's model. |
| `sa.GetPlayerObjectPos` | Get a player object's position. |
| `sa.GetPlayerObjectRot` | Get a player object's rotation. |
| `sa.GetPlayerPing` | Get a player's ping. |
| `sa.GetPlayerPoolSize` | Highest allocated player id. |
| `sa.GetPlayerPos` | Get a player's position. |
| `sa.GetPlayerScore` | Get a player's score. |
| `sa.GetPlayerSkin` | Get a player's skin. |
| `sa.GetPlayerSpecialAction` | Get a player's special action. |
| `sa.GetPlayerState` | Get a player's state. |
| `sa.GetPlayerSurfingObjectID` | Get the object the player is surfing. |
| `sa.GetPlayerSurfingVehicleID` | Get the vehicle the player is surfing. |
| `sa.GetPlayerTargetActor` | Get the actor a player is targeting. |
| `sa.GetPlayerTargetPlayer` | Get the player a player is targeting. |
| `sa.GetPlayerTeam` | Get a player's team. |
| `sa.GetPlayerTime` | Get a player's local time. |
| `sa.GetPlayerVehicleID` | Get the vehicle id a player is in. |
| `sa.GetPlayerVehicleSeat` | Get the seat a player occupies. |
| `sa.GetPlayerVelocity` | Get a player's velocity. |
| `sa.GetPlayerVersion` | Get a player's client version string. |
| `sa.GetPlayerVirtualWorld` | Get a player's virtual world. |
| `sa.GetPlayerWantedLevel` | Get a player's wanted level. |
| `sa.GetPlayerWeapon` | Get a player's current weapon. |
| `sa.GetPlayerWeaponData` | Get weapon/ammo for a weapon slot. |
| `sa.GetPlayerWeaponState` | Get the weapon state. |
| `sa.GetSVarFloat` | Read a float server variable. |
| `sa.GetSVarInt` | Read an integer server variable. |
| `sa.GetSVarNameAtIndex` | Get a server variable name at an index. |
| `sa.GetSVarString` | Read a string server variable. |
| `sa.GetSVarType` | Get a server variable's type. |
| `sa.GetSVarsUpperIndex` | Highest server variable index. |
| `sa.GetServerTickRate` | Get the server tick rate. |
| `sa.GetServerVarAsBool` | Read a boolean server variable. |
| `sa.GetServerVarAsInt` | Read an integer server variable. |
| `sa.GetServerVarAsString` | Read a string server variable. |
| `sa.GetTickCount` | Milliseconds since server start. |
| `sa.GetVehicleComponentInSlot` | Get the component in a vehicle slot. |
| `sa.GetVehicleComponentType` | Get a component's type. |
| `sa.GetVehicleDamageStatus` | Get vehicle panel/door/light/tyre damage. |
| `sa.GetVehicleDistanceFromPoint` | Distance from a vehicle to a point. |
| `sa.GetVehicleHealth` | Get a vehicle's health. |
| `sa.GetVehicleModel` | Get a vehicle's model id. |
| `sa.GetVehicleModelInfo` | Get model info (size, seats, ...). |
| `sa.GetVehicleParamsCarDoors` | Get vehicle door open states. |
| `sa.GetVehicleParamsCarWindows` | Get vehicle window open states. |
| `sa.GetVehicleParamsEx` | Get vehicle params (engine, lights, ...). |
| `sa.GetVehicleParamsSirenState` | Get the siren state. |
| `sa.GetVehiclePoolSize` | Highest allocated vehicle id. |
| `sa.GetVehiclePos` | Get a vehicle's position. |
| `sa.GetVehicleRotationQuat` | Get a vehicle's rotation quaternion. |
| `sa.GetVehicleTrailer` | Get a vehicle's attached trailer. |
| `sa.GetVehicleVelocity` | Get a vehicle's velocity. |
| `sa.GetVehicleVirtualWorld` | Get a vehicle's virtual world. |
| `sa.GetVehicleZAngle` | Get a vehicle's Z angle. |
| `sa.GetWeaponName` | Resolve a weapon id to its name. |
| `sa.GetWorldTime` | Get the world time. |
| `sa.GivePlayerMoney` | Give (or take) money. |
| `sa.GivePlayerWeapon` | Give a weapon with ammo. |
| `sa.HidePlayerDialog` | Close the player's current dialog. |
| `sa.InterpolateCameraLookAt` | Interpolate the camera look-at point. |
| `sa.InterpolateCameraPos` | Interpolate the camera position. |
| `sa.IsActorInvulnerable` | Whether an actor is invulnerable. |
| `sa.IsActorStreamedIn` | Whether an actor is streamed to a player. |
| `sa.IsObjectMoving` | Whether an object is moving. |
| `sa.IsPlayerAdmin` | Whether a player is an admin. |
| `sa.IsPlayerAttachedObjectSlotUsed` | Whether an attached-object slot is used. |
| `sa.IsPlayerConnected` | Whether a player id is connected. |
| `sa.IsPlayerInAnyVehicle` | Whether a player is in any vehicle. |
| `sa.IsPlayerInCheckpoint` | Whether a player is in their checkpoint. |
| `sa.IsPlayerInDynamicArea` | Whether a player is in a dynamic area. |
| `sa.IsPlayerInDynamicCP` | Whether a player is in a dynamic checkpoint. |
| `sa.IsPlayerInDynamicRaceCP` | Whether a player is in a dynamic race checkpoint. |
| `sa.IsPlayerInRaceCheckpoint` | Whether a player is in a race checkpoint. |
| `sa.IsPlayerInRangeOfPoint` | Whether a player is within range of a point. |
| `sa.IsPlayerInVehicle` | Whether a player is in a specific vehicle. |
| `sa.IsPlayerNPC` | Whether a player is an NPC. |
| `sa.IsPlayerObjectMoving` | Whether a player object is moving. |
| `sa.IsPlayerStreamedIn` | Whether a player is streamed to another. |
| `sa.IsTrailerAttachedToVehicle` | Whether a trailer is attached. |
| `sa.IsValidActor` | Whether an actor id is valid. |
| `sa.IsValidDynamic3DTextLabel` | Whether a dynamic 3D label is valid. |
| `sa.IsValidDynamicActor` | Whether a dynamic actor is valid. |
| `sa.IsValidDynamicArea` | Whether a dynamic area is valid. |
| `sa.IsValidDynamicMapIcon` | Whether a dynamic map icon is valid. |
| `sa.IsValidDynamicObject` | Whether a dynamic object is valid. |
| `sa.IsValidDynamicPickup` | Whether a dynamic pickup is valid. |
| `sa.IsValidObject` | Whether an object id is valid. |
| `sa.IsValidPlayerObject` | Whether a player object is valid. |
| `sa.IsValidVehicle` | Whether a vehicle id is valid. |
| `sa.IsVehicleStreamedIn` | Whether a vehicle is streamed to a player. |
| `sa.Kick` | Kick a player. |
| `sa.KickPlayer` | Kick a player with an optional reason. |
| `sa.KillTimer` | Cancel a timer. |
| `sa.LimitGlobalChatRadius` | Limit global chat to a radius. |
| `sa.LimitPlayerMarkerRadius` | Limit player marker radius. |
| `sa.LinkVehicleToInterior` | Link a vehicle to an interior. |
| `sa.Log` | Write a line to the server log. |
| `sa.ManualVehicleEngineAndLights` | Require manual engine/light control. |
| `sa.MoveDynamicObject` | Move a dynamic object over time. |
| `sa.MoveObject` | Move an object over time. |
| `sa.MovePlayerObject` | Move a player object over time. |
| `sa.NetStats_BytesReceived` | Bytes received for a player. |
| `sa.NetStats_BytesSent` | Bytes sent for a player. |
| `sa.NetStats_ConnectionStatus` | Connection status for a player. |
| `sa.NetStats_GetConnectedTime` | Connected time in milliseconds. |
| `sa.NetStats_GetIpPort` | IP and port for a player. |
| `sa.NetStats_MessagesReceived` | Messages received for a player. |
| `sa.NetStats_MessagesRecvPerSecond` | Messages received per second. |
| `sa.NetStats_MessagesSent` | Messages sent for a player. |
| `sa.NetStats_PacketLossPercent` | Packet loss percentage. |
| `sa.PlayAudioStreamForPlayer` | Play an audio stream URL. |
| `sa.PlayCrimeReportForPlayer` | Play a crime report sound. |
| `sa.PlayerCount` | Number of connected players. |
| `sa.PlayerName` | Get a player's name. |
| `sa.PlayerPlaySound` | Play a sound for a player. |
| `sa.PlayerSpectatePlayer` | Make a player spectate another player. |
| `sa.PlayerSpectateVehicle` | Make a player spectate a vehicle. |
| `sa.PlayerTextDrawAlignment` | Set a player text draw alignment. |
| `sa.PlayerTextDrawBackgroundColor` | Set a player text draw background colour. |
| `sa.PlayerTextDrawBoxColor` | Set a player text draw box colour. |
| `sa.PlayerTextDrawColor` | Set a player text draw text colour. |
| `sa.PlayerTextDrawCreate` | Create a player text draw. |
| `sa.PlayerTextDrawDestroy` | Destroy a player text draw. |
| `sa.PlayerTextDrawFont` | Set a player text draw font. |
| `sa.PlayerTextDrawHide` | Hide a player text draw. |
| `sa.PlayerTextDrawLetterSize` | Set player text draw letter size. |
| `sa.PlayerTextDrawSetOutline` | Set player text draw outline. |
| `sa.PlayerTextDrawSetPreviewModel` | Set the model preview for a player text draw. |
| `sa.PlayerTextDrawSetPreviewRot` | Set the rotation of a model preview. |
| `sa.PlayerTextDrawSetPreviewVehCol` | Set preview vehicle colours. |
| `sa.PlayerTextDrawSetProportional` | Toggle proportional spacing. |
| `sa.PlayerTextDrawSetSelectable` | Make a player text draw selectable. |
| `sa.PlayerTextDrawSetShadow` | Set player text draw shadow. |
| `sa.PlayerTextDrawSetString` | Set player text draw string. |
| `sa.PlayerTextDrawShow` | Show a player text draw. |
| `sa.PlayerTextDrawTextSize` | Set player text draw text size. |
| `sa.PlayerTextDrawUseBox` | Toggle the player text draw box. |
| `sa.PutPlayerInVehicle` | Put a player into a vehicle seat. |
| `sa.RedirectDownload` | Redirect a client download URL. |
| `sa.RemoveBuildingForPlayer` | Remove a map building for a player. |
| `sa.RemovePlayerAttachedObject` | Remove an attached object from a player. |
| `sa.RemovePlayerFromVehicle` | Remove a player from their vehicle. |
| `sa.RemovePlayerMapIcon` | Remove a radar map icon. |
| `sa.RemoveVehicleComponent` | Remove a vehicle component. |
| `sa.RepairVehicle` | Repair a vehicle. |
| `sa.ResetPlayerMoney` | Reset a player's money to zero. |
| `sa.ResetPlayerWeapons` | Remove all of a player's weapons. |
| `sa.SHA256_PassHash` | Hash a password with SHA-256 and salt. |
| `sa.SelectObject` | Open object selection for a player. |
| `sa.SelectTextDraw` | Enable text draw selection mode. |
| `sa.SendClientCheck` | Send an integrity check request to a client. |
| `sa.SendClientMessage` | Send a chat message to a player. |
| `sa.SendClientMessageToAll` | Send a chat message to everyone. |
| `sa.SendDeathMessage` | Add a death to the kill feed. |
| `sa.SendDeathMessageToPlayer` | Add a death to one player's kill feed. |
| `sa.SendPlayerMessageToAll` | Send a message to everyone from a player. |
| `sa.SendPlayerMessageToPlayer` | Send a message from one player to another. |
| `sa.SendRconCommand` | Execute an RCON command. |
| `sa.SetActorFacingAngle` | Set an actor's facing angle. |
| `sa.SetActorHealth` | Set an actor's health. |
| `sa.SetActorInvulnerable` | Make an actor invulnerable. |
| `sa.SetActorPos` | Set an actor's position. |
| `sa.SetActorVirtualWorld` | Set an actor's virtual world. |
| `sa.SetCameraBehindPlayer` | Restore the camera behind the player. |
| `sa.SetDeathDropAmount` | Set the money dropped on death. |
| `sa.SetDynamicActorFacingAngle` | Set a dynamic actor's facing angle. |
| `sa.SetDynamicActorPos` | Set a dynamic actor's position. |
| `sa.SetDynamicObjectMaterial` | Set a dynamic object material. |
| `sa.SetDynamicObjectMaterialText` | Set dynamic object material text. |
| `sa.SetDynamicObjectPos` | Set a dynamic object's position. |
| `sa.SetDynamicObjectRot` | Set a dynamic object's rotation. |
| `sa.SetGameModeText` | Set the gamemode text shown in the browser. |
| `sa.SetGravity` | Set the world gravity. |
| `sa.SetNameTagDrawDistance` | Set the name tag draw distance. |
| `sa.SetObjectMaterial` | Set an object material. |
| `sa.SetObjectMaterialText` | Set object material text. |
| `sa.SetObjectNoCameraCol` | Disable camera collision for an object. |
| `sa.SetObjectPos` | Set an object's position. |
| `sa.SetObjectRot` | Set an object's rotation. |
| `sa.SetObjectRotation` | Set an object's rotation. |
| `sa.SetObjectsDefaultCameraCol` | Toggle default camera collision for objects. |
| `sa.SetPVarFloat` | Set a float player variable. |
| `sa.SetPVarInt` | Set an integer player variable. |
| `sa.SetPVarString` | Set a string player variable. |
| `sa.SetPlayerAdmin` | Grant or revoke admin rights. |
| `sa.SetPlayerAmmo` | Set ammo for a weapon. |
| `sa.SetPlayerArmedWeapon` | Set the armed weapon. |
| `sa.SetPlayerArmour` | Set a player's armour. |
| `sa.SetPlayerAttachedObject` | Attach an object model to a player bone. |
| `sa.SetPlayerCameraBehindPlayer` | Restore the camera behind the player. |
| `sa.SetPlayerCameraLookAt` | Point the camera at a position. |
| `sa.SetPlayerCameraPos` | Set the camera position. |
| `sa.SetPlayerChatBubble` | Show a chat bubble above a player. |
| `sa.SetPlayerCheckpoint` | Create a checkpoint for a player. |
| `sa.SetPlayerColor` | Set a player's name/chat colour. |
| `sa.SetPlayerDrunkLevel` | Set a player's drunk level. |
| `sa.SetPlayerFacingAngle` | Set a player's facing angle. |
| `sa.SetPlayerFightingStyle` | Set a player's fighting style. |
| `sa.SetPlayerHealth` | Set a player's health. |
| `sa.SetPlayerInterior` | Set a player's interior. |
| `sa.SetPlayerMapIcon` | Add a radar map icon for a player. |
| `sa.SetPlayerMarkerForPlayer` | Show or hide another player's marker. |
| `sa.SetPlayerName` | Set a player's name. |
| `sa.SetPlayerObjectMaterial` | Set a player object material. |
| `sa.SetPlayerObjectMaterialText` | Set player object material text. |
| `sa.SetPlayerObjectNoCameraCol` | Disable camera collision for a player object. |
| `sa.SetPlayerObjectPos` | Set a player object's position. |
| `sa.SetPlayerObjectRot` | Set a player object's rotation. |
| `sa.SetPlayerPos` | Teleport a player. |
| `sa.SetPlayerPosFindZ` | Teleport a player and snap to ground Z. |
| `sa.SetPlayerRaceCheckpoint` | Create a race checkpoint for a player. |
| `sa.SetPlayerScore` | Set a player's score. |
| `sa.SetPlayerShopName` | Set the shop name for a player's interior. |
| `sa.SetPlayerSkillLevel` | Set a player's weapon skill level. |
| `sa.SetPlayerSkin` | Set a player's skin. |
| `sa.SetPlayerSpecialAction` | Set a player's special action. |
| `sa.SetPlayerTeam` | Set a player's team. |
| `sa.SetPlayerTime` | Set a player's local time. |
| `sa.SetPlayerVelocity` | Set a player's velocity. |
| `sa.SetPlayerVirtualWorld` | Set a player's virtual world. |
| `sa.SetPlayerWantedLevel` | Set a player's wanted level. |
| `sa.SetPlayerWeather` | Set a player's weather. |
| `sa.SetPlayerWorldBounds` | Set a player's world boundaries. |
| `sa.SetSVarFloat` | Set a float server variable. |
| `sa.SetSVarInt` | Set an integer server variable. |
| `sa.SetSVarString` | Set a string server variable. |
| `sa.SetSpawnInfo` | Set the spawn information for the next spawn. |
| `sa.SetTeamCount` | Set the number of teams. |
| `sa.SetTimer` | Schedule a named function after a delay. |
| `sa.SetTimerEx` | Schedule a named function with arguments. |
| `sa.SetVehicleAngularVelocity` | Set a vehicle's angular velocity. |
| `sa.SetVehicleDamageStatus` | Set vehicle panel/door/light/tyre damage. |
| `sa.SetVehicleHealth` | Set a vehicle's health. |
| `sa.SetVehicleNumberPlate` | Set a vehicle's number plate. |
| `sa.SetVehicleParamsCarDoors` | Set vehicle door open states. |
| `sa.SetVehicleParamsCarWindows` | Set vehicle window open states. |
| `sa.SetVehicleParamsEx` | Set vehicle params (engine, lights, ...). |
| `sa.SetVehicleParamsForPlayer` | Set vehicle params for one player. |
| `sa.SetVehiclePos` | Teleport a vehicle. |
| `sa.SetVehicleToRespawn` | Respawn a vehicle. |
| `sa.SetVehicleVelocity` | Set a vehicle's velocity. |
| `sa.SetVehicleVirtualWorld` | Set a vehicle's virtual world. |
| `sa.SetVehicleZAngle` | Set a vehicle's Z angle. |
| `sa.SetWeather` | Set the global weather. |
| `sa.SetWorldTime` | Set the global world time. |
| `sa.ShowNameTags` | Toggle name tags globally. |
| `sa.ShowPlayerDialog` | Show a dialog to a player. |
| `sa.ShowPlayerMarkers` | Toggle player markers. |
| `sa.ShowPlayerNameTagForPlayer` | Show or hide a name tag for one player. |
| `sa.SpawnPlayer` | Spawn a player immediately. |
| `sa.StartRecordingPlayerData` | Start recording player data. |
| `sa.StopAudioStreamForPlayer` | Stop a player's audio stream. |
| `sa.StopDynamicObject` | Stop a dynamic object's move. |
| `sa.StopObject` | Stop an object's move. |
| `sa.StopPlayerObject` | Stop a player object's move. |
| `sa.StopRecordingPlayerData` | Stop recording player data. |
| `sa.Streamer_CountItems` | Count streamer items of a type. |
| `sa.Streamer_DestroyAllVisibleItems` | Destroy all visible streamer items. |
| `sa.Streamer_GetArrayData` | Read streamer array data. |
| `sa.Streamer_MaxItems` | Set the maximum streamed items. |
| `sa.Streamer_SetArrayData` | Write streamer array data. |
| `sa.Streamer_SetIntData` | Set streamer integer data. |
| `sa.Streamer_SetRadiusMultiplier` | Set the streamer radius multiplier. |
| `sa.Streamer_SetVisibleItems` | Set the visible item count. |
| `sa.Streamer_ToggleIdleUpdate` | Toggle idle streamer updates. |
| `sa.Streamer_Update` | Update the streamer for a player. |
| `sa.Streamer_UpdateEx` | Update the streamer at a position. |
| `sa.TextDrawAlignment` | Set text draw alignment. |
| `sa.TextDrawBackgroundColor` | Set text draw background colour. |
| `sa.TextDrawBoxColor` | Set text draw box colour. |
| `sa.TextDrawColor` | Set text draw text colour. |
| `sa.TextDrawCreate` | Create a global text draw. |
| `sa.TextDrawDestroy` | Destroy a global text draw. |
| `sa.TextDrawFont` | Set text draw font. |
| `sa.TextDrawHideForAll` | Hide a text draw from everyone. |
| `sa.TextDrawHideForPlayer` | Hide a text draw from a player. |
| `sa.TextDrawLetterSize` | Set text draw letter size. |
| `sa.TextDrawSetOutline` | Set text draw outline. |
| `sa.TextDrawSetPreviewModel` | Set a model preview for a text draw. |
| `sa.TextDrawSetPreviewRot` | Set the rotation of a model preview. |
| `sa.TextDrawSetPreviewVehCol` | Set preview vehicle colours. |
| `sa.TextDrawSetProportional` | Toggle proportional spacing. |
| `sa.TextDrawSetSelectable` | Make a text draw selectable. |
| `sa.TextDrawSetShadow` | Set text draw shadow. |
| `sa.TextDrawSetString` | Set text draw string. |
| `sa.TextDrawShowForAll` | Show a text draw to everyone. |
| `sa.TextDrawShowForPlayer` | Show a text draw to a player. |
| `sa.TextDrawTextSize` | Set text draw text size. |
| `sa.TextDrawUseBox` | Toggle the text draw box. |
| `sa.TogglePlayerClock` | Toggle the in-game clock. |
| `sa.TogglePlayerControllable` | Enable or disable player control. |
| `sa.TogglePlayerSpectating` | Toggle spectate mode. |
| `sa.TogglePlayerWidescreen` | Toggle widescreen mode. |
| `sa.UnBlockIpAddress` | Unblock a previously blocked IP. |
| `sa.Update3DTextLabelText` | Update a 3D text label's text. |
| `sa.UpdateDynamic3DTextLabelText` | Update a dynamic 3D label's text. |
| `sa.UpdatePlayer3DTextLabelText` | Update a player 3D label's text. |
| `sa.UpdateVehicleDamageStatus` | Update vehicle damage status. |
| `sa.UsePlayerPedAnims` | Use the player ped animation set. |
| `sa.VectorSize` | Length of a vector (x, y, z). |
| `sa.cache_delete` | Delete a cached result set. |
| `sa.cache_get_field_count` | Number of fields in a cached result. |
| `sa.cache_get_row_count` | Number of rows in a cached result. |
| `sa.cache_get_value_index_int` | Read an integer field by row/column index. |
| `sa.cache_get_value_name` | Read a field value by column name. |
| `sa.cache_get_value_name_float` | Read a float field by column name. |
| `sa.cache_get_value_name_int` | Read an integer field by column name. |
| `sa.cache_insert_id` | Last inserted row id. |
| `sa.format` | Format a string with placeholders. |
| `sa.gpci` | Get the player's client serial (GPCI). |
| `sa.hash_password` | Hash a password with bcrypt. |
| `sa.mysql_close` | Close a MySQL connection. |
| `sa.mysql_errno` | Last MySQL error number. |
| `sa.mysql_format` | Format a MySQL query string. |
| `sa.mysql_open` | Open a MySQL connection. |
| `sa.mysql_pquery` | Run a parallel MySQL query. |
| `sa.mysql_tquery` | Run a threaded MySQL query. |
| `sa.random_token` | Generate a random token string. |
| `sa.sqlite_close` | Close a SQLite connection. |
| `sa.sqlite_exec` | Run a SQLite statement (returns error or null). |
| `sa.sqlite_exec_async` | Run a SQLite statement asynchronously. |
| `sa.sqlite_open` | Open a SQLite connection (returns handle or null). |
| `sa.sqlite_query` | Run a SQLite query (returns result index or null). |
| `sa.sqlite_query_async` | Run a SQLite query asynchronously. |
| `sa.sscanf` | Parse a string by format. |
| `sa.strcat` | Concatenate strings into a destination. |
| `sa.strcmp` | Compare two strings. |
| `sa.strdel` | Delete part of a string. |
| `sa.strfind` | Find a substring. |
| `sa.strins` | Insert a string at an offset. |
| `sa.strlen` | String length. |
| `sa.strmid` | Extract a substring. |
| `sa.strpack` | Pack a string into a destination. |
| `sa.strunpack` | Unpack a string. |
| `sa.strval` | Parse a string to an integer. |
| `sa.verify_password` | Verify a password against a bcrypt hash. |
