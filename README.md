# Lua API Documentation

This document outlines the Lua API for interacting with game entities, weapons, input commands, global variables, configuration variables, events, beams, networking, and rendering utilities. The API is organized into enums, usertypes, tables, and global properties with their respective methods and properties.

## Enums

### Hitboxes
- `HEAD`: number - Head hitbox.
- `NECK`: number - Neck hitbox.
- `PELVIS`: number - Pelvis hitbox.
- `STOMACH`: number - Stomach hitbox.
- `CHEST`: number - Chest hitbox.
- `RIGHT_THIGH`: number - Right thigh hitbox.
- `LEFT_THIGH`: number - Left thigh hitbox.
- `RIGHT_CALF`: number - Right calf hitbox.
- `LEFT_CALF`: number - Left calf hitbox.
- `RIGHT_FOOT`: number - Right foot hitbox.
- `LEFT_FOOT`: number - Left foot hitbox.
- `RIGHT_HAND`: number - Right hand hitbox.
- `LEFT_HAND`: number - Left hand hitbox.
- `RIGHT_UPPER_ARM`: number - Right upper arm hitbox.
- `RIGHT_FOREARM`: number - Right forearm hitbox.
- `LEFT_UPPER_ARM`: number - Left upper arm hitbox.
- `LEFT_FOREARM`: number - Left forearm hitbox.

### Buttons
- `IN_ATTACK`: number - Primary attack button.
- `IN_JUMP`: number - Jump button.
- `IN_DUCK`: number - Duck button.
- `IN_FORWARD`: number - Move forward button.
- `IN_BACK`: number - Move backward button.
- `IN_USE`: number - Use button.
- `IN_CANCEL`: number - Cancel button.
- `IN_LEFT`: number - Look left button.
- `IN_RIGHT`: number - Look right button.
- `IN_MOVELEFT`: number - Move left button.
- `IN_MOVERIGHT`: number - Move right button.
- `IN_ATTACK2`: number - Secondary attack button.
- `IN_RUN`: number - Run button.
- `IN_RELOAD`: number - Reload button.
- `IN_ALT1`: number - Alternate button 1.
- `IN_ALT2`: number - Alternate button 2.
- `IN_SCORE`: number - Show scoreboard button.
- `IN_SPEED`: number - Speed toggle button.
- `IN_WALK`: number - Walk button.
- `IN_ZOOM`: number - Zoom button.
- `IN_WEAPON1`: number - Weapon slot 1 button.
- `IN_WEAPON2`: number - Weapon slot 2 button.
- `IN_BULLRUSH`: number - Bullrush button.
- `IN_GRENADE1`: number - Grenade 1 button.
- `IN_GRENADE2`: number - Grenade 2 button.
- `IN_LOOKSPIN`: number - Look spin button.

### Contents
- `CONTENTS_EMPTY`: number - Empty space.
- `CONTENTS_SOLID`: number - Solid surface.
- `CONTENTS_WINDOW`: number - Window surface.
- `CONTENTS_AUX`: number - Auxiliary surface.
- `CONTENTS_GRATE`: number - Grate surface.
- `CONTENTS_SLIME`: number - Slime surface.
- `CONTENTS_WATER`: number - Water surface.
- `CONTENTS_MIST`: number - Mist surface.
- `CONTENTS_OPAQUE`: number - Opaque surface.
- `LAST_VISIBLE_CONTENTS`: number - Last visible content flag.
- `ALL_VISIBLE_CONTENTS`: number - All visible content flags combined.
- `CONTENTS_TESTFOGVOLUME`: number - Fog volume test flag.
- `CONTENTS_UNUSED5`: number - Unused content flag 5.
- `CONTENTS_UNUSED6`: number - Unused content flag 6.
- `CONTENTS_TEAM1`: number - Team 1 content flag.
- `CONTENTS_TEAM2`: number - Team 2 content flag.
- `CONTENTS_IGNORE_NODRAW_OPAQUE`: number - Ignore nodraw opaque flag.
- `CONTENTS_MOVEABLE`: number - Moveable object flag.
- `CONTENTS_AREAPORTAL`: number - Area portal flag.
- `CONTENTS_PLAYERCLIP`: number - Player clip flag.
- `CONTENTS_MONSTERCLIP`: number - Monster clip flag.
- `CONTENTS_CURRENT_0`: number - Current direction 0 degrees.
- `CONTENTS_CURRENT_90`: number - Current direction 90 degrees.
- `CONTENTS_CURRENT_180`: number - Current direction 180 degrees.
- `CONTENTS_CURRENT_270`: number - Current direction 270 degrees.
- `CONTENTS_CURRENT_UP`: number - Current direction upward.
- `CONTENTS_CURRENT_DOWN`: number - Current direction downward.
- `CONTENTS_ORIGIN`: number - Origin point flag.
- `CONTENTS_MONSTER`: number - Monster entity flag.
- `CONTENTS_DEBRIS`: number - Debris flag.
- `CONTENTS_DETAIL`: number - Detail geometry flag.
- `CONTENTS_TRANSLUCENT`: number - Translucent surface flag.
- `CONTENTS_LADDER`: number - Ladder surface flag.
- `CONTENTS_HITBOX`: number - Hitbox flag.

