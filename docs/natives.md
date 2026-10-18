# Knight — Native & Object Reference

Engine functions are called as `sa.<Native>(...)`. All 498 natives are
available from any handler. The tables below also document the typed object
surface (fields and methods) and namespace helpers.

## `Broadcast`

### Methods

| Method | Returns |
|---|---|
| `log(string)` | `—` |
| `message(string)` | `—` |

## `Object`

### Fields

| Field | Type | Access |
|---|---|---|
| `id` | `int` | read |
| `model` | `int` | read |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

| Method | Returns |
|---|---|
| `destroy()` | `—` |
| `move(float, float, float, float, float, float, float)` | `—` |
| `set_material(int, int, string, string, int)` | `—` |
| `set_position(float, float, float)` | `—` |
| `set_rotation(float, float, float)` | `—` |
| `stop()` | `—` |

**Factory:** `Object.create(int, float, float, float, float, float, float, float) -> Object`

## `Player`

### Fields

| Field | Type | Access |
|---|---|---|
| `armor` | `float` | read/write |
| `armour` | `float` | read/write |
| `color` | `int` | read/write |
| `colour` | `int` | read/write |
| `connected` | `bool` | read |
| `facing_angle` | `float` | read/write |
| `health` | `float` | read/write |
| `id` | `int` | read |
| `interior` | `int` | read/write |
| `ip` | `string` | read |
| `money` | `int` | read/write |
| `name` | `string` | read/write |
| `ping` | `int` | read |
| `score` | `int` | read/write |
| `skin` | `int` | read/write |
| `team` | `int` | read/write |
| `vehicle` | `int` | read |
| `virtual_world` | `int` | read/write |
| `weapon` | `int` | read/write |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

| Method | Returns |
|---|---|
| `apply_animation(string, string, float, bool, bool, bool, bool, int)` | `—` |
| `apply_animation2(string, string, float, bool, bool, bool, bool, int)` | `—` |
| `ban()` | `—` |
| `ban_with_reason(string)` | `—` |
| `clear_animations()` | `—` |
| `disable_checkpoint()` | `—` |
| `distance_to(Player)` | `float` |
| `force_class_selection()` | `—` |
| `get_position()` | `array` |
| `give_weapon(int, int)` | `—` |
| `hide_textdraw(TextDraw)` | `—` |
| `is_admin()` | `bool` |
| `kick()` | `—` |
| `kick_with_reason(string)` | `—` |
| `message(string, int)` | `—` |
| `reset_money()` | `—` |
| `reset_weapons()` | `—` |
| `send_message(string)` | `—` |
| `send_score(int)` | `—` |
| `set_admin(bool)` | `—` |
| `set_armor(float)` | `—` |
| `set_armour(float)` | `—` |
| `set_camera_behind()` | `—` |
| `set_camera_look_at(float, float, float, int)` | `—` |
| `set_camera_pos(float, float, float)` | `—` |
| `set_checkpoint(float, float, float, float)` | `—` |
| `set_color(int)` | `—` |
| `set_health(float)` | `—` |
| `set_interior(int)` | `—` |
| `set_map_icon(int, float, float, float, int, int, int)` | `—` |
| `set_money(int)` | `—` |
| `set_position(float, float, float)` | `—` |
| `set_skin(int)` | `—` |
| `set_special_action(int)` | `—` |
| `set_team(int)` | `—` |
| `set_virtual_world(int)` | `—` |
| `show_dialog(int, int, string, string, string, string)` | `—` |
| `show_textdraw(TextDraw)` | `—` |

## `TextDraw`

### Fields

| Field | Type | Access |
|---|---|---|
| `id` | `int` | read |

### Methods

| Method | Returns |
|---|---|
| `destroy()` | `—` |
| `set_string(string)` | `—` |
| `show()` | `—` |

**Factory:** `TextDraw.create(int, int, string) -> TextDraw`

## `Vehicle`

### Fields

