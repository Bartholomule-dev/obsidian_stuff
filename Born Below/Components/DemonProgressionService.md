---
type: service
domain: demon
file: DemonProgressionService.gd
status: stable
---
# DemonProgressionService

Handles demon experience accumulation, leveling, and calculation of effective attribute totals.

## Purpose

Core progression logic - XP awards, level-ups, and stat calculations.

## Key Responsibilities

- Awards XP with multipliers for personality, mood, and loyalty
- Processes level-up events with stat bonuses and milestone events
- Calculates stat bonuses from level, personality, and equipment
- Provides canonical "effective stats" for validation and execution

## Key Methods

| Method | Purpose |
|--------|---------|
| `award_xp(demon_id, amount, source, type)` | Grant experience |
| `recalculate_stat_bonuses(demon_id)` | Update level bonuses |
| `recalculate_personality_bonuses(demon_id)` | Update personality bonuses |
| `get_effective_stats(demon_id)` | Final stats for gameplay |
| `_process_level_up(demon_id)` | Handle level advancement |

## XP Multipliers

Final XP = Base × Personality × Mood × Loyalty

| Factor | Range |
|--------|-------|
| Personality | 0.8x - 1.2x |
| Mood | 0.75x - 1.0x |
| Loyalty | 0.85x - 1.15x |

## Effective Stats

Combines:
- Base demon stats
- Level bonuses (+2 per level)
- Personality bonuses
- Equipment bonuses

## Level Caps by Rank

| Rank | Max Level |
|------|-----------|
| Lesser | 12 |
| Greater | 15 |
| Archdemon | 20 |

## Related

- [[Demon System]] - System overview
- [[Demon Ranks]] - Level caps
- [[DemonManager]] - Parent coordinator