### Surface Flags
- `SURF_LIGHT`: number - Surface emits light.
- `SURF_SLICK`: number - Slippery surface.
- `SURF_SKY`: number - Skybox surface.
- `SURF_WARP`: number - Teleport surface.
- `SURF_TRANS`: number - Transparent surface.
- `SURF_WET`: number - Wet surface.
- `SURF_TRIGGER`: number - Trigger surface.
- `SURF_NODRAW`: number - Non-rendered surface.
- `SURF_HINT`: number - Hint surface for AI.
- `SURF_SKIP`: number - Skipped surface.
- `SURF_NOLIGHT`: number - No light surface.
- `SURF_BUMPLIGHT`: number - Bump-mapped light surface.
- `SURF_NOSHADOWS`: number - No shadows surface.
- `SURF_NODECALS`: number - No decals surface.
- `SURF_NOCHOP`: number - No chop surface.
- `SURF_HITBOX`: number - Hitbox surface.

### Masks
- `MASK_ALL`: number - All collision mask.
- `MASK_SOLID`: number - Solid objects mask.
- `MASK_PLAYERSOLID`: number - Player solid mask.
- `MASK_NPCSOLID`: number - NPC solid mask.
- `MASK_WATER`: number - Water mask.
- `MASK_OPAQUE`: number - Opaque objects mask.
- `MASK_OPAQUE_AND_NPCS`: number - Opaque and NPC mask.
- `MASK_VISIBLE`: number - Visible objects mask.
- `MASK_VISIBLE_AND_NPCS`: number - Visible and NPC mask.
- `MASK_SHOT`: number - Shot trace mask.
- `MASK_SHOT_HULL`: number - Shot hull trace mask.
- `MASK_SHOT_HULL_EX`: number - Extended shot hull mask.
- `MASK_SHOT_PORTAL`: number - Portal shot mask.
- `MASK_SOLID_BRUSHONLY`: number - Solid brush-only mask.
- `MASK_PLAYERSOLID_BRUSHONLY`: number - Player solid brush-only mask.
- `MASK_NPCSOLID_BRUSHONLY`: number - NPC solid brush-only mask.
- `MASK_NPCWORLDSTATIC`: number - NPC world static mask.
- `MASK_SPLITAREAPORTAL`: number - Split area portal mask.
- `MASK_CURRENT`: number - Current flow mask.

### Network Flow
- `FLOW_OUTGOING`: number - Represents outgoing network flow.
- `FLOW_INCOMING`: number - Represents incoming network flow.
- `MAX_FLOWS`: number - Maximum number of network flows.

### Keybind Types
- `BIND_TYPE_TOGGLE`: number - Keybind toggles between on and off states.
- `BIND_TYPE_HOLD`: number - Keybind is active only while held.

## Usertypes

### CGlobalVarsBase
Represents global game variables, providing access to timing and network-related properties.

**Properties:**
- `realTime`: number - Real-world time since the game started.
- `frameCount`: number - Total number of frames rendered.
- `absoluteFrameTime`: number - Time taken for the current frame, including simulation.
- `curTime`: number - Current game time.
- `frameTime`: number - Time taken for the current frame’s simulation.
- `maxClients`: number - Maximum number of clients allowed on the server.
- `tickCount`: number - Total number of server ticks.
- `intervalPerTick`: number - Time duration of a single server tick.
- `interpolationAmount`: number - Amount of interpolation applied for rendering.
- `simTicksThisFrame`: number - Number of simulation ticks in the current frame.
- `networkProtocol`: number - Network protocol version.
- `isClient`: boolean - Whether the game is running on the client side.
- `timestampNetworkingBase`: number - Base timestamp for networking.
- `timestampRandomizeWindow`: number - Window for randomizing network timestamps.