| Field | Type | Access |
|---|---|---|
| `angle` | `float` | read/write |
| `health` | `float` | read/write |
| `id` | `int` | read |
| `model` | `int` | read |
| `x` | `float` | read |
| `y` | `float` | read |
| `z` | `float` | read |

### Methods

| Method | Returns |
|---|---|
| `destroy()` | `—` |
| `repair()` | `—` |
| `set_color(int, int)` | `—` |
| `set_health(float)` | `—` |
| `set_number_plate(string)` | `—` |
| `set_position(float, float, float)` | `—` |

**Factory:** `Vehicle.create(int, float, float, float, float, int, int) -> Vehicle`

## `server` (runtime methods)

| Method | Returns |
|---|---|
| `server.disable_interior_enter_exits()` | `—` |
| `server.game_mode_exit()` | `—` |
| `server.get_gravity()` | `float` |
| `server.get_max_players()` | `int` |
| `server.get_player_count()` | `int` |
| `server.log(string)` | `—` |
| `server.send_rcon(string)` | `—` |
| `server.set_gamemode_text(string)` | `—` |
| `server.set_gravity(float)` | `—` |
| `server.set_team_count(int)` | `—` |
| `server.set_weather(int)` | `—` |
| `server.set_world_time(int)` | `—` |
| `server.show_name_tags(bool)` | `—` |
| `server.show_player_markers(int)` | `—` |

## Namespace helpers

| Call | Maps to |
|---|---|
| `player.add_class(int, float, float, float, float, int, int, int, int, int, int)` | `sa.AddPlayerClass` |
| `player.add_class_ex(int, int, float, float, float, float, int, int, int, int, int, int)` | `sa.AddPlayerClassEx` |
| `server.set_gamemode_text(string)` | `sa.SetGameModeText` |
| `server.set_weather(int)` | `sa.SetWeather` |
| `server.set_world_time(int)` | `sa.SetWorldTime` |

## Native index

498 natives:

