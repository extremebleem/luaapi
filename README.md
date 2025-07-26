Lua API Documentation
This document outlines the Lua API for interacting with game entities, input commands, configuration variables, events, and rendering utilities. The API is organized into enums, usertypes, and tables with their respective methods and properties.
Enums
Hitboxes

HEAD: number
NECK: number
PELVIS: number
STOMACH: number
CHEST: number
RIGHT_THIGH: number
LEFT_THIGH: number
RIGHT_CALF: number
LEFT_CALF: number
RIGHT_FOOT: number
LEFT_FOOT: number
RIGHT_HAND: number
LEFT_HAND: number
RIGHT_UPPER_ARM: number
RIGHT_FOREARM: number
LEFT_UPPER_ARM: number
LEFT_FOREARM: number

Buttons

IN_ATTACK: number
IN_JUMP: number
IN_DUCK: number
IN_FORWARD: number
IN_BACK: number
IN_USE: number
IN_CANCEL: number
IN_LEFT: number
IN_RIGHT: number
IN_MOVELEFT: number
IN_MOVERIGHT: number
IN_ATTACK2: number
IN_RUN: number
IN_RELOAD: number
IN_ALT1: number
IN_ALT2: number
IN_SCORE: number
IN_SPEED: number
IN_WALK: number
IN_ZOOM: number
IN_WEAPON1: number
IN_WEAPON2: number
IN_BULLRUSH: number
IN_GRENADE1: number
IN_GRENADE2: number
IN_LOOKSPIN: number

Contents

CONTENTS_EMPTY: number
CONTENTS_SOLID: number
CONTENTS_WINDOW: number
CONTENTS_AUX: number
CONTENTS_GRATE: number
CONTENTS_SLIME: number
CONTENTS_WATER: number
CONTENTS_MIST: number
CONTENTS_OPAQUE: number
LAST_VISIBLE_CONTENTS: number
ALL_VISIBLE_CONTENTS: number
CONTENTS_TESTFOGVOLUME: number
CONTENTS_UNUSED5: number
CONTENTS_UNUSED6: number
CONTENTS_TEAM1: number
CONTENTS_TEAM2: number
CONTENTS_IGNORE_NODRAW_OPAQUE: number
CONTENTS_MOVEABLE: number
CONTENTS_AREAPORTAL: number
CONTENTS_PLAYERCLIP: number
CONTENTS_MONSTERCLIP: number
CONTENTS_CURRENT_0: number
CONTENTS_CURRENT_90: number
CONTENTS_CURRENT_180: number
CONTENTS_CURRENT_270: number
CONTENTS_CURRENT_UP: number
CONTENTS_CURRENT_DOWN: number
CONTENTS_ORIGIN: number
CONTENTS_MONSTER: number
CONTENTS_DEBRIS: number
CONTENTS_DETAIL: number
CONTENTS_TRANSLUCENT: number
CONTENTS_LADDER: number
CONTENTS_HITBOX: number

Surface Flags

SURF_LIGHT: number
SURF_SLICK: number
SURF_SKY: number
SURF_WARP: number
SURF_TRANS: number
SURF_WET: number
SURF_TRIGGER: number
SURF_NODRAW: number
SURF_HINT: number
SURF_SKIP: number
SURF_NOLIGHT: number
SURF_BUMPLIGHT: number
SURF_NOSHADOWS: number
SURF_NODECALS: number
SURF_NOCHOP: number
SURF_HITBOX: number

Masks

MASK_ALL: number
MASK_SOLID: number
MASK_PLAYERSOLID: number
MASK_NPCSOLID: number
MASK_WATER: number
MASK_OPAQUE: number
MASK_OPAQUE_AND_NPCS: number
MASK_VISIBLE: number
MASK_VISIBLE_AND_NPCS: number
MASK_SHOT: number
MASK_SHOT_HULL: number
MASK_SHOT_HULL_EX: number
MASK_SHOT_PORTAL: number
MASK_SOLID_BRUSHONLY: number
MASK_PLAYERSOLID_BRUSHONLY: number
MASK_NPCSOLID_BRUSHONLY: number
MASK_NPCWORLDSTATIC: number
MASK_SPLITAREAPORTAL: number
MASK_CURRENT: number

Usertypes
vector
Represents a 3D vector with x, y, z components.
Constructors:

vector(): Creates a zero vector.
vector(x: number, y: number, z: number): Creates a vector with specified coordinates.

Properties:

x: number
y: number
z: number

Methods:

isZero(): boolean - Checks if the vector is zero.
length(): number - Returns the vector's length.
length2D(): number - Returns the 2D length (x, y).
length2DSqr(): number - Returns the squared 2D length.
lengthSqr(): number - Returns the squared length.
cross(other: vector): vector - Computes the cross product with another vector.
normalize(): number - Normalizes the vector and returns its length.
normalized(): vector - Returns a normalized copy of the vector.
clear(): void - Sets the vector to zero.
withinAABox(min: vector, max: vector): boolean - Checks if the vector is within an axis-aligned bounding box.
dot(other: vector | table<number, number, number>): number - Computes the dot product with another vector or a table of three numbers.

Operators:

+ (vector): Adds two vectors.
- (vector): Subtracts another vector.
* (number | vector): Multiplies by a scalar or component-wise with another vector.
/ (number | vector): Divides by a scalar or component-wise by another vector.

Global Function:

Vector(x: number, y: number, z: number): vector - Creates a new vector.