### vector
Represents a 3D vector with x, y, z components.

**Constructors:**
- `vector()`: Creates a zero vector.
- `vector(x: number, y: number, z: number)`: Creates a vector with specified coordinates.

**Properties:**
- `x`: number
- `y`: number
- `z`: number

**Methods:**
- `isZero(): boolean` - Checks if the vector is zero.
- `length(): number` - Returns the vector's length.
- `length2D(): number` - Returns the 2D length (x, y).
- `length2DSqr(): number` - Returns the squared 2D length.
- `lengthSqr(): number` - Returns the squared length.
- `cross(other: vector): vector` - Computes the cross product with another vector.
- `normalize(): number` - Normalizes the vector and returns its length.
- `normalized(): vector` - Returns a normalized copy of the vector.
- `clear(): void` - Sets the vector to zero.
- `withinAABox(min: vector, max: vector): boolean` - Checks if the vector is within an axis-aligned bounding box.
- `dot(other: vector | table<number, number, number>): number` - Computes the dot product with another vector or a table of three numbers.

**Operators:**
- `+ (vector)`: Adds two vectors.
- `- (vector)`: Subtracts another vector.
- `* (number | vector)`: Multiplies by a scalar or component-wise with another vector.
- `/ (number | vector)`: Divides by a scalar or component-wise by another vector.

**Global Function:**
- `Vector(x: number, y: number, z: number): vector` - Creates a new vector.

### CCSWeaponInfo
Represents properties and characteristics of a weapon in the game.

**Properties:**
- `ammoType`: number - The type of ammunition used by the weapon.
- `maxSpeed`: number - The maximum movement speed when holding the weapon.
- `weaponType`: number - The type of weapon (e.g., pistol, rifle).
- `armorRatio`: number - The armor penetration ratio.
- `penetration`: number - The number of surfaces the weapon can penetrate.
- `damage`: number - The base damage dealt by the weapon.
- `range`: number - The maximum range of the weapon.
- `rangeModifier`: number - The damage falloff modifier based on range.
- `bullets`: number - The number of bullets fired per shot.
- `cycleTime`: number - The time between consecutive shots.
- `accuracyQuadratic`: boolean - Whether the weapon uses quadratic accuracy calculations.
- `accuracyDivisor`: number - The divisor used in accuracy calculations.
- `accuracyOffset`: number - The offset used in accuracy calculations.
- `maxInaccuracy`: number - The maximum inaccuracy value.
- `timeToIdleAfterFire`: number - The time before the weapon returns to idle after firing.
- `idleInterval`: number - The interval for idle animations.
- `weaponPrice`: number - The in-game price of the weapon.

### CBaseHandle
Represents a handle to a game entity, typically used to reference entities like weapons, players, or other objects.

**Methods:**
- `get(): IClientEntity | nil` - Retrieves the entity associated with this handle. Returns `nil` if the handle is invalid.

### C_BaseCombatWeapon
Inherits from `IClientEntity`. Represents a combat weapon in the game.

**Methods:**
- `getName(): string` - Returns the name of the weapon.
- `getWeaponID(): number` - Returns the weapon's unique ID.
- `getCSWpnData(): CCSWeaponInfo` - Returns the weapon’s configuration data.
- `getNetvars(): WeaponNetvars` - Returns the weapon’s network variables.

### IClientEntity
Represents a game entity.

**Properties:**
- `isAlive`: boolean - Whether the entity is alive.
- `absVelocity`: vector - Absolute velocity.
- `absOrigin`: vector - Absolute origin.
- `absAngles`: vector - Absolute angles.

**Methods:**
- `getField(field: string): any` - Retrieves a field value by name.
- `getNetvars(): EntityNetvars` - Returns the entity’s network variables.

### WeaponNetvars
Inherits from `EntityNetvars`. Represents network variables specific to weapons, including grenades and specific weapon types like Glock, FAMAS, M4A1, and USP.

