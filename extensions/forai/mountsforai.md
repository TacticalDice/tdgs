# TACTICAL DICE GAME SYSTEM (TDGS) - EXTENSION
# Title: Mounts & Vehicles
# Version: 1.0
# Purpose: AI-readable specification for mounts and vehicles
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
OVERVIEW
================================================================================

Extension defining rules for mounts (creatures you ride) and vehicles 
(conveyances you operate).

BUILDS ON:
  - Document 5: Action Taxonomy
  - Document 6: Action Economy
  - Document 8: Combat
  - Document 9: Entities
  - Document 12: Progression
  - Document 13: Character Creation
  - Document 14: Movement & Positioning
  - Document 15: Equipment & Slots

DOES NOT REDEFINE CORE RULES.

================================================================================
CORE DISTINCTION
================================================================================

MOUNT = Entity (has mind)
  - Full 9 stats (its own)
  - Can act independently
  - Can be charmed, panicked, resist
  - Race: Creature type (Horse, Wolf, Griffin)
  - Class: Trained abilities (War Mount, Tracker)
  - Progression: XP from adventuring AND training

VEHICLE = Inert Entity (no mind)
  - Physical stats only (STR, DEX, CON, MOV)
  - Borrows mental stats from driver (REF, INT, WIS, CHA, LUK)
  - Cannot act without driver
  - Race: Vehicle template (Wagon, Chariot, Ship)
  - Class: Inert (always, no progression)
  - Progression: Upgrades (gold) or replacement

TRADE-OFF:
  Mounts: More capability, but can panic/resist
  Vehicles: Total compliance, but no independent action

================================================================================
CREATION: MOUNTS
================================================================================

PROCESS:
  1. Select race (creature type)
  2. Determine base stats from race
  3. Select class (if trained) or leave classless (wild)
  4. Apply class abilities

RACE:
  Defines base stats and innate traits.
  Examples: Horse (base stats, Kick), Wolf (base stats, Bite)
  Content defines mount races.

CLASS:
  Defines trained abilities.
  Examples: War Mount (War-Trained, Trample, Charge), Tracker (Scent)
  Content defines mount classes.

WILD VS TRAINED:
  Wild: Has race, no class levels
  Trained: Has race plus class levels
  Same creature, different training

================================================================================
CREATION: VEHICLES
================================================================================

PROCESS:
  1. Select race (vehicle template)
  2. Stats and traits defined by template
  3. Class is always Inert (Level 1, no progression)
  4. Apply upgrades if desired

RACE (TEMPLATE):
  Defines base stats and innate traits.
  "Wagon" is a race. "War Chariot" is a race.
  Content defines vehicle templates as races.

CLASS (INERT):
  Name: Inert
  Description: For entities without agency or progression
  Max Level: 1
  Abilities: None
  Stat Bonuses: None
  Progression: None (cannot gain XP, cannot level)

  Design Note: Exists to satisfy entity framework.
  All entities have race and class. Vehicles are entities.
  Therefore vehicles have class, but it is an empty one.

================================================================================
PROGRESSION: MOUNTS
================================================================================

Mounts are entities. Entities that participate in challenges earn XP.
Standard progression rules apply (Document 12).

ADVENTURING XP:
  Mounts earn XP from participating in challenges.
  Both rider and mount receive XP. Participation is not divided.
  They were there, they faced danger, they get XP.

TRAINING XP:
  Downtime training is an additional XP source.
  Content defines costs (gold, time, trainer) and XP awarded.
  Lets mounts progress even between adventures.

SPENDING XP:
  Mounts spend XP on class levels and stat increases.
  Standard progression rules (Document 12) apply.

================================================================================
PROGRESSION: VEHICLES
================================================================================

NO XP:
  Vehicles cannot gain XP.
  Inert class has no levels beyond 1.

UPGRADES:
  Modifications, repairs, enchantments improve stats or add traits.
  Content defines costs (gold, time, materials, craftsmen).
  Not XP-based.

