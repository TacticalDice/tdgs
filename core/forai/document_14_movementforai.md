# TACTICAL DICE GAME SYSTEM (TDGS) - DOCUMENT 14
# Title: Movement & Positioning
# Version: 1.0
# Purpose: AI-readable specification for movement and positioning
# Target: Language models, AI assistants, game designers, developers
# License: MIT

================================================================================
DISTANCE SYSTEM (HYBRID)
================================================================================

GRID_SYSTEM:
    unit: "square"  // Abstract unit
    scale: "1 MOV = 1 square"
    content_defines: "real-world scale (e.g., 5 feet, 1.5 meters)"
    diagonal_cost: 1  // Not 1.5, gameplay > geometry

RANGE_BANDS:
    adjacent: {squares: "0-1", description: "Touching, melee range"}
    near: {squares: "2-4", description: "Close, easy reach"}
    far: {squares: "5-10", description: "Ranged combat distance"}
    distant: {squares: "11+", description: "Long range"}

MOV_TO_BANDS:
    mov_6_or_less: 1 band per Move
    mov_7_to_12: 2 bands per Move
    mov_13_plus: 3 bands per Move

MEASUREMENT_UNITS_NOTE:
    engine_unit: "square"
    content_examples: [
        "1 square = 5 feet (fantasy)",
        "1 square = 1.5 meters (metric)",
        "1 square = 2 meters (sci-fi)"
    ]
    weight_unit: "WU (Weight Unit)"
    see_also: "Document 15 (Equipment & Slots)"

================================================================================
MOVEMENT ACTIONS
================================================================================

MOVE_ACTION:
    cost: "Action"
    distance: "Up to MOV squares"
    
STEP:
    cost: "Free action"
    distance: 1  // Always 1 square
    terrain_affected: false
    triggers_opportunity_attack: false
    
DISENGAGE:
    cost: "Action"
    distance: "Up to MOV squares"
    triggers_opportunity_attack: false

================================================================================
TERRAIN
================================================================================

TERRAIN_TYPES:
    normal:
        movement: "Full MOV"
        
    difficult:
        movement: "Half MOV (round down)"
        examples: ["mud", "rubble", "undergrowth", "shallow water"]
        
    very_difficult:
        movement: "Quarter MOV (round down)"
        examples: ["deep snow", "dense jungle", "waist-deep water"]
        
    hazardous:
        movement: "Varies"
        effect: "Damage on entry or start of turn"
        damage: "Defined by content"
        examples: ["fire", "acid pools", "spike traps"]
        
    blocking:
        movement: "Cannot pass"
        blocks_los: true
        examples: ["walls", "boulders", "closed doors"]
        
    obscuring:
        movement: "Normal"
        blocks_los: true
        examples: ["fog", "smoke", "magical darkness"]

================================================================================
LINE OF SIGHT
================================================================================

LINE_OF_SIGHT:
    method: "Center to center"
    clear: "Can see/target"
    blocked: "Cannot see/target"
    blocked_by: ["blocking terrain", "obscuring terrain"]

================================================================================
ADJACENCY
================================================================================

ADJACENCY:
    definition: "Within 1 square"
    includes_diagonals: true
    adjacent_squares: 8  // Ring around entity

================================================================================
WEAPON RANGE
================================================================================

WEAPON_RANGE:
    melee:
        optimal: "Adjacent"
        extended: null
        maximum: "Adjacent"
        
    reach:
        optimal: ["Adjacent", "Near"]
        extended: null
        maximum: "Near"
        opportunity_attack_range: ["Adjacent", "Near"]
        
    thrown:
        optimal: "Near"
        extended: "Far"
        extended_penalty: -2
        maximum: "Far"
        
    ranged:
        optimal: "Far"
        extended: "Distant"
        extended_penalty: -2
        maximum: "Distant"
        
    long_range:
        optimal: "Distant"
        extended: null
        maximum: "Distant"

================================================================================
COVER
================================================================================

COVER:
    partial:
        obscured: "25-50%"
        bonus: "+2 REF"
        
    half:
        obscured: "50-75%"
        bonus: "+4 REF"
        
    full:
        obscured: "75%+"
        effect: "Untargetable"
        
    applies_to: "Ranged attacks"
    note: "Melee attackers are adjacent - cover doesn't help"