**Properties:**
- `nextPrimaryAttack`: number - Time until the next primary attack is available.
- `nextSecondaryAttack`: number - Time until the next secondary attack is available.
- `timeWeaponIdle`: number - Time until the weapon enters the idle state.
- `throwTime`: number - Time when a grenade is thrown.
- `pinPulled`: boolean - Whether the grenade pin has been pulled.
- `redraw`: boolean - Whether the grenade requires a redraw.
- `clip1`: number - Number of bullets in the primary magazine.
- `primaryAmmoType`: number - Type of primary ammunition used by the weapon.
- `owner`: CBaseHandle - Handle to the entity owning the weapon.
- `initialVelocity`: vector - Initial velocity of a grenade projectile.
- `burstModeGlock`: boolean - Whether burst mode is enabled for the Glock.
- `burstModeFamas`: boolean - Whether burst mode is enabled for the FAMAS.
- `silencerOnM4A1`: boolean - Whether the silencer is attached to the M4A1.
- `silencerOnUSP`: boolean - Whether the silencer is attached to the USP.

### EntityNetvars
Represents network variables for game entities.

**Properties:**
- `vecOrigin`: vector - Entity’s origin position.
- `vecMins`: vector - Minimum bounds of the entity’s collision box.
- `vecMaxs`: vector - Maximum bounds of the entity’s collision box.
- `renderMode`: number - Rendering mode of the entity.
- `modelIndex`: number - Index of the entity’s model.
- `renderFX`: number - Render effects applied to the entity.
- `angRotation`: vector - Entity’s rotation angles.
- `vecOldOrigin`: vector - Previous origin position.
- `teamNum`: number - Team number of the entity.
- `simulationTime`: number - Time of the last simulation update.
- `ownerEntity`: CBaseHandle - Handle to the entity’s owner.
- `oldSimulationTime`: number - Previous simulation time.
- `collisionGroup`: number - Collision group of the entity.
- `movetype`: number - Movement type of the entity.
- `takeDamage`: number - Damage handling type.
- `coordinateFrame`: table - 3x4 transformation matrix for the entity.
- `skin`: number - Skin index for the entity’s model.
- `body`: number - Body group index.
- `hitboxSet`: number - Hitbox set index.
- `cycle`: number - Animation cycle.
- `sequence`: number - Animation sequence.
- `clientSideAnimation`: boolean - Whether client-side animations are enabled.
- `playbackRate`: number - Animation playback rate.
- `flexWeight`: table - Array of flex weights.
- `viewtarget`: vector - View target position.
- `animTime`: number - Animation time.
- `nextAttack`: number - Time until the next attack is available.
- `activeWeapon`: CBaseHandle - Handle to the active weapon.
- `lastWeapon`: CBaseHandle - Handle to the last used weapon.
- `waterLevel`: number - Water level the entity is in.
- `viewOffset`: vector - View offset for the entity.
- `deadflag`: boolean - Whether the entity is dead.
- `flags`: number - Entity flags.
- `health`: number - Health value.
- `effects`: number - Visual effects flags.
- `tickBase`: number - Tick base for prediction.
- `lifestate`: number - Life state of the entity.
- `punchAngle`: vector - Recoil punch angle.
- `punchAngleVel`: vector - Recoil punch angle velocity.
- `velocity`: vector - Entity’s velocity.
- `baseVelocity`: vector - Base velocity for movement.
- `fov`: number - Field of view.
- `stamina`: number - Stamina value.
- `maxspeed`: number - Maximum movement speed.
- `observerTarget`: CBaseHandle - Handle to the observer target.
- `groundEntity`: CBaseHandle - Handle to the ground entity.
- `observerMode`: number - Observer mode.
- `fallVelocity`: number - Velocity of falling.
- `viewModel`: CBaseHandle - Handle to the view model.
- `eyeAngles`: vector - Eye angles for the player.
- `account`: number - Player’s account balance.
- `armorValue`: number - Armor value.
- `flashMaxAlpha`: number - Maximum alpha for flashbang effect.
- `flashDuration`: number - Duration of flashbang effect.
- `hasHelmet`: boolean - Whether the player has a helmet.
- `isDefusing`: boolean - Whether the player is defusing a bomb.
- `hasDefuser`: boolean - Whether the player has a defuser kit.
- `shotsFired`: number - Number of shots fired.
- `velocityModifier`: number - Velocity modifier.
- `ducked`: boolean - Whether the player is ducked.
- `ducktime`: number - Time spent ducking.
- `allowAutoMovement`: boolean - Whether automatic movement is allowed.
- `ducking`: boolean - Whether the player is in the process of ducking.
- `inBuyZone`: boolean - Whether the player is in a buy zone.
- `lastZoom`: number - Last zoom level.
- `resumeZoom`: boolean - Whether to resume zoom.
- `cycleLatch`: number - Animation cycle latch.
- `poseParameter`: table - Array of 5 pose parameters.
- `encodedController`: table - Array of encoded controller values.
- `myWeapons`: table - Array of 8 CBaseHandle values for weapons.
- `ammo`: table - Array of 32 ammo counts.