REPLACEMENT:
  Buy a better vehicle outright.
  Content defines vehicle catalogs and prices.

================================================================================
PROGRESSION: DRAFT ANIMALS
================================================================================

Draft animals are entities. All non-inert entities earn XP per core 
progression rules (Document 12).

ADVENTURING XP:
  Draft animals pulling a vehicle through combat earn XP from challenges.
  If the chariot tramples goblins, the horses faced danger and survived.
  They earn XP.

TRAINING XP:
  Like mounts, draft animals may earn XP through dedicated training.
  Content defines training costs and XP awarded.

DESIGN NOTE:
  A draft animal is not equipment. It is an entity with a job.
  The job does not remove its right to progress.

================================================================================
PROGRESSION: OPERATORS AND UNWILLING MOUNTS
================================================================================

OPERATOR XP:
  Vehicle operators earn FULL XP for challenges overcome.
  Method does not determine reward.

UNWILLING MOUNTS:
  Earn XP normally from challenges they participate in.
  XP is survival, not consent.
  XP belongs to the entity regardless of status.

================================================================================
ACTION ECONOMY: RIDER AND OPERATOR
================================================================================

Your Action is occupied with controlling the mount or vehicle.
Everything else works normally.

  Timing Type   | Available?
  --------------|--------------------------------------------
  Action        | Restricted to mount/vehicle operation and its abilities
  Step          | N/A (mount/vehicle provides movement)
  Free Actions  | Yes
  Instants      | Yes
  Interrupts    | Yes

MOUNT/VEHICLE ABILITIES:
  Using Trample, Ram, or similar uses your Action.

================================================================================
ACTION ECONOMY: PASSENGERS
================================================================================

Passengers are not controlling the conveyance.
They have nearly full action economy.

  Timing Type   | Available?
  --------------|--------------------------------------------
  Action        | Yes (full)
  Step          | No (moving with conveyance)
  Free Actions  | Yes
  Instants      | Yes
  Interrupts    | Yes

WHY NO STEP:
  Step is movement across the battlefield.
  Passengers are moving with the conveyance, not independently.
  Dismount to get your Step back.

================================================================================
ACTION ECONOMY: MOUNTS (WHILE RIDDEN)
================================================================================

The rider directs. The mount responds.

  Timing Type   | Available?
  --------------|--------------------------------------------
  Action        | No (rider directs)
  Step          | N/A (mount IS the movement)
  Free Actions  | Yes
  Instants      | Yes (if any)
  Interrupts    | Yes (kick, bite, buck)

================================================================================
ATTACKING WHILE MOUNTED OR OPERATING
================================================================================

DEFAULT (NO SPECIAL TRAINING):
  - Use mount/vehicle abilities (Trample, Ram) with your Action
  - Use your Interrupts (Parry, Counterspell, etc.)
  - Use your Instants at round start
  - Use Free Actions (shout commands, drop items)
  - CANNOT use personal attack Actions (swing sword, cast spell)

WITH APPROPRIATE SKILL OR ABILITY:
  - Rider with "Mounted Archery" can make ranged attacks while riding
  - Charioteer with "Combat Driver" can attack while operating
  - Content defines these Skills and Abilities

PASSENGERS:
  No restriction. Can attack normally without special training.

================================================================================
BEING ATTACKED (TARGET CHOICE)
================================================================================

Attacker chooses target freely.
Mount/vehicle and rider/passenger are both valid targets.
No penalty for choosing either.

TACTICAL CHOICES:
  - Kill the mount to strand the rider
  - Kill the rider to claim the mount
  - Destroy the vehicle to halt everyone
  - Target the driver to leave the vehicle uncontrolled

================================================================================
DRIVER INCAPACITATION
================================================================================

If a vehicle's driver is killed or incapacitated mid-movement:
  1. Vehicle completes declared movement in a straight line
  2. Vehicle stops