================================================================================
OPPORTUNITY ATTACKS
================================================================================

OPPORTUNITY_ATTACK:
    trigger: "Leaving adjacent square of hostile entity"
    attack_type: "One free melee attack"
    resolution: "STR vs REF (normal attack)"
    timing: "Before movement completes"
    limit: "One per triggering movement"
    
AVOIDANCE:
    step:
        distance: 1
        triggers_oa: false
        
    disengage:
        cost: "Action"
        movement: "Up to MOV"
        triggers_oa: false

REACH_WEAPONS:
    threat_range: ["Adjacent", "Near"]
    oa_trigger: "Leaving Adjacent OR Near"

================================================================================
FLANKING AND SURROUNDED
================================================================================

POSITIONAL_BONUSES:
    flanking:
        requirement: "2 allies on opposite sides of enemy"
        condition: "Both adjacent, straight line through target"
        bonus: "+2 to hit"
        
    surrounded:
        requirement: "3+ adjacent enemies"
        bonus: "+4 to hit"
        
    overwhelmed:
        requirement: "5+ adjacent enemies"
        bonus: "+6 to hit"

================================================================================
HIGH GROUND (OPTIONAL)
================================================================================

HIGH_GROUND:
    optional: true
    requirement: "Higher elevation than target"
    bonus: "+2 to hit"

================================================================================
FALLING
================================================================================

FALLING:
    damage: "1d6 per 2 squares"
    cap: "10d6 (20 squares)"
    reduction: "Content decides (skills, abilities)"
    
FALLING_TABLE:  // Squares are engine unit; feet are content example
    2_squares: {damage: "1d6", example_5ft: "10 feet"}
    4_squares: {damage: "2d6", example_5ft: "20 feet"}
    10_squares: {damage: "5d6", example_5ft: "50 feet"}
    20_plus_squares: {damage: "10d6 (capped)", example_5ft: "100+ feet"}

================================================================================
FORCED MOVEMENT
================================================================================

FORCED_MOVEMENT:
    push:
        effect: "Move target X squares directly away from you"
        
    pull:
        effect: "Move target X squares directly toward you"
        
    slide:
        effect: "Move target X squares in any direction"
        
    triggers_opportunity_attack: false
    note: "Not choosing to leave - being moved"

================================================================================
SUMMARY: ALL POSITIONAL MODIFIERS
================================================================================

ATTACK_MODIFIERS:
    flanking: +2
    surrounded_3_plus: +4
    overwhelmed_5_plus: +6
    high_ground: +2  // Optional rule
    extended_range: -2

DEFENSE_MODIFIERS:
    partial_cover: "+2 REF"
    half_cover: "+4 REF"
    full_cover: "Untargetable"

================================================================================
KEY CONSTANTS
================================================================================

MOVEMENT_CONSTANTS:
    step_distance: 1
    diagonal_cost: 1
    distance_unit: "square"  // Abstract, content defines scale
    
TERRAIN_MULTIPLIERS:
    normal: 1.0
    difficult: 0.5
    very_difficult: 0.25
    
FALLING_CONSTANTS:
    damage_per_2_squares: "1d6"
    max_damage: "10d6"
    max_distance: 20  // squares
    
COVER_BONUSES:
    partial: 2
    half: 4
    full: "untargetable"
    
POSITIONAL_BONUSES:
    flanking: 2
    surrounded: 4
    overwhelmed: 6
    high_ground: 2

================================================================================
DESIGN NOTES
================================================================================

DESIGN_PRINCIPLES:
    - Hybrid distance supports both grid and theater-of-mind
    - Diagonal costs 1 (gameplay > geometry)
    - Square is abstract unit; content defines scale
    - Opportunity attacks create sticky melee engagement
    - Step and Disengage provide escape options
    - Cover bonuses offset flanking bonuses (natural counters)
    - Forced movement never triggers OA (you're not choosing to leave)
    - Falling caps at 10d6 (terminal velocity)
    - Weight uses WU (Weight Unit), distance uses squares

================================================================================
END OF DOCUMENT 14
================================================================================
