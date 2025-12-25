---
type: facade
domain: mortal
file: MortalCharacterFacade.gd
status: stable
---
# MortalCharacterFacade

Unified interface for mortal character operations.

## Purpose

Manages character retrieval, pressure application, corruption state, awareness, defenses, and recovery.

## Dependencies

- [[MortalCharacterManager]] - Character data, CRUD
- [[MortalCharacterService]] - Pressure, corruption logic
- [[CharacterDefenseService]] - Defense mechanics
- [[CorruptionRippleService]] - Cascading effects

## Key Responsibilities

### Character Retrieval
- `get_character(character_id)` - Get by ID
- `get_all_characters()` - All characters
- `get_uncorrupted_characters()` - Active targets
- `get_corrupted_characters()` - Completed targets
- `is_character_active(character_id)` - Not corrupted?

### Pressure & Corruption
- `apply_pressure(character_id, need, amount, demon_id)` - Apply pressure
- `calculate_effective_pressure(character_id, need, base_amount)` - With vulnerabilities
- `is_corrupted(character_id)` - Corruption check
- `get_corruption_flavor(character_id)` - Flavor text

### Corruption Stage (0-4)
- `get_corruption_stage(character_id)` - Stage number
- `get_corruption_stage_name(character_id)` - innocent/tempted/wavering/falling/corrupted
- `cleanse_character(character_id)` - Reset to stage 0

### Awareness System
- `get_awareness(character_id)` - 0-100 value
- `get_awareness_level(character_id)` - unaware/suspicious/alert/vigilant
- `is_vigilant(character_id)` - At highest tier?

### Defense System
- `get_active_defenses(character_id)` - Active defense list
- `has_active_defense(character_id, defense_type)` - Check specific
- `is_sin_blocked(character_id, sin_type)` - Change Routine check

### Recovery
- `get_recovery_rate(need_name)` - Recovery rate for need
- `will_character_recover_this_week(character_id)` - Recovery check

## Stage Names

| Stage | Name | Description |
|-------|------|-------------|
| 0 | innocent | Untouched |
| 1 | tempted | Beginning to waver |
| 2 | wavering | Seriously tempted |
| 3 | falling | Near corruption |
| 4 | corrupted | Fully corrupted |

## Related

- [[Corruption System]] - System overview
- [[Mortal Character Data]] - Data structure
- [[Seven Sins]] - Need mapping