```
AddCharModel, AddPlayerClass, AddPlayerClassEx, AddSimpleModel
AddSimpleModelTimed, AddStaticPickup, AddStaticVehicle, AddStaticVehicleEx
AddVehicleComponent, AllowAdminTeleport, AllowInteriorWeapons, AllowPlayerTeleport
ApplyActorAnimation, ApplyAnimation, ApplyDynamicActorAnimation, ApplyPlayerAnimation
Attach3DTextLabelToPlayer, Attach3DTextLabelToVehicle, AttachCameraToObject, AttachCameraToPlayerObject
AttachDynamicObjectToPlayer, AttachDynamicObjectToVehicle, AttachObjectToObject, AttachObjectToPlayer
AttachObjectToVehicle, AttachPlayerObjectToPlayer, AttachPlayerObjectToVehicle, AttachTrailerToVehicle
Ban, BanEx, BanPlayer, BlockIpAddress
CallLocalFunction, CallRemoteFunction, CancelEdit, CancelSelectTextDraw
ChangeVehicleColor, ChangeVehiclePaintjob, ClearActorAnimation, ClearActorAnimations
ClearAnimations, ClearDynamicActorAnimations, ClearPlayerAnimation, ConnectNPC
Create3DTextLabel, Create3DTextLabelAttachedToPlayer, Create3DTextLabelAttachedToVehicle, CreateActor
CreateDynamic3DTextLabel, CreateDynamicActor, CreateDynamicCP, CreateDynamicCircle
CreateDynamicMapIcon, CreateDynamicObject, CreateDynamicPickup, CreateDynamicRaceCP
CreateDynamicRectangle, CreateExplosion, CreateExplosionForPlayer, CreateObject
CreatePickup, CreatePlayer3DTextLabel, CreatePlayerObject, CreateVehicle
Delete3DTextLabel, DeletePVar, DeletePlayer3DTextLabel, DeleteSVar
DestroyActor, DestroyDynamic3DTextLabel, DestroyDynamicActor, DestroyDynamicArea
DestroyDynamicCP, DestroyDynamicMapIcon, DestroyDynamicObject, DestroyDynamicPickup
DestroyDynamicRaceCP, DestroyObject, DestroyPickup, DestroyPlayerObject
DestroyVehicle, DetachTrailerFromVehicle, DisableInteriorEnterExits, DisableNameTagLOS
DisablePlayerCheckpoint, DisablePlayerRaceCheckpoint, DisableRemoteVehicleCollisions, EditAttachedObject
EditDynamicObject, EditObject, EditPlayerObject, EnablePlayerCameraTarget
EnableStuntBonusForAll, EnableStuntBonusForPlayer, EnableTirePopping, EnableVehicleFriendlyFire
EnableZoneNames, FindModelFileNameFromCRC, FindTextureFileNameFromCRC, ForceClassSelection
GameModeExit, GameTextForAll, GameTextForPlayer, GangZoneCreate
GangZoneDestroy, GangZoneFlashForAll, GangZoneFlashForPlayer, GangZoneHideForAll
GangZoneHideForPlayer, GangZoneShowForAll, GangZoneShowForPlayer, GangZoneStopFlashForAll
GangZoneStopFlashForPlayer, GetActorFacingAngle, GetActorHealth, GetActorPoolSize
GetActorPos, GetActorVirtualWorld, GetAnimationName, GetConsoleVarAsBool
GetConsoleVarAsInt, GetConsoleVarAsString, GetDistanceBetweenPlayers, GetDynamicObjectPos
GetDynamicObjectRot, GetGravity, GetMaxPlayers, GetNetworkStats
GetObjectModel, GetObjectPos, GetObjectRot, GetPVarFloat
GetPVarInt, GetPVarNameAtIndex, GetPVarString, GetPVarType
GetPVarsUpperIndex, GetPlayerAmmo, GetPlayerAnimationIndex, GetPlayerArmour
GetPlayerCameraAspectRatio, GetPlayerCameraFrontVector, GetPlayerCameraMode, GetPlayerCameraPos
GetPlayerCameraTargetActor, GetPlayerCameraTargetObject, GetPlayerCameraTargetPlayer, GetPlayerCameraTargetVehicle
GetPlayerCameraZoom, GetPlayerColor, GetPlayerCustomSkin, GetPlayerDistanceFromPoint
GetPlayerDrunkLevel, GetPlayerFacingAngle, GetPlayerFightingStyle, GetPlayerHealth
GetPlayerInterior, GetPlayerIp, GetPlayerKeys, GetPlayerLastShotVectors
GetPlayerMoney, GetPlayerNetworkStats, GetPlayerObjectModel, GetPlayerObjectPos
GetPlayerObjectRot, GetPlayerPing, GetPlayerPoolSize, GetPlayerPos
GetPlayerScore, GetPlayerSkin, GetPlayerSpecialAction, GetPlayerState
GetPlayerSurfingObjectID, GetPlayerSurfingVehicleID, GetPlayerTargetActor, GetPlayerTargetPlayer
GetPlayerTeam, GetPlayerTime, GetPlayerVehicleID, GetPlayerVehicleSeat
GetPlayerVelocity, GetPlayerVersion, GetPlayerVirtualWorld, GetPlayerWantedLevel
GetPlayerWeapon, GetPlayerWeaponData, GetPlayerWeaponState, GetSVarFloat
GetSVarInt, GetSVarNameAtIndex, GetSVarString, GetSVarType
GetSVarsUpperIndex, GetServerTickRate, GetServerVarAsBool, GetServerVarAsInt
GetServerVarAsString, GetTickCount, GetVehicleComponentInSlot, GetVehicleComponentType
GetVehicleDamageStatus, GetVehicleDistanceFromPoint, GetVehicleHealth, GetVehicleModel
GetVehicleModelInfo, GetVehicleParamsCarDoors, GetVehicleParamsCarWindows, GetVehicleParamsEx
GetVehicleParamsSirenState, GetVehiclePoolSize, GetVehiclePos, GetVehicleRotationQuat
GetVehicleTrailer, GetVehicleVelocity, GetVehicleVirtualWorld, GetVehicleZAngle
GetWeaponName, GetWorldTime, GivePlayerMoney, GivePlayerWeapon
HidePlayerDialog, InterpolateCameraLookAt, InterpolateCameraPos, IsActorInvulnerable
IsActorStreamedIn, IsObjectMoving, IsPlayerAdmin, IsPlayerAttachedObjectSlotUsed
IsPlayerConnected, IsPlayerInAnyVehicle, IsPlayerInCheckpoint, IsPlayerInDynamicArea
IsPlayerInDynamicCP, IsPlayerInDynamicRaceCP, IsPlayerInRaceCheckpoint, IsPlayerInRangeOfPoint
IsPlayerInVehicle, IsPlayerNPC, IsPlayerObjectMoving, IsPlayerStreamedIn
IsTrailerAttachedToVehicle, IsValidActor, IsValidDynamic3DTextLabel, IsValidDynamicActor
IsValidDynamicArea, IsValidDynamicMapIcon, IsValidDynamicObject, IsValidDynamicPickup
IsValidObject, IsValidPlayerObject, IsValidVehicle, IsVehicleStreamedIn
Kick, KickPlayer, KillTimer, LimitGlobalChatRadius
LimitPlayerMarkerRadius, LinkVehicleToInterior, Log, ManualVehicleEngineAndLights
MoveDynamicObject, MoveObject, MovePlayerObject, NetStats_BytesReceived
NetStats_BytesSent, NetStats_ConnectionStatus, NetStats_GetConnectedTime, NetStats_GetIpPort
NetStats_MessagesReceived, NetStats_MessagesRecvPerSecond, NetStats_MessagesSent, NetStats_PacketLossPercent
PlayAudioStreamForPlayer, PlayCrimeReportForPlayer, PlayerCount, PlayerName
PlayerPlaySound, PlayerSpectatePlayer, PlayerSpectateVehicle, PlayerTextDrawAlignment
PlayerTextDrawBackgroundColor, PlayerTextDrawBoxColor, PlayerTextDrawColor, PlayerTextDrawCreate
PlayerTextDrawDestroy, PlayerTextDrawFont, PlayerTextDrawHide, PlayerTextDrawLetterSize
PlayerTextDrawSetOutline, PlayerTextDrawSetPreviewModel, PlayerTextDrawSetPreviewRot, PlayerTextDrawSetPreviewVehCol
PlayerTextDrawSetProportional, PlayerTextDrawSetSelectable, PlayerTextDrawSetShadow, PlayerTextDrawSetString
PlayerTextDrawShow, PlayerTextDrawTextSize, PlayerTextDrawUseBox, PutPlayerInVehicle
RedirectDownload, RemoveBuildingForPlayer, RemovePlayerAttachedObject, RemovePlayerFromVehicle
RemovePlayerMapIcon, RemoveVehicleComponent, RepairVehicle, ResetPlayerMoney
ResetPlayerWeapons, SHA256_PassHash, SelectObject, SelectTextDraw
SendClientCheck, SendClientMessage, SendClientMessageToAll, SendDeathMessage
SendDeathMessageToPlayer, SendPlayerMessageToAll, SendPlayerMessageToPlayer, SendRconCommand
SetActorFacingAngle, SetActorHealth, SetActorInvulnerable, SetActorPos
SetActorVirtualWorld, SetCameraBehindPlayer, SetDeathDropAmount, SetDynamicActorFacingAngle
SetDynamicActorPos, SetDynamicObjectMaterial, SetDynamicObjectMaterialText, SetDynamicObjectPos
SetDynamicObjectRot, SetGameModeText, SetGravity, SetNameTagDrawDistance
SetObjectMaterial, SetObjectMaterialText, SetObjectNoCameraCol, SetObjectPos
SetObjectRot, SetObjectRotation, SetObjectsDefaultCameraCol, SetPVarFloat
SetPVarInt, SetPVarString, SetPlayerAdmin, SetPlayerAmmo
SetPlayerArmedWeapon, SetPlayerArmour, SetPlayerAttachedObject, SetPlayerCameraBehindPlayer
SetPlayerCameraLookAt, SetPlayerCameraPos, SetPlayerChatBubble, SetPlayerCheckpoint
SetPlayerColor, SetPlayerDrunkLevel, SetPlayerFacingAngle, SetPlayerFightingStyle
SetPlayerHealth, SetPlayerInterior, SetPlayerMapIcon, SetPlayerMarkerForPlayer
SetPlayerName, SetPlayerObjectMaterial, SetPlayerObjectMaterialText, SetPlayerObjectNoCameraCol
SetPlayerObjectPos, SetPlayerObjectRot, SetPlayerPos, SetPlayerPosFindZ
SetPlayerRaceCheckpoint, SetPlayerScore, SetPlayerShopName, SetPlayerSkillLevel
SetPlayerSkin, SetPlayerSpecialAction, SetPlayerTeam, SetPlayerTime
SetPlayerVelocity, SetPlayerVirtualWorld, SetPlayerWantedLevel, SetPlayerWeather
SetPlayerWorldBounds, SetSVarFloat, SetSVarInt, SetSVarString
SetSpawnInfo, SetTeamCount, SetTimer, SetTimerEx
SetVehicleAngularVelocity, SetVehicleDamageStatus, SetVehicleHealth, SetVehicleNumberPlate
SetVehicleParamsCarDoors, SetVehicleParamsCarWindows, SetVehicleParamsEx, SetVehicleParamsForPlayer
SetVehiclePos, SetVehicleToRespawn, SetVehicleVelocity, SetVehicleVirtualWorld
SetVehicleZAngle, SetWeather, SetWorldTime, ShowNameTags
ShowPlayerDialog, ShowPlayerMarkers, ShowPlayerNameTagForPlayer, SpawnPlayer
StartRecordingPlayerData, StopAudioStreamForPlayer, StopDynamicObject, StopObject
StopPlayerObject, StopRecordingPlayerData, Streamer_CountItems, Streamer_DestroyAllVisibleItems
Streamer_GetArrayData, Streamer_MaxItems, Streamer_SetArrayData, Streamer_SetIntData
Streamer_SetRadiusMultiplier, Streamer_SetVisibleItems, Streamer_ToggleIdleUpdate, Streamer_Update
Streamer_UpdateEx, TextDrawAlignment, TextDrawBackgroundColor, TextDrawBoxColor
TextDrawColor, TextDrawCreate, TextDrawDestroy, TextDrawFont
TextDrawHideForAll, TextDrawHideForPlayer, TextDrawLetterSize, TextDrawSetOutline
TextDrawSetPreviewModel, TextDrawSetPreviewRot, TextDrawSetPreviewVehCol, TextDrawSetProportional
TextDrawSetSelectable, TextDrawSetShadow, TextDrawSetString, TextDrawShowForAll
TextDrawShowForPlayer, TextDrawTextSize, TextDrawUseBox, TogglePlayerClock
TogglePlayerControllable, TogglePlayerSpectating, TogglePlayerWidescreen, UnBlockIpAddress
Update3DTextLabelText, UpdateDynamic3DTextLabelText, UpdatePlayer3DTextLabelText, UpdateVehicleDamageStatus
UsePlayerPedAnims, VectorSize, cache_delete, cache_get_field_count
cache_get_row_count, cache_get_value_index_int, cache_get_value_name, cache_get_value_name_float
cache_get_value_name_int, cache_insert_id, format, gpci
hash_password, mysql_close, mysql_errno, mysql_format
mysql_open, mysql_pquery, mysql_tquery, random_token
sqlite_close, sqlite_exec, sqlite_exec_async, sqlite_open
sqlite_query, sqlite_query_async, sscanf, strcat
strcmp, strdel, strfind, strins
strlen, strmid, strpack, strunpack
strval, verify_password, 
```