### CUserCmd
Represents a user command for input handling.

**Properties:**
- `commandNumber`: number - Command sequence number.
- `tickCount`: number - Tick count for the command.
- `buttons`: number - Button states (bitmask).
- `weaponSelect`: number - Selected weapon index.
- `weaponSubType`: number - Weapon subtype.
- `randomSeed`: number - Random seed for prediction.
- `forwardMove`: number - Forward movement input.
- `sideMove`: number - Side movement input.
- `upMove`: number - Vertical movement input.
- `viewAngles`: vector - View angles for the command.
- `impulse`: number - Impulse command.
- `mousedx`: number - Mouse X delta.
- `mousedy`: number - Mouse Y delta.
- `hasBeenPredicted`: boolean - Whether the command has been predicted.

### CKeybind
Represents a keybind configuration for toggling or holding actions.

**Methods:**
- `active(): boolean` - Checks if the keybind is currently active.
- `setKeyCode(key: number): void` - Sets the key code for the keybind.
- `setType(type: number): void` - Sets the keybind type (`BIND_TYPE_TOGGLE` or `BIND_TYPE_HOLD`).
- `toggle(): void` - Toggles the keybind’s state.
- `setValue(value: string): void` - Sets the keybind’s value from a string.
- `getValue(): string` - Gets the keybind’s value as a string.

### CConfigVariable
Represents a configuration variable with keybind support.

**Methods:**
- `set(value: any): void` - Sets the variable’s value.
- `get(): string` - Gets the variable’s value as a string.
- `addDisableVariable(var: CConfigVariable): void` - Adds a variable whose active keybind disables this variable’s keybind.
- `getKeybind(): CKeybind` - Retrieves the associated keybind.

### IGameEvent
Represents a game event.

**Methods:**
- `getEventName(): string` - Gets the event name.
- `getInt(key: string): number` - Gets an integer value for the specified key.
- `getFloat(key: string): number` - Gets a float value for the specified key.
- `getBool(key: string): boolean` - Gets a boolean value for the specified key.
- `getString(key: string): string` - Gets a string value for the specified key.
- `setBool(key: string, value: boolean): void` - Sets a boolean value for the specified key.
- `setFloat(key: string, value: number): void` - Sets a float value for the specified key.
- `setInt(key: string, value: number): void` - Sets an integer value for the specified key.

### Beam_t
Represents a beam entity in the game.

### BeamInfo_t
Represents the configuration for creating a beam.

**Properties:**
- `type`: number - Type of the beam.
- `startEnt`: IClientEntity | nil - Starting entity for the beam.
- `startAttachment`: number - Attachment point on the start entity.
- `endEnt`: IClientEntity | nil - Ending entity for the beam.
- `endAttachment`: number - Attachment point on the end entity.
- `vecStart`: vector - Starting position of the beam.
- `vecEnd`: vector - Ending position of the beam.
- `modelIndex`: number - Index of the beam’s model.
- `modelName`: string | nil - Name of the beam’s model.
- `haloIndex`: number - Index of the halo effect.
- `haloName`: string | nil - Name of the halo effect.
- `haloScale`: number - Scale of the halo effect.
- `life`: number - Duration of the beam.
- `width`: number - Width of the beam.
- `endWidth`: number - Width at the end of the beam.
- `fadeLength`: number - Length over which the beam fades.
- `amplitude`: number - Amplitude of the beam’s oscillation.
- `brightness`: number - Brightness of the beam.
- `speed`: number - Speed of the beam’s animation.
- `startFrame`: number - Starting frame for the beam’s animation.
- `frameRate`: number - Frame rate of the beam’s animation.
- `red`: number - Red color component.
- `green`: number - Green color component.
- `blue`: number - Blue color component.
- `renderable`: boolean - Whether the beam is renderable.
- `segments`: number - Number of segments in the beam.
- `flags`: number - Beam flags.
- `vecCenter`: vector - Center position for ring beams.
- `startRadius`: number - Starting radius for ring beams.
- `endRadius`: number - Ending radius for ring beams.

