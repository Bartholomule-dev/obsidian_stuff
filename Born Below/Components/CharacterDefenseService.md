---
type: service
domain: corruption
file: CharacterDefenseService.gd
status: stable
---
# CharacterDefenseService

Manages active defensive behaviors mortal characters adopt to resist corruption.

## Purpose

AI-driven character resistance based on awareness and need states.

## Key Responsibilities

- Activates defenses when awareness/needs cross thresholds
- Implements Change Routine system blocking repeated sin types
- Calculates weekly intervention risk from defenses
- Handles character-specific modifiers (e.g., Bishop's prayer)

## Key Methods

| Method | Purpose |
|--------|---------|
| `check_and_update_defenses(char_id)` | Toggle active defenses |
| `record_scheme_sin_type(char_id, sin)` | Track for routine change |
| `can_target_character(char_id, sin)` | Validate targeting |
| `process_weekly_defenses()` | Weekly decay/updates |
| `get_intervention_risk_from_defenses(char_id)` | Risk contribution |

## Defense Triggers

| Defense | Trigger |
|---------|---------|
| Seek Allies | Awareness ≥ 51 |
| Fortify Weakness | Lowest need < 40 |
| Change Routine | 3+ schemes same sin |
| Divine Prayer | Awareness ≥ 76 |

## Character Modifiers

| Character | Modifier |
|-----------|----------|
| Knight | Protected blocks Lust |
| Queen | Protected blocks solo schemes |
| Bishop | Prayer effect doubled |

## Change Routine

After 3 schemes of same sin type:
- That sin blocked for 2 weeks
- Counter resets after block expires

## Related

- [[Character Defenses]] - Concept overview
- [[Awareness System]] - Triggers defenses
- [[Intervention Risk]] - Prayer effects