entity
Represents a game entity.
Properties:

teamNum: number - Team number.
isAlive: boolean - Whether the entity is alive.
absVelocity: vector - Absolute velocity.
absOrigin: vector - Absolute origin.
absAngles: vector - Absolute angles.
health: number - Health value.

Methods:

getField(field: string): any - Retrieves a field value by name.

usercmd
Represents a user command for input handling.
Properties:

commandNumber: number
tickCount: number
buttons: number
weaponSelect: number
weaponSubType: number
randomSeed: number
forwardMove: number
sideMove: number
upMove: number
viewAngles: vector
impulse: number
mousedx: number
mousedy: number
hasBeenPredicted: boolean

cfgVar
Represents a configuration variable.
Methods:

set(value: any): void - Sets the variable's value.
get(): string - Gets the variable's value as a string.

gameEvent
Represents a game event.
Methods:

getEventName(): string - Gets the event name.
getInt(key: string): number - Gets an integer value.
getFloat(key: string): number - Gets a float value.
getBool(key: string): boolean - Gets a boolean value.
getString(key: string): string - Gets a string value.
setBool(key: string, value: boolean): void - Sets a boolean value.
setFloat(key: string, value: number): void - Sets a float value.
setInt(key: string, value: number): void - Sets an integer value.

surface_t
Represents a surface.
Properties:

name: string
surfaceProps: number
flags: number

plane
Represents a plane.
Properties:

normal: vector
dist: number

trace_t
Represents a trace result.
Properties:

fractionLeftSolid: number
surface: surface_t
hitGroup: number
physicsBone: number
ent: entity
hitbox: number
startPos: vector
endPos: vector
plane: plane
fraction: number
contents: number
dispFlags: number
allSolid: boolean
startSolid: boolean

ITraceFilter
Base type for trace filters.
CTraceFilter
Inherits from ITraceFilter.
CTraceFilterSimple
Inherits from CTraceFilter.
Constructor:

CTraceFilterSimple(ent: entity): Creates a trace filter for a single entity.

Global Function:

traceFilterSimple(ent: entity): CTraceFilterSimple

CTraceFilterSkipTwoEntities
Inherits from CTraceFilterSimple.
Constructor:

CTraceFilterSkipTwoEntities(ent1: entity, ent2: entity): Creates a trace filter ignoring two entities.

Global Function:

traceFilterSkipTwoEntities(ent1: entity, ent2: entity): CTraceFilterSkipTwoEntities

Tables
callbacks

createMove(func: function): void - Registers a callback for the create move event.
createMovePostPredict(func: function): void - Registers a callback for post-prediction create move.
createMovePostRestore(func: function): void - Registers a callback for post-restore create move.
onPresent(func: function): void - Registers a callback for the present event.
onGameEvent(func: function): void - Registers a callback for game events.

entityList

getLocalPlayer(): entity - Gets the local player entity.
getPlayer(index: number): entity - Gets a player entity by index.

events

registerEvent(event: string, func: function): void - Registers a function for a specific game event.

netvars

getFieldOffset(dataTable: string, fieldName: string): number - Gets the offset of a field in a data table.

cfg

getVar(name: string): cfgVar - Gets a configuration variable by name.

imgui
Drawing functions for rendering UI elements.

drawLine(p1: vector, p2: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void
drawRect(p_min: vector, p_max: vector, r: number, g: number, b: number, a: number, rounding: number = 0.0, flags: number = 0, thickness: number = 1.0): void
drawRectFilled(p_min: vector, p_max: vector, r: number, g: number, b: number, a: number, rounding: number = 0.0, flags: number = 0): void
drawRectFilledMultiColor(p_min: vector, p_max: vector, r1: number, g1: number, b1: number, a1: number, r2: number, g2: number, b2: number, a2: number, r3: number, g3: number, b3: number, a3: number, r4: number, g4: number, b4: number, a4: number): void
drawQuad(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void
drawQuadFilled(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number): void
drawTriangle(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number, thickness: number = 1.0): void
drawTriangleFilled(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number): void
drawCircle(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number = 0, thickness: number = 1.0): void
drawCircleFilled(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number = 0): void
drawNgon(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number, thickness: number = 1.0): void
drawNgonFilled(center: vector, radius: number, r: number, g: number, b: number, a: number, segments: number): void
drawText(pos: vector, r: number, g: number, b: number, a: number, text: string): void
drawPolyline(points: table<vector>, count: number, r: number, g: number, b: number, a: number, flags: number, thickness: number): void
drawConvexPolyFilled(points: table<vector>, count: number, r: number, g: number, b: number, a: number): void
drawBezierCubic(p1: vector, p2: vector, p3: vector, p4: vector, r: number, g: number, b: number, a: number, thickness: number, segments: number = 0): void
drawBezierQuadratic(p1: vector, p2: vector, p3: vector, r: number, g: number, b: number, a: number, thickness: number, segments: number = 0): void

debugOverlay

addBoxOverlay(origin: vector, mins: vector, max: vector, orientation: vector, r: number, g: number, b: number, a: number, duration: number): void
addLineOverlay(origin: vector, dest: vector, r: number, g: number, b: number, noDepthTest: boolean, duration: number): void
worldToScreen(pos: vector): vector - Converts a world position to screen coordinates.

engineTrace

traceRay(start: vector, end: vector, mask: number, filter: ITraceFilter): trace_t - Performs a ray trace.