### IViewRenderBeams
Manages rendering and manipulation of beams.

**Methods:**
- `clearBeams(): void` - Clears all beams.
- `createBeamEnts(beamInfo: BeamInfo_t): Beam_t | nil` - Creates a beam between two entities.
- `createBeamEntPoint(beamInfo: BeamInfo_t): Beam_t | nil` - Creates a beam from an entity to a point.
- `createBeamFollow(beamInfo: BeamInfo_t): Beam_t | nil` - Creates a beam that follows an entity.
- `createBeamRing(beamInfo: BeamInfo_t): Beam_t | nil` - Creates a ring-shaped beam between entities.
- `createBeamRingPoint(beamInfo: BeamInfo_t): Beam_t | nil` - Creates a ring-shaped beam at a point.
- `freeBeam(beam: Beam_t): void` - Frees a beam.
- `updateBeamInfo(beam: Beam_t, beamInfo: BeamInfo_t): void` - Updates a beam’s properties.
- `drawBeam(beam: Beam_t): void` - Draws a beam.

### surface_t
Represents a surface.

**Properties:**
- `name`: string - Surface name.
- `surfaceProps`: number - Surface properties.
- `flags`: number - Surface flags.

### plane
Represents a plane.

**Properties:**
- `normal`: vector - Plane normal vector.
- `dist`: number - Distance from origin along the normal.

### trace_t
Represents a trace result.

**Properties:**
- `fractionLeftSolid`: number - Fraction until leaving solid.
- `surface`: surface_t - Surface hit.
- `hitGroup`: number - Hit group impacted.
- `physicsBone`: number - Physics bone hit.
- `ent`: IClientEntity - Entity hit.
- `hitbox`: number - Hitbox index.
- `startPos`: vector - Trace start position.
- `endPos`: vector - Trace end position.
- `plane`: plane - Plane of the surface hit.
- `fraction`: number - Fraction of the trace completed.
- `contents`: number - Contents hit.
- `dispFlags`: number - Displacement flags.
- `allSolid`: boolean - Whether the trace was entirely in solid.
- `startSolid`: boolean - Whether the trace started in solid.

### ITraceFilter
Base type for trace filters.

### CTraceFilter
Inherits from `ITraceFilter`.

### CTraceFilterSimple
Inherits from `CTraceFilter`.

**Constructor:**
- `CTraceFilterSimple(ent: IClientEntity)`: Creates a trace filter for a single entity.

**Global Function:**
- `traceFilterSimple(ent: IClientEntity): CTraceFilterSimple` - Creates a trace filter for a single entity.

### CTraceFilterSkipTwoEntities
Inherits from `CTraceFilterSimple`.

**Constructor:**
- `CTraceFilterSkipTwoEntities(ent1: IClientEntity, ent2: IClientEntity, collision_group: number)`: Creates a trace filter ignoring two entities with a specified collision group.

**Global Function:**
- `traceFilterSkipTwoEntities(ent1: IClientEntity, ent2: IClientEntity): CTraceFilterSkipTwoEntities` - Creates a trace filter ignoring two entities.

### IInput
Manages input-related properties and user commands.

**Properties:**
- `cameraInThirdPerson`: boolean - Whether the camera is in third-person mode.
- `cameraOffset`: vector - Offset of the camera in third-person mode.

**Methods:**
- `getUserCmd(commandNumber: number): CUserCmd | nil` - Retrieves the user command for the specified command number.

### ConVar
Inherits from `ConCommandBase`. Represents a console variable.

**Properties:**
- `parent`: ConVar - Parent console variable.
- `defaultValue`: string - Default value of the console variable.
- `strValue`: string - Current string value.
- `strLength`: number - Length of the string value.
- `flValue`: number - Current float value.
- `nValue`: number - Current integer value.
- `hasMin`: boolean - Whether the variable has a minimum value.
- `minVal`: number - Minimum value.
- `hasMax`: boolean - Whether the variable has a maximum value.
- `maxVal`: number - Maximum value.