SEIZING CONTROL MID-MOVEMENT:
  Requires relevant Interrupt ability (content-defined).
  Without such ability, occupants cannot react until vehicle stops.

SEIZING CONTROL AFTER MOVEMENT:
  Any occupant may take control using their Action on their turn.

================================================================================
TRAMPLE MECHANICS
================================================================================

Trample applies to any mount or vehicle with the Trample trait.
Physics are the same whether hooves or wheels.

TRIGGER:
  Trampler enters a smaller creature's square during movement.

RESOLUTION:
  Trampler STR vs Target REF (standard resolution)
  d20 + (Trampler STR - Target REF) + Modifiers >= 11

ON SUCCESS:
  - Target takes trample damage (defined by Trample trait)
  - Target is knocked prone
  - Trampler continues in direction of travel

ON FAILURE:
  - Trampler's movement ends in the square before the target
  - The target braced and held the line

TRAMPLE DISTANCE:
  Formula: MOV / 4 (rounded down) squares in direction of travel

  Mount/Vehicle   | MOV | Trample Distance
  ----------------|-----|------------------
  Riding Horse    | 10  | 2 squares
  Warhorse        | 12  | 3 squares
  War Elephant    | 8   | 2 squares
  Dragon          | 16  | 4 squares
  War Chariot     | 10  | 2 squares

CHAIN EFFECT:
  Each creature in the trample path gets their own opposed roll.
  Trample continues until:
    - Maximum trample distance reached, OR
    - A creature wins the opposed roll (stops the trampler)

RESTRICTIONS:
  - Cannot trample creatures of equal or larger size
  - Cannot trample the same target twice in one turn
  - Target does not get an Interrupt (this is being run over, not an attack)
  - Trample is part of movement. No extra Action cost.

================================================================================
CHARGE
================================================================================

Mounts with the Charge trait deal bonus damage after straight-line movement.

TRIGGER:
  4+ squares of straight-line movement immediately before attack.

EFFECT:
  Bonus damage as defined by trait (e.g., "Charge: +1d6 damage").

================================================================================
ANY ENTITY CAN BE A MOUNT
================================================================================

RULE:
  Any entity can be mounted by entity at least one size smaller.
  Must have carrying capacity.
  Physics does not require trait. Control is the question.

CONTROL STATES:
  State       | Behavior                              | Action Required
  ------------|---------------------------------------|---------------------------
  Trained     | Obeys commands                        | None
  Untrained   | Does not obey, acts on own will       | Action to attempt control
  Hostile     | Actively tries to throw rider         | Check each round or dismounted

CONTROL CHECK:
  Rider CHA vs Mount WIS (standard resolution)

================================================================================
MOUNT RULES
================================================================================

MOUNT STATS:
  All 9 stats are the mount's own.
  Mount is a full Entity per Document 9.

MOUNTED MOVEMENT:
  Use mount's MOV. Rider's MOV is irrelevant while riding.

MOUNTING/DISMOUNTING:
  Mount: Action
  Dismount: Action
  Traits MAY grant faster (e.g., "Cavalry Training: Mount as Free Action")

MOUNT CONTROL:
  Trained/Bonded: No check required, mount obeys
  Under External Effect: Mount may act against rider
  Reasserting Control: Rider CHA vs Mount WIS (standard resolution)

