# Knight — Native Function Reference

Natives are global functions: `SetPlayerHealth(playerid, 100.0)`.

There are **508** natives.

| Native | Description |
|---|---|
| `AddCharModel` | Register a custom character model (skin). |
| `AddPlayerClass` | Add a spawn class (skin, position, angle, optional weapons). |
| `AddPlayerClassEx` | Add a spawn class for a specific team. |
| `AddSimpleModel` | Register an object model for custom objects. |
| `AddSimpleModelTimed` | Register a time-limited custom object model. |
| `AddStaticPickup` | Create a static pickup (engine-managed). |
| `AddStaticVehicle` | Create a static vehicle (engine-managed). |
| `AddStaticVehicleEx` | Create a static vehicle with respawn delay. |
| `AddVehicleComponent` | Attach a visual component to a vehicle. |
| `AllowAdminTeleport` | Allow admins to teleport with the map. |
| `AllowInteriorWeapons` | Allow weapons inside interiors. |
| `AllowPlayerTeleport` | Allow the player to teleport via the map. |
| `ApplyActorAnimation` | Play an animation on an actor. |
| `ApplyAnimation` | Play a library/name animation on a player. |
| `ApplyDynamicActorAnimation` | Play an animation on a dynamic actor. |
| `ApplyPlayerAnimation` | Play an animation on a player. |
| `Attach3DTextLabelToPlayer` | Attach a 3D text label to a player. |
| `Attach3DTextLabelToVehicle` | Attach a 3D text label to a vehicle. |
| `AttachCameraToObject` | Attach the player camera to an object. |
| `AttachCameraToPlayerObject` | Attach the camera to a player object. |
| `AttachDynamicObjectToPlayer` | Attach a dynamic object to a player. |
| `AttachDynamicObjectToVehicle` | Attach a dynamic object to a vehicle. |
| `AttachObjectToObject` | Attach an object to another object. |
| `AttachObjectToPlayer` | Attach an object to a player bone. |
| `AttachObjectToVehicle` | Attach an object to a vehicle. |
| `AttachPlayerObjectToPlayer` | Attach a player object to a player. |
| `AttachPlayerObjectToVehicle` | Attach a player object to a vehicle. |
| `AttachTrailerToVehicle` | Attach a trailer to a vehicle. |
| `Ban` | Ban a player by id. |
| `BanEx` | Ban a player with a reason. |
| `BanPlayer` | Ban a player with an optional reason. |
| `BlockIpAddress` | Block an IP address for a duration. |
| `CallLocalFunction` | Call a gamemode function by name. |
| `CallRemoteFunction` | Call a function in another script. |
| `CancelEdit` | Cancel object editing for a player. |
| `CancelSelectTextDraw` | Cancel text draw selection mode. |
| `ChangeVehicleColor` | Change a vehicle's colours. |
| `ChangeVehiclePaintjob` | Change a vehicle's paintjob. |
| `ClearActorAnimation` | Stop an actor's animation. |
| `ClearActorAnimations` | Stop all animations on an actor. |
| `ClearAnimations` | Stop a player's animation. |
| `ClearDynamicActorAnimations` | Stop all animations on a dynamic actor. |
| `ClearPlayerAnimation` | Stop a player's animation. |
| `ConnectNPC` | Connect an NPC into the world. |
| `Create3DTextLabel` | Create a 3D text label in the world. |
| `Create3DTextLabelAttachedToPlayer` | Create a 3D label attached to a player. |
| `Create3DTextLabelAttachedToVehicle` | Create a 3D label attached to a vehicle. |
| `CreateActor` | Create a static actor. |
| `CreateDynamic3DTextLabel` | Create a streamed 3D text label. |
| `CreateDynamicActor` | Create a streamed dynamic actor. |
| `CreateDynamicCP` | Create a streamed checkpoint. |
| `CreateDynamicCircle` | Create a streamed circular area. |
| `CreateDynamicMapIcon` | Create a streamed radar map icon. |
| `CreateDynamicObject` | Create a streamed object. |
| `CreateDynamicPickup` | Create a streamed pickup. |
| `CreateDynamicRaceCP` | Create a streamed race checkpoint. |
| `CreateDynamicRectangle` | Create a streamed rectangular area. |
| `CreateExplosion` | Create an explosion in the world. |
| `CreateExplosionForPlayer` | Create an explosion visible to one player. |
| `CreateObject` | Create a global object. |
| `CreatePickup` | Create a pickup. |
| `CreatePlayer3DTextLabel` | Create a player-local 3D text label. |
| `CreatePlayerObject` | Create a player-local object. |
| `CreateVehicle` | Create a vehicle; returns its id. |
| `Delete3DTextLabel` | Delete a 3D text label. |
| `DeletePVar` | Delete a player variable. |
| `DeletePlayer3DTextLabel` | Delete a player 3D text label. |
| `DeleteSVar` | Delete a server variable. |
| `DestroyActor` | Destroy a static actor. |
| `DestroyDynamic3DTextLabel` | Destroy a streamed 3D text label. |
| `DestroyDynamicActor` | Destroy a dynamic actor. |
| `DestroyDynamicArea` | Destroy a dynamic area. |
| `DestroyDynamicCP` | Destroy a streamed checkpoint. |
| `DestroyDynamicMapIcon` | Destroy a streamed map icon. |
| `DestroyDynamicObject` | Destroy a streamed object. |
| `DestroyDynamicPickup` | Destroy a streamed pickup. |
| `DestroyDynamicRaceCP` | Destroy a streamed race checkpoint. |
| `DestroyObject` | Destroy a global object. |
| `DestroyPickup` | Destroy a pickup. |
| `DestroyPlayerObject` | Destroy a player object. |
| `DestroyVehicle` | Destroy a vehicle. |
| `DetachTrailerFromVehicle` | Detach a trailer from a vehicle. |
| `DisableInteriorEnterExits` | Remove interior entrance markers from the map. |
| `DisableNameTagLOS` | Remove line-of-sight checks for name tags. |
| `DisablePlayerCheckpoint` | Remove the player's checkpoint. |
| `DisablePlayerRaceCheckpoint` | Remove the player's race checkpoint. |
| `DisableRemoteVehicleCollisions` | Disable collisions with remote vehicles. |
| `EditAttachedObject` | Open the attached-object editor. |
| `EditDynamicObject` | Open the object editor for a dynamic object. |
| `EditObject` | Open the object editor. |
| `EditPlayerObject` | Open the editor for a player object. |
| `EnablePlayerCameraTarget` | Enable camera target queries for a player. |
| `EnableStuntBonusForAll` | Enable stunt bonuses for everyone. |
| `EnableStuntBonusForPlayer` | Enable stunt bonuses for a player. |
| `EnableTirePopping` | Enable tyre popping. |
| `EnableVehicleFriendlyFire` | Allow players in the same team to damage vehicles. |
| `EnableZoneNames` | Show zone names above the radar. |
| `FindModelFileNameFromCRC` | Resolve a model file name from its CRC. |
| `FindTextureFileNameFromCRC` | Resolve a texture file name from its CRC. |
| `ForceClassSelection` | Force the class-selection screen. |
| `GameModeExit` | Shut the server down cleanly. |
| `GameTextForAll` | Show game text to all players. |
| `GameTextForPlayer` | Show game text to one player. |
| `GangZoneCreate` | Create a gang zone rectangle. |
| `GangZoneDestroy` | Destroy a gang zone. |
| `GangZoneFlashForAll` | Flash a gang zone for all players. |
| `GangZoneFlashForPlayer` | Flash a gang zone for one player. |
| `GangZoneHideForAll` | Hide a gang zone from all players. |
| `GangZoneHideForPlayer` | Hide a gang zone from one player. |
| `GangZoneShowForAll` | Show a gang zone to all players. |
| `GangZoneShowForPlayer` | Show a gang zone to one player. |
| `GangZoneStopFlashForAll` | Stop flashing a gang zone for all players. |
| `GangZoneStopFlashForPlayer` | Stop flashing a gang zone for one player. |
| `GetActorFacingAngle` | Get an actor's facing angle. |
| `GetActorHealth` | Get an actor's health. |
| `GetActorPoolSize` | Highest allocated actor id. |
| `GetActorPos` | Get an actor's position. |
| `GetActorVirtualWorld` | Get an actor's virtual world. |
| `GetAnimationName` | Resolve an animation index to library/name. |
| `GetConsoleVarAsBool` | Read a boolean console variable. |
| `GetConsoleVarAsInt` | Read an integer console variable. |
| `GetConsoleVarAsString` | Read a string console variable. |
| `GetDistanceBetweenPlayers` | Distance between two players. |
| `GetDynamicObjectPos` | Get a dynamic object's position. |
| `GetDynamicObjectRot` | Get a dynamic object's rotation. |
| `GetGravity` | Get the world gravity. |
| `GetMaxPlayers` | Get the configured player slot count. |
| `GetNetworkStats` | Get network statistics for a player. |
| `GetObjectModel` | Get an object's model id. |
| `GetObjectPos` | Get an object's position. |
| `GetObjectPosX` | Get an object's X coordinate. |
| `GetObjectPosY` | Get an object's Y coordinate. |
| `GetObjectPosZ` | Get an object's Z coordinate. |
| `GetObjectRot` | Get an object's rotation. |
| `GetPVarFloat` | Read a float player variable. |
| `GetPVarInt` | Read an integer player variable. |
| `GetPVarNameAtIndex` | Get a player variable name at an index. |
| `GetPVarString` | Read a string player variable. |
| `GetPVarType` | Get a player variable's type. |
| `GetPVarsUpperIndex` | Highest player variable index. |
| `GetPlayerAmmo` | Get a player's ammo. |
| `GetPlayerAnimationIndex` | Get the current animation index. |
| `GetPlayerArmour` | Get a player's armour. |
| `GetPlayerCameraAspectRatio` | Get the camera aspect ratio. |
| `GetPlayerCameraFrontVector` | Get the camera forward vector. |
| `GetPlayerCameraMode` | Get the camera mode. |
| `GetPlayerCameraPos` | Get the camera position. |
| `GetPlayerCameraTargetActor` | Get the actor the camera targets. |
| `GetPlayerCameraTargetObject` | Get the object the camera targets. |
| `GetPlayerCameraTargetPlayer` | Get the player the camera targets. |
| `GetPlayerCameraTargetVehicle` | Get the vehicle the camera targets. |
| `GetPlayerCameraZoom` | Get the camera zoom. |
| `GetPlayerColor` | Get a player's colour. |
| `GetPlayerCustomSkin` | Get a player's custom skin id. |
| `GetPlayerDistanceFromPoint` | Distance from a player to a point. |
| `GetPlayerDrunkLevel` | Get a player's drunk level. |
| `GetPlayerFacingAngle` | Get a player's facing angle. |
| `GetPlayerFightingStyle` | Get a player's fighting style. |
| `GetPlayerHealth` | Get a player's health. |
| `GetPlayerInterior` | Get a player's interior. |
| `GetPlayerIp` | Get a player's IP address. |
| `GetPlayerKeys` | Get a player's keys, up/down and left/right state. |
| `GetPlayerLastShotVectors` | Get the last shot origin and hit vectors. |
| `GetPlayerMoney` | Get a player's money. |
| `GetPlayerNetworkStats` | Get a player's network statistics. |
| `GetPlayerObjectModel` | Get a player object's model. |
| `GetPlayerObjectPos` | Get a player object's position. |
| `GetPlayerObjectRot` | Get a player object's rotation. |
| `GetPlayerPing` | Get a player's ping. |
| `GetPlayerPoolSize` | Highest allocated player id. |
| `GetPlayerPos` | Get a player's position. |
| `GetPlayerPosX` | Get a player's X coordinate. |
| `GetPlayerPosY` | Get a player's Y coordinate. |
| `GetPlayerPosZ` | Get a player's Z coordinate. |
| `GetPlayerScore` | Get a player's score. |
| `GetPlayerSkin` | Get a player's skin. |
| `GetPlayerSpecialAction` | Get a player's special action. |
| `GetPlayerState` | Get a player's state. |
| `GetPlayerSurfingObjectID` | Get the object the player is surfing. |
| `GetPlayerSurfingVehicleID` | Get the vehicle the player is surfing. |
| `GetPlayerTargetActor` | Get the actor a player is targeting. |
| `GetPlayerTargetPlayer` | Get the player a player is targeting. |
| `GetPlayerTeam` | Get a player's team. |
| `GetPlayerTime` | Get a player's local time. |
| `GetPlayerVehicleID` | Get the vehicle id a player is in. |
| `GetPlayerVehicleSeat` | Get the seat a player occupies. |
| `GetPlayerVelocity` | Get a player's velocity. |
| `GetPlayerVersion` | Get a player's client version string. |
| `GetPlayerVirtualWorld` | Get a player's virtual world. |
| `GetPlayerWantedLevel` | Get a player's wanted level. |
| `GetPlayerWeapon` | Get a player's current weapon. |
| `GetPlayerWeaponData` | Get weapon/ammo for a weapon slot. |
| `GetPlayerWeaponState` | Get the weapon state. |
| `GetSVarFloat` | Read a float server variable. |
| `GetSVarInt` | Read an integer server variable. |
| `GetSVarNameAtIndex` | Get a server variable name at an index. |
| `GetSVarString` | Read a string server variable. |
| `GetSVarType` | Get a server variable's type. |
| `GetSVarsUpperIndex` | Highest server variable index. |
| `GetServerTickRate` | Get the server tick rate. |
| `GetServerVarAsBool` | Read a boolean server variable. |
| `GetServerVarAsInt` | Read an integer server variable. |
| `GetServerVarAsString` | Read a string server variable. |
| `GetTickCount` | Milliseconds since server start. |
| `GetVehicleComponentInSlot` | Get the component in a vehicle slot. |
| `GetVehicleComponentType` | Get a component's type. |
| `GetVehicleDamageStatus` | Get vehicle panel/door/light/tyre damage. |
| `GetVehicleDistanceFromPoint` | Distance from a vehicle to a point. |
| `GetVehicleHealth` | Get a vehicle's health. |
| `GetVehicleModel` | Get a vehicle's model id. |
| `GetVehicleModelInfo` | Get model info (size, seats, ...). |
| `GetVehicleParamsCarDoors` | Get vehicle door open states. |
| `GetVehicleParamsCarWindows` | Get vehicle window open states. |
| `GetVehicleParamsEx` | Get vehicle params (engine, lights, ...). |
| `GetVehicleParamsSirenState` | Get the siren state. |
| `GetVehiclePoolSize` | Highest allocated vehicle id. |
| `GetVehiclePos` | Get a vehicle's position. |
| `GetVehiclePosX` | Get a vehicle's X coordinate. |
| `GetVehiclePosY` | Get a vehicle's Y coordinate. |
| `GetVehiclePosZ` | Get a vehicle's Z coordinate. |
| `GetVehicleRotationQuat` | Get a vehicle's rotation quaternion. |
| `GetVehicleTrailer` | Get a vehicle's attached trailer. |
| `GetVehicleVelocity` | Get a vehicle's velocity. |
| `GetVehicleVirtualWorld` | Get a vehicle's virtual world. |
| `GetVehicleZAngle` | Get a vehicle's Z angle. |
| `GetWeaponName` | Resolve a weapon id to its name. |
| `GetWorldTime` | Get the world time. |
| `GivePlayerMoney` | Give (or take) money. |
| `GivePlayerWeapon` | Give a weapon with ammo. |
| `HidePlayerDialog` | Close the player's current dialog. |
| `InterpolateCameraLookAt` | Interpolate the camera look-at point. |
| `InterpolateCameraPos` | Interpolate the camera position. |
| `IsActorInvulnerable` | Whether an actor is invulnerable. |
| `IsActorStreamedIn` | Whether an actor is streamed to a player. |
| `IsObjectMoving` | Whether an object is moving. |
| `IsPlayerAdmin` | Whether a player is an admin. |
| `IsPlayerAttachedObjectSlotUsed` | Whether an attached-object slot is used. |
| `IsPlayerConnected` | Whether a player id is connected. |
| `IsPlayerInAnyVehicle` | Whether a player is in any vehicle. |
| `IsPlayerInCheckpoint` | Whether a player is in their checkpoint. |
| `IsPlayerInDynamicArea` | Whether a player is in a dynamic area. |
| `IsPlayerInDynamicCP` | Whether a player is in a dynamic checkpoint. |
| `IsPlayerInDynamicRaceCP` | Whether a player is in a dynamic race checkpoint. |
| `IsPlayerInRaceCheckpoint` | Whether a player is in a race checkpoint. |
| `IsPlayerInRangeOfPoint` | Whether a player is within range of a point. |
| `IsPlayerInVehicle` | Whether a player is in a specific vehicle. |
| `IsPlayerNPC` | Whether a player is an NPC. |
| `IsPlayerObjectMoving` | Whether a player object is moving. |
| `IsPlayerStreamedIn` | Whether a player is streamed to another. |
| `IsTrailerAttachedToVehicle` | Whether a trailer is attached. |
| `IsValidActor` | Whether an actor id is valid. |
| `IsValidCustomModel` | Whether an id is a registered custom skin or object id. |
| `IsValidDynamic3DTextLabel` | Whether a dynamic 3D label is valid. |
| `IsValidDynamicActor` | Whether a dynamic actor is valid. |
| `IsValidDynamicArea` | Whether a dynamic area is valid. |
| `IsValidDynamicMapIcon` | Whether a dynamic map icon is valid. |
| `IsValidDynamicObject` | Whether a dynamic object is valid. |
| `IsValidDynamicPickup` | Whether a dynamic pickup is valid. |
| `IsValidObject` | Whether an object id is valid. |
| `IsValidPlayerObject` | Whether a player object is valid. |
| `IsValidVehicle` | Whether a vehicle id is valid. |
| `IsVehicleStreamedIn` | Whether a vehicle is streamed to a player. |
| `Kick` | Kick a player. |
| `KickPlayer` | Kick a player with an optional reason. |
| `KillTimer` | Cancel a timer. |
| `LimitGlobalChatRadius` | Limit global chat to a radius. |
| `LimitPlayerMarkerRadius` | Limit player marker radius. |
| `LinkVehicleToInterior` | Link a vehicle to an interior. |
| `Log` | Write a line to the server log. |
| `ManualVehicleEngineAndLights` | Require manual engine/light control. |
| `MoveDynamicObject` | Move a dynamic object over time. |
| `MoveObject` | Move an object over time. |
| `MovePlayerObject` | Move a player object over time. |
| `NetStats_BytesReceived` | Bytes received for a player. |
| `NetStats_BytesSent` | Bytes sent for a player. |
| `NetStats_ConnectionStatus` | Connection status for a player. |
| `NetStats_GetConnectedTime` | Connected time in milliseconds. |
| `NetStats_GetIpPort` | IP and port for a player. |
| `NetStats_MessagesReceived` | Messages received for a player. |
| `NetStats_MessagesRecvPerSecond` | Messages received per second. |
| `NetStats_MessagesSent` | Messages sent for a player. |
| `NetStats_PacketLossPercent` | Packet loss percentage. |
| `PlayAudioStreamForPlayer` | Play an audio stream URL. |
| `PlayCrimeReportForPlayer` | Play a crime report sound. |
| `PlayerCount` | Number of connected players. |
| `PlayerName` | Get a player's name. |
| `PlayerPlaySound` | Play a sound for a player. |
| `PlayerSpectatePlayer` | Make a player spectate another player. |
| `PlayerSpectateVehicle` | Make a player spectate a vehicle. |
| `PlayerTextDrawAlignment` | Set a player text draw alignment. |
| `PlayerTextDrawBackgroundColor` | Set a player text draw background colour. |
| `PlayerTextDrawBoxColor` | Set a player text draw box colour. |
| `PlayerTextDrawColor` | Set a player text draw text colour. |
| `PlayerTextDrawCreate` | Create a player text draw. |
| `PlayerTextDrawDestroy` | Destroy a player text draw. |
| `PlayerTextDrawFont` | Set a player text draw font. |
| `PlayerTextDrawHide` | Hide a player text draw. |
| `PlayerTextDrawLetterSize` | Set player text draw letter size. |
| `PlayerTextDrawSetOutline` | Set player text draw outline. |
| `PlayerTextDrawSetPreviewModel` | Set the model preview for a player text draw. |
| `PlayerTextDrawSetPreviewRot` | Set the rotation of a model preview. |
| `PlayerTextDrawSetPreviewVehCol` | Set preview vehicle colours. |
| `PlayerTextDrawSetProportional` | Toggle proportional spacing. |
| `PlayerTextDrawSetSelectable` | Make a player text draw selectable. |
| `PlayerTextDrawSetShadow` | Set player text draw shadow. |
| `PlayerTextDrawSetString` | Set player text draw string. |
| `PlayerTextDrawShow` | Show a player text draw. |
| `PlayerTextDrawTextSize` | Set player text draw text size. |
| `PlayerTextDrawUseBox` | Toggle the player text draw box. |
| `PutPlayerInVehicle` | Put a player into a vehicle seat. |
| `RedirectDownload` | Redirect a client download URL. |
| `RemoveBuildingForPlayer` | Remove a map building for a player. |
| `RemovePlayerAttachedObject` | Remove an attached object from a player. |
| `RemovePlayerFromVehicle` | Remove a player from their vehicle. |
| `RemovePlayerMapIcon` | Remove a radar map icon. |
| `RemoveVehicleComponent` | Remove a vehicle component. |
| `RepairVehicle` | Repair a vehicle. |
| `ResetPlayerMoney` | Reset a player's money to zero. |
| `ResetPlayerWeapons` | Remove all of a player's weapons. |
| `SHA256_PassHash` | Hash a password with SHA-256 and salt. |
| `SelectObject` | Open object selection for a player. |
| `SelectTextDraw` | Enable text draw selection mode. |
| `SendClientCheck` | Send an integrity check request to a client. |
| `SendClientMessage` | Send a chat message to a player. |
| `SendClientMessageToAll` | Send a chat message to everyone. |
| `SendDeathMessage` | Add a death to the kill feed. |
| `SendDeathMessageToPlayer` | Add a death to one player's kill feed. |
| `SendPlayerMessageToAll` | Send a message to everyone from a player. |
| `SendPlayerMessageToPlayer` | Send a message from one player to another. |
| `SendRconCommand` | Execute an RCON command. |
| `SetActorFacingAngle` | Set an actor's facing angle. |
| `SetActorHealth` | Set an actor's health. |
| `SetActorInvulnerable` | Make an actor invulnerable. |
| `SetActorPos` | Set an actor's position. |
| `SetActorVirtualWorld` | Set an actor's virtual world. |
| `SetCameraBehindPlayer` | Restore the camera behind the player. |
| `SetDeathDropAmount` | Set the money dropped on death. |
| `SetDynamicActorFacingAngle` | Set a dynamic actor's facing angle. |
| `SetDynamicActorPos` | Set a dynamic actor's position. |
| `SetDynamicObjectMaterial` | Set a dynamic object material. |
| `SetDynamicObjectMaterialText` | Set dynamic object material text. |
| `SetDynamicObjectPos` | Set a dynamic object's position. |
| `SetDynamicObjectRot` | Set a dynamic object's rotation. |
| `SetGameModeText` | Set the gamemode text shown in the browser. |
| `SetGravity` | Set the world gravity. |
| `SetNameTagDrawDistance` | Set the name tag draw distance. |
| `SetObjectMaterial` | Set an object material. |
| `SetObjectMaterialText` | Set object material text. |
| `SetObjectNoCameraCol` | Disable camera collision for an object. |
| `SetObjectPos` | Set an object's position. |
| `SetObjectRot` | Set an object's rotation. |
| `SetObjectRotation` | Set an object's rotation. |
| `SetObjectsDefaultCameraCol` | Toggle default camera collision for objects. |
| `SetPVarFloat` | Set a float player variable. |
| `SetPVarInt` | Set an integer player variable. |
| `SetPVarString` | Set a string player variable. |
| `SetPlayerAdmin` | Grant or revoke admin rights. |
| `SetPlayerAmmo` | Set ammo for a weapon. |
| `SetPlayerArmedWeapon` | Set the armed weapon. |
| `SetPlayerArmour` | Set a player's armour. |
| `SetPlayerAttachedObject` | Attach an object model to a player bone. |
| `SetPlayerCameraBehindPlayer` | Restore the camera behind the player. |
| `SetPlayerCameraLookAt` | Point the camera at a position. |
| `SetPlayerCameraPos` | Set the camera position. |
| `SetPlayerChatBubble` | Show a chat bubble above a player. |
| `SetPlayerCheckpoint` | Create a checkpoint for a player. |
| `SetPlayerColor` | Set a player's name/chat colour. |
| `SetPlayerDrunkLevel` | Set a player's drunk level. |
| `SetPlayerFacingAngle` | Set a player's facing angle. |
| `SetPlayerFightingStyle` | Set a player's fighting style. |
| `SetPlayerHealth` | Set a player's health. |
| `SetPlayerInterior` | Set a player's interior. |
| `SetPlayerMapIcon` | Add a radar map icon for a player. |
| `SetPlayerMarkerForPlayer` | Show or hide another player's marker. |
| `SetPlayerName` | Set a player's name. |
| `SetPlayerObjectMaterial` | Set a player object material. |
| `SetPlayerObjectMaterialText` | Set player object material text. |
| `SetPlayerObjectNoCameraCol` | Disable camera collision for a player object. |
| `SetPlayerObjectPos` | Set a player object's position. |
| `SetPlayerObjectRot` | Set a player object's rotation. |
| `SetPlayerPos` | Teleport a player. |
| `SetPlayerPosFindZ` | Teleport a player and snap to ground Z. |
| `SetPlayerRaceCheckpoint` | Create a race checkpoint for a player. |
| `SetPlayerScore` | Set a player's score. |
| `SetPlayerShopName` | Set the shop name for a player's interior. |
| `SetPlayerSkillLevel` | Set a player's weapon skill level. |
| `SetPlayerSkin` | Set a player's skin. |
| `SetPlayerSpecialAction` | Set a player's special action. |
| `SetPlayerTeam` | Set a player's team. |
| `SetPlayerTime` | Set a player's local time. |
| `SetPlayerVelocity` | Set a player's velocity. |
| `SetPlayerVirtualWorld` | Set a player's virtual world. |
| `SetPlayerWantedLevel` | Set a player's wanted level. |
| `SetPlayerWeather` | Set a player's weather. |
| `SetPlayerWorldBounds` | Set a player's world boundaries. |
| `SetSVarFloat` | Set a float server variable. |
| `SetSVarInt` | Set an integer server variable. |
| `SetSVarString` | Set a string server variable. |
| `SetSpawnInfo` | Set the spawn information for the next spawn. |
| `SetTeamCount` | Set the number of teams. |
| `SetTimer` | Schedule a named function after a delay. |
| `SetTimerEx` | Schedule a named function with arguments. |
| `SetVehicleAngularVelocity` | Set a vehicle's angular velocity. |
| `SetVehicleDamageStatus` | Set vehicle panel/door/light/tyre damage. |
| `SetVehicleHealth` | Set a vehicle's health. |
| `SetVehicleNumberPlate` | Set a vehicle's number plate. |
| `SetVehicleParamsCarDoors` | Set vehicle door open states. |
| `SetVehicleParamsCarWindows` | Set vehicle window open states. |
| `SetVehicleParamsEx` | Set vehicle params (engine, lights, ...). |
| `SetVehicleParamsForPlayer` | Set vehicle params for one player. |
| `SetVehiclePos` | Teleport a vehicle. |
| `SetVehicleToRespawn` | Respawn a vehicle. |
| `SetVehicleVelocity` | Set a vehicle's velocity. |
| `SetVehicleVirtualWorld` | Set a vehicle's virtual world. |
| `SetVehicleZAngle` | Set a vehicle's Z angle. |
| `SetWeather` | Set the global weather. |
| `SetWorldTime` | Set the global world time. |
| `ShowNameTags` | Toggle name tags globally. |
| `ShowPlayerDialog` | Show a dialog to a player. |
| `ShowPlayerMarkers` | Toggle player markers. |
| `ShowPlayerNameTagForPlayer` | Show or hide a name tag for one player. |
| `SpawnPlayer` | Spawn a player immediately. |
| `StartRecordingPlayerData` | Start recording player data. |
| `StopAudioStreamForPlayer` | Stop a player's audio stream. |
| `StopDynamicObject` | Stop a dynamic object's move. |
| `StopObject` | Stop an object's move. |
| `StopPlayerObject` | Stop a player object's move. |
| `StopRecordingPlayerData` | Stop recording player data. |
| `Streamer_CountItems` | Count streamer items of a type. |
| `Streamer_DestroyAllVisibleItems` | Destroy all visible streamer items. |
| `Streamer_GetArrayData` | Read streamer array data. |
| `Streamer_MaxItems` | Set the maximum streamed items. |
| `Streamer_SetArrayData` | Write streamer array data. |
| `Streamer_SetIntData` | Set streamer integer data. |
| `Streamer_SetRadiusMultiplier` | Set the streamer radius multiplier. |
| `Streamer_SetVisibleItems` | Set the visible item count. |
| `Streamer_ToggleIdleUpdate` | Toggle idle streamer updates. |
| `Streamer_Update` | Update the streamer for a player. |
| `Streamer_UpdateEx` | Update the streamer at a position. |
| `TextDrawAlignment` | Set text draw alignment. |
| `TextDrawBackgroundColor` | Set text draw background colour. |
| `TextDrawBoxColor` | Set text draw box colour. |
| `TextDrawColor` | Set text draw text colour. |
| `TextDrawCreate` | Create a global text draw. |
| `TextDrawDestroy` | Destroy a global text draw. |
| `TextDrawFont` | Set text draw font. |
| `TextDrawHideForAll` | Hide a text draw from everyone. |
| `TextDrawHideForPlayer` | Hide a text draw from a player. |
| `TextDrawLetterSize` | Set text draw letter size. |
| `TextDrawSetOutline` | Set text draw outline. |
| `TextDrawSetPreviewModel` | Set a model preview for a text draw. |
| `TextDrawSetPreviewRot` | Set the rotation of a model preview. |
| `TextDrawSetPreviewVehCol` | Set preview vehicle colours. |
| `TextDrawSetProportional` | Toggle proportional spacing. |
| `TextDrawSetSelectable` | Make a text draw selectable. |
| `TextDrawSetShadow` | Set text draw shadow. |
| `TextDrawSetString` | Set text draw string. |
| `TextDrawShowForAll` | Show a text draw to everyone. |
| `TextDrawShowForPlayer` | Show a text draw to a player. |
| `TextDrawTextSize` | Set text draw text size. |
| `TextDrawUseBox` | Toggle the text draw box. |
| `TogglePlayerClock` | Toggle the in-game clock. |
| `TogglePlayerControllable` | Enable or disable player control. |
| `TogglePlayerSpectating` | Toggle spectate mode. |
| `TogglePlayerWidescreen` | Toggle widescreen mode. |
| `UnBlockIpAddress` | Unblock a previously blocked IP. |
| `Update3DTextLabelText` | Update a 3D text label's text. |
| `UpdateDynamic3DTextLabelText` | Update a dynamic 3D label's text. |
| `UpdatePlayer3DTextLabelText` | Update a player 3D label's text. |
| `UpdateVehicleDamageStatus` | Update vehicle damage status. |
| `UsePlayerPedAnims` | Use the player ped animation set. |
| `VectorSize` | Length of a vector (x, y, z). |
| `cache_delete` | Delete a cached result set. |
| `cache_get_field_count` | Number of fields in a cached result. |
| `cache_get_row_count` | Number of rows in a cached result. |
| `cache_get_value_index_int` | Read an integer field by row/column index. |
| `cache_get_value_name` | Read a field value by column name. |
| `cache_get_value_name_float` | Read a float field by column name. |
| `cache_get_value_name_int` | Read an integer field by column name. |
| `cache_insert_id` | Last inserted row id. |
| `format` | Format a string with placeholders. |
| `gpci` | Get the player's client serial (GPCI). |
| `hash_password` | Hash a password with bcrypt. |
| `mysql_close` | Close a MySQL connection. |
| `mysql_errno` | Last MySQL error number. |
| `mysql_format` | Format a MySQL query string. |
| `mysql_open` | Open a MySQL connection. |
| `mysql_pquery` | Run a parallel MySQL query. |
| `mysql_tquery` | Run a threaded MySQL query. |
| `random_token` | Generate a random token string. |
| `sqlite_close` | Close a SQLite connection. |
| `sqlite_exec` | Run a SQLite statement (returns error or null). |
| `sqlite_exec_async` | Run a SQLite statement asynchronously. |
| `sqlite_open` | Open a SQLite connection (returns handle or null). |
| `sqlite_query` | Run a SQLite query (returns result index or null). |
| `sqlite_query_async` | Run a SQLite query asynchronously. |
| `sscanf` | Parse a string by format. |
| `strcat` | Concatenate strings into a destination. |
| `strcmp` | Compare two strings. |
| `strdel` | Delete part of a string. |
| `strfind` | Find a substring. |
| `strins` | Insert a string at an offset. |
| `strlen` | String length. |
| `strmid` | Extract a substring. |
| `strpack` | Pack a string into a destination. |
| `strunpack` | Unpack a string. |
| `strval` | Parse a string to an integer. |
| `verify_password` | Verify a password against a bcrypt hash. |

## Engine constants

| Constant | Value |
|---|---|
| `BONE_HEAD` | `2` |
| `BONE_LEFT_HAND` | `5` |
| `BONE_PELVIS` | `1` |
| `BONE_RIGHT_HAND` | `6` |
| `BONE_SPINE` | `1` |
| `DOWNLOAD_REQUEST_EMPTY` | `0` |
| `DOWNLOAD_REQUEST_MODEL_FILE` | `1` |
| `DOWNLOAD_REQUEST_TEXTURE_FILE` | `2` |
| `INVALID_PLAYER_ID` | `65535` |
| `INVALID_VEHICLE_ID` | `65535` |
| `MAX_CUSTOM_OBJECT_ID` | `-1000` |
| `MAX_CUSTOM_SKIN_ID` | `30000` |
| `MAX_PLAYERS` | `1000` |
| `MIN_CUSTOM_OBJECT_ID` | `-30000` |
| `MIN_CUSTOM_SKIN_ID` | `20001` |
| `SPECIAL_ACTION_DANCE1` | `5` |
| `SPECIAL_ACTION_HANDSUP` | `2` |
| `SPECIAL_ACTION_NONE` | `0` |