### ICvar
Manages console variables.

**Methods:**
- `findVar(name: string): ConVar | nil` - Finds a console variable by name.

### INetChannel
Inherits from `INetChannelInfo`. Represents a network channel for communication.

**Methods:**
- `getAvgLatency(flow: number): number` - Gets the average latency for the specified flow (`FLOW_OUTGOING` or `FLOW_INCOMING`).
- `getLatency(flow: number): number` - Gets the current latency for the specified flow.
- `getAvgChoke(flow: number): number` - Gets the average choke for the specified flow.
- `getAvgLoss(flow: number): number` - Gets the average packet loss for the specified flow.
- `isTimingOut(): boolean` - Checks if the network channel is timing out.
- `getAddress(): string` - Gets the network address of the channel.

### IVEngineClient
Provides access to engine-related functionality.

**Methods:**
- `clientCmd(command: string): void` - Executes a client-side command.
- `isInGame(): boolean` - Checks if the client is in a game.
- `isConnected(): boolean` - Checks if the client is connected to a server.
- `setViewAngles(angles: vector): void` - Sets the view angles.
- `getViewAngles(): vector` - Gets the current view angles.
- `getLastTimeStamp(): number` - Gets the last timestamp.
- `conIsVisible(): boolean` - Checks if the console is visible.
- `getScreenSize(): table<number, number>` - Returns the screen size as `{width, height}`.
- `isPaused(): boolean` - Checks if the game is paused.
- `isTakingScreenshot(): boolean` - Checks if a screenshot is being taken.
- `isRecordingDemo(): boolean` - Checks if a demo is being recorded.
- `isPlayingDemo(): boolean` - Checks if a demo is being played.
- `getNetChannel(): INetChannel | nil` - Gets the current network channel.

### IPrediction
Manages prediction-related properties for client-side simulation.

**Properties:**
- `inPrediction`: boolean - Whether prediction is active.
- `firstTimePredicted`: boolean - Whether this is the first time prediction is run.
- `oldCLPredictValue`: boolean - Previous client prediction value.
- `previousStartFrame`: number - Previous start frame for prediction.
- `commandsPredicted`: number - Number of commands predicted.
- `serverCommandsAcknowledged`: number - Number of server commands acknowledged.
- `previousAckHadErrors`: boolean - Whether the previous acknowledgment had errors.
- `incomingPacketNumber`: number - Incoming packet number.
- `idealPitch`: number - Ideal pitch for the player.

## Tables

### callbacks
Collection of functions for registering event callbacks.

- `createMove(func: function): void` - Registers a callback for the create move event.
- `createMovePostPredict(func: function): void` - Registers a callback for post-prediction create move.
- `createMovePostRestore(func: function): void` - Registers a callback for post-restore create move.
- `onPresent(func: function): void` - Registers a callback for the present event.
- `onGameEvent(func: function): void` - Registers a callback for game events.
- `onLevelInit(func: function): void` - Registers a callback for level initialization (post-entity).
- `onLevelShutdown(func: function): void` - Registers a callback for level shutdown.

### entityList
Functions for accessing game entities.

- `getLocalPlayer(): IClientEntity` - Gets the local player entity.
- `getPlayer(index: number): IClientEntity` - Gets a player entity by index.
- `getEntityByHandle(handle: CBaseHandle): IClientEntity | nil` - Gets an entity by its handle. Returns `nil` if the handle is invalid.

### events
Functions for managing game event callbacks.

- `registerEvent(event: string, func: function): void` - Registers a function for a specific game event.

### netvars
Functions for accessing network variable offsets.

- `getFieldOffset(dataTable: string, fieldName: string): number` - Gets the offset of a field in a data table.

### cfg
Functions for accessing configuration variables and keybinds.

- `getVar(name: string): CConfigVariable` - Gets a configuration variable by name.
- `getActiveKeybinds(): table` - Returns a table of active keybinds with their names and states.

### imgui
Drawing and UI functions for rendering elements.