MOUNT DAMAGE AND DEATH:
  Mount has own health pool.
  Damage to mount does not affect rider.
  Mount dies: Rider lands prone in adjacent square (rider's choice).
  Standing from prone: Action
  Airborne death: Rider falls. Falling damage per Document 14 
    (1d6 per 2 squares, cap 10d6 at 20 squares).

INVOLUNTARY DISMOUNT:
  If effect forces rider off mount (knockback, grapple, mount bucking, etc.):
    - Rider lands prone in adjacent square of their choice
    - If mount was airborne, falling damage applies per Document 14

SIZE COMPATIBILITY (MOUNTS):
  Mount must be >= 1 size larger than rider.
  
  Rider Size | Min Mount Size
  -----------|---------------
  Tiny       | Small
  Small      | Medium
  Medium     | Large
  Large      | Huge
  Huge       | Gargantuan

MULTIPLE RIDERS:
  Allowed if mount has carrying capacity.
  Carrying Capacity = STR x 10 x Size Multiplier (WU)
  One rider controls. Additional riders are passengers (full Action, no Step).

================================================================================
VEHICLE RULES
================================================================================

VEHICLE STATS:
  Physical Stats (Vehicle's Own):
    Stat | Source
    -----|--------
    STR  | Vehicle
    DEX  | Vehicle
    CON  | Vehicle
    MOV  | Vehicle (or motive source)

  Mental Stats (Borrowed from Driver):
    The driver (entity actively steering/commanding) provides mental stats.
    In multi-crew vehicles, designate one driver.
    
    Stat | Source
    -----|--------
    REF  | Driver
    INT  | Driver
    WIS  | Driver
    CHA  | Driver
    LUK  | Driver

OCCUPIED VEHICLE:
  Physical attacks target vehicle's stats.
  Mental attacks target driver's stats.

UNOCCUPIED VEHICLE:
  Physical attacks target vehicle's stats.
  Mental attacks auto-succeed (no resistance).
  Exception: Traits may grant resistance (e.g., "Warded").

VEHICLE OPERATION:
  Basic operation: No check.
  Difficult maneuvers: Standard resolution vs terrain's virtual DEX.
  
VEHICLE MANEUVERS:
  Roll: d20 + (Driver DEX - Terrain DEX) + Handling + Modifiers >= 11

PASSENGERS AND CREW:
  Passengers MAY use full Action while aboard (not controlling).
  
  Crew Requirement (X): Need X people or vehicle does not move.
  
  Crew are passengers with jobs. They use normal action economy for tasks.
  A rower uses their Action to row.
  A siege engineer uses their Action to fire the ballista.
  No new mechanics. Action economy applied to vehicle context.

COVER:
  Not inherent. Defined per vehicle via Cover trait.
  
  Cover Type | Effect
  -----------|--------
  None       | No cover bonus
  Partial    | +2 REF vs ranged attacks
  Half       | +4 REF vs ranged attacks
  Full       | Cannot be targeted directly (must destroy vehicle first)

VEHICLE DAMAGE:
  Health pool: HP = CON x 5 (standard entity rules)
  At 0 HP: Destroyed/disabled. Occupants must disembark or are trapped.

MOTIVE SOURCES:
  Requires Motive Source: No inherent MOV, needs propulsion.
  Self-Propelled: Has own MOV (exotic).
  Most vehicles require motive sources.

DRAFT ANIMALS:
  Draft animal Carrying Capacity = STR x 10 x Size Multiplier (WU)
  Total load = vehicle weight + cargo + passengers
  
  Load vs Capacity | Effect
  -----------------|--------
  At or under      | Full MOV
  Over, under 2x   | Half MOV
  Over 2x          | Cannot move

MULTIPLE DRAFT ANIMALS:
  Add carrying capacities together.
  Example: Two horses (STR 10, Large 2x) = 200 + 200 = 400 WU capacity.

RAMMING:
  Basic: d20 + (Vehicle STR - Target REF) + Modifiers >= 11
  Damage: Ram Damage trait.
  With Trample trait: Use full trample mechanics.

================================================================================
COMMON MOUNT TRAITS
================================================================================

Trait          | Description
---------------|---------------------------------------------
Trained        | Obeys without check
War-Trained    | Immune mundane panic, +2 vs magical fear, offensive Interrupts
Skittish       | -2 to rider CHA when reasserting control
Loyal          | +2 to rider CHA when reasserting control
Aggressive     | Attacks adjacent enemies without command
Flight         | Can fly using MOV
Aquatic        | Full MOV in water
Amphibious     | Full MOV on land and water
Burrowing      | Can move through earth/sand
Climbing       | Can scale vertical surfaces
Trample (XdY)  | Can trample smaller creatures, deals XdY damage
Charge         | Bonus damage after 4+ squares straight line
Mount (Size)   | Valid rider sizes

================================================================================
COMMON VEHICLE TRAITS
================================================================================

Trait                    | Description
-------------------------|---------------------------------------------
Passenger Capacity (X)   | Count, size restrictions, action restrictions
Crew Requirement (X)     | Minimum operators needed
Handling (+/-X)          | Modifier to maneuver checks
Cover (Type)             | None, Partial (+2), Half (+4), Full
Cargo Capacity (X WU)    | Weight beyond passengers
Terrain Restriction      | Cannot traverse specified terrain
Terrain Specialization   | Bonus in specific terrain
Enclosed                 | Full cover, limited visibility/actions
Open                     | No cover, full visibility/actions
Fuel/Feed                | Requires resource to operate
Magical                  | Operates via magic
Requires Motive Source   | No inherent MOV
Self-Propelled           | Has own MOV
Ram Damage (X or XdY)    | Basic collision damage
Trample (XdY)            | Can trample smaller creatures, deals XdY damage

================================================================================
EXAMPLE: HORSE (MOUNT RACE)
================================================================================

Name: Horse
Size: Large
Base STR: 10
Base DEX: 10
Base REF: 8
Base CON: 8
Base MOV: 10
Base INT: 3
Base WIS: 6
Base CHA: 4
Base LUK: 0
Innate Traits: Trained, Skittish
Mount: Medium or smaller
Carrying Capacity: 200 WU

================================================================================
EXAMPLE: WAR MOUNT (MOUNT CLASS)
================================================================================

Level | XP Cost | Abilities Gained
------|---------|----------------------------------
1     | 50      | War-Trained, removes Skittish
2     | 100     | Trample (1d6)
3     | 200     | Charge (+1d6)
4     | 400     | Trample improves to 1d8

================================================================================
EXAMPLE: WARHORSE (HORSE + WAR MOUNT 4)
================================================================================

Name: Warhorse
Race: Horse
Class: War Mount (Level 4)
Size: Large
STR: 12
DEX: 8
REF: 6
CON: 10
MOV: 12
INT: 3
WIS: 6
CHA: 4
LUK: 0
Traits: Trained, War-Trained, Trample (1d8), Charge (+1d6)
Mount: Medium or smaller
Carrying Capacity: 240 WU
Trample Distance: 3 squares

================================================================================
EXAMPLE: WAGON (VEHICLE RACE)
================================================================================

Name: Wagon
Size: Large
STR: 15
DEX: 4
CON: 12
MOV: -
Class: Inert (Level 1)
Weight: 50 WU
Traits:
  - Requires Motive Source
  - Passenger Capacity (4, Medium or smaller)
  - Cargo Capacity (200 WU)
  - Open
  - Handling (-2)
  - Crew Requirement (1)

================================================================================
EXAMPLE: WAR CHARIOT (VEHICLE RACE)
================================================================================

Name: War Chariot
Size: Large
STR: 10
DEX: 8
CON: 8
MOV: -
Class: Inert (Level 1)
Weight: 30 WU
Traits:
  - Requires Motive Source
  - Passenger Capacity (2, Medium or smaller)
  - Cargo Capacity (20 WU)
  - Open
  - Handling (+1)
  - Crew Requirement (1)
  - Trample (2d6)
  - Cover (Partial)

================================================================================
GRAPPLING RIDERS
================================================================================

Standard grapple rules apply.
Grapple: STR vs STR (per Document 5).
Success: Target gains Grappled condition.
Subsequent grapple actions can move target, including off the mount.
No extension-specific mechanics required.

================================================================================
SUMMARY
================================================================================

Mount vs Vehicle:        Mount = Entity. Vehicle = Inert Entity.
Any Entity as Mount:     Yes, if size allows. Control state determines behavior.
Mount Creation:          Race (creature type) + Class (trained abilities)
Mount Progression:       XP from adventuring AND training (downtime)
Vehicle Creation:        Race (template) + Inert class (no progression)
Vehicle Progression:     Upgrades (gold) or replacement. Not XP-based.
Rider/Operator Action:   Restricted unless Skill/Ability grants combat Actions
Passenger Action:        Full Action (no Step)
Mount Action (Ridden):   No Action; Instants/Interrupts/Free work
Rider XP:                Full XP from challenges
Draft Animal XP:         Full XP from challenges AND training
Unwilling Mount XP:      Earns XP normally (survival, not consent)
Mounted Movement:        Mount's MOV
Mount/Dismount:          Action each
Mount Control:           Trained = obeys. Reassert = CHA vs WIS.
Mount Death:             Rider prone adjacent; falling damage if airborne (Doc 14)
Involuntary Dismount:    Prone adjacent; falling damage if airborne
Vehicle Stats:           Physical own, mental from driver
Driver Incapacitation:   Vehicle completes movement straight, then stops
Unoccupied Vehicle:      No mental resistance
Maneuvers:               Standard resolution vs terrain virtual DEX
Cover:                   Content defines via traits
Target Choice:           Attacker picks freely
Size (Mounts):           Mount >= 1 size larger
Size (Vehicles):         Trait defines
Load/Speed:              Over capacity = half MOV; over 2x = cannot move
Draft Animals:           Add capacities
Trample:                 STR vs REF, MOV / 4 distance, chain until stopped
Ramming:                 Vehicle STR vs Target REF
Grappling Riders:        Standard STR vs STR

================================================================================
KEY CONSTANTS
================================================================================

TRAMPLE_DISTANCE_DIVISOR = 4
MOUNT_SIZE_DIFFERENCE = 1 // Mount must be 1 size larger
LOAD_HALF_SPEED_MULTIPLIER = 2 // Over capacity but under 2x
LOAD_NO_MOVE_MULTIPLIER = 2 // Over 2x capacity
CARRYING_CAPACITY_FORMULA = "STR x 10 x Size_Multiplier"
VEHICLE_HP_FORMULA = "CON x 5"

SIZE_MULTIPLIERS:
  Tiny: 0.25
  Small: 0.5
  Medium: 1
  Large: 2
  Huge: 4
  Gargantuan: 8+

================================================================================
CROSS-REFERENCES
================================================================================

Document 5: Action Taxonomy
  - Action types (Action, Step, Free, Instant, Interrupt)
  - Grapple mechanics (STR vs STR)

Document 6: Action Economy
  - Turn structure (1 Action + 1 Step + unlimited Free)
  - Timing rules

Document 8: Combat
  - Standard resolution (d20 + stat diff >= 11)
  - Damage and conditions

Document 9: Entities
  - Entity structure (race + class)
  - Size categories
  - HP = CON x 5

Document 12: Progression
  - XP from challenges
  - Stat increases and class levels

Document 13: Character Creation
  - Entity creation process

Document 14: Movement & Positioning
  - Falling damage (1d6 per 2 squares, cap 10d6)
  - Terrain types
  - Square-based movement

Document 15: Equipment & Slots
  - Carrying capacity (STR x 10 x Size Multiplier)
  - Weight Units (WU)

================================================================================
EXTENSION STATUS
================================================================================

STATUS: Canonical Extension
VERSION: 1.0

This extension builds on core TDGS rules. It does not redefine them.

================================================================================
CANONICAL URLS
================================================================================

Human-readable: https://tacticaldice.com/docs/tdgs/mounts
AI-optimized:   https://tacticaldice.com/docs/tdgs/mountsforai

================================================================================
END OF DOCUMENT
================================================================================