- `drawLine(p1: vector, p2: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void` - Draws a line between two points with specified color and thickness.
- `drawRect(p_min: vector, p_max: vector, r: number, g: number, b: number, a: number, rounding: number = 0.0, flags: number = 0, thickness: number = 1.0): void` - Draws a rectangle outline with optional rounding and flags.
- `drawRectFilled(p_min: vector, p_max: vector, r: number, g: number, b: number, a: number, rounding: number = 0.0, flags: number = 0): void` - Draws a filled rectangle with optional rounding and flags.
- `drawRectFilledMultiColor(p_min: vector, p_max: vector, r1: number, g1: number, b1: number, a1: number, r2: number, g2: number, b2: number, a2: number, r3: number, g3: number, b3: number, a3: number, r4: number, g4: number, b4: number, a4: number): void` - Draws a filled rectangle with gradient colors at each corner.
- `drawQuad(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void` - Draws a quadrilateral outline.
- `drawQuadFilled(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number): void` - Draws a filled quadrilateral.
- `drawTriangle(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void` - Draws a triangle outline.
- `drawTriangleFilled(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number): void` - Draws a filled triangle.
- `drawCircle(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number = 0, thickness: number = 1.0): void` - Draws a circle outline with optional segment count.
- `drawCircleFilled(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number = 0): void` - Draws a filled circle with optional segment count.
- `drawNgon(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number, thickness: number = 1.0): void` - Draws an n-sided polygon outline.
- `drawNgonFilled(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number): void` - Draws a filled n-sided polygon.
- `drawText(pos: vector, r: number, g: number, b: number, a: number, text: string): void` - Draws text at a specified position with color.
- `drawPolyline(points: table<vector>, count: number, r: number, g: number, b: number, a: number, flags: number, thickness: number): void` - Draws a polyline from a table of points.
- `drawConvexPolyFilled(points: table<vector>, count: number, r: number, g: number, b: number, a: number): void` - Draws a filled convex polygon from a table of points.
- `drawBezierCubic(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number, thickness: number, segments: number = 0): void` - Draws a cubic Bezier curve.
- `drawBezierQuadratic(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number, thickness: number, segments: number = 0): void` - Draws a quadratic Bezier curve.
- `addFont(filepath: string, pixelSize: number): userdata` - Adds a font from the specified file path with given pixel size, returning a font handle.
- `pushFont(font: userdata): void` - Pushes a font handle onto the font stack.
- `popFont(): void` - Pops the current font from the font stack.
- `checkbox(label: string, value: boolean, callback: function): void` - Renders a checkbox with the specified label and initial value, calling the callback with the new value on change.
- `sliderInt(label: string, value: number, min: number, max: number, callback: function): void` - Renders an integer slider with the specified label, value, and range, calling the callback with the new value on change.
- `sliderFloat(label: string, value: number, min: number, max: number, callback: function): void` - Renders a float slider with the specified label, value, and range, calling the callback with the new value on change.
- `separator(callback: function): void` - Renders a horizontal separator, calling the callback when rendered.
- `combo(label: string, elements: table<string>, defValue: number, callback: function): void` - Renders a dropdown combo box with the specified label, items, and default value, calling the callback with the selected index on change.

### debugOverlay
Functions for rendering debug overlays in the game world.

- `addBoxOverlay(origin: vector, mins: vector, max: vector, orientation: vector, r: number, g: number, b: number, a: number, duration: number): void` - Draws a box overlay at the specified origin with given bounds and orientation.
- `addLineOverlay(origin: vector, dest: vector, r: number, g: number, b: number, noDepthTest: boolean, duration: number): void` - Draws a line overlay between two points with optional depth testing.
- `worldToScreen(pos: vector): vector` - Converts a world position to screen coordinates.

### engineTrace
Functions for performing trace operations.

- `traceRay(start: vector, end: vector, mask: number, filter: ITraceFilter): trace_t` - Performs a ray trace from start to end with specified mask and filter.

## Global Properties
Interfaces providing direct access to game systems and utilities.

- `beams: IViewRenderBeams` - Manages rendering and manipulation of beams. Provides methods to create, update, and draw beams in the game world.
- `cvar: ICvar` - Manages console variables. Allows finding and manipulating game configuration variables.
- `engine: IVEngineClient` - Provides access to engine-related functionality, such as executing client commands, checking game state, and managing view angles.
- `globalVars: CGlobalVarsBase` - Provides access to global game variables, including timing and network-related properties like current game time and tick count.
- `input: IInput` - Manages input-related properties and user commands, such as camera settings and retrieving user input commands.
- `prediction: IPrediction` - Manages client-side prediction properties, including prediction state and command acknowledgment information.