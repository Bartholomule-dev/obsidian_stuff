---
type: service
domain: combat
file: EncounterResolutionService.gd
status: stable
---
# EncounterResolutionService

Provides shared logic for weighted encounter selection and instant stat-based battle resolution.

## Purpose

Handles quick, non-visual combat resolution and encounter selection for exploration and events.

## Key Responsibilities

- Handles weighted random selection of encounters from pools
- Calculates success probabilities for stat-based checks
- Bridges to RewardDistributionService for XP and rewards
- Provides effective stat calculation used by all combat

## Key Methods

| Method | Purpose |
|--------|---------|
| `pick_encounter(encounters)` | Select encounter by weight |
| `resolve_battle_encounter(...)` | Single-roll stat check |
| `calculate_success_rate(stat, difficulty)` | Success probability (0.2-0.95) |
| `get_effective_stats(demon_id)` | Stats with equipment/buffs |

## Success Rate Formula

```
base_rate = stat_value / (stat_value + difficulty)
clamped = clamp(base_rate, 0.2, 0.95)
```

- Minimum 20% success (never hopeless)
- Maximum 95% success (never guaranteed)

## Effective Stats

Combines:
- Base demon stats
- Equipment bonuses
- Buff effects
- Personality modifiers

## Related

- [[CombatFacade]] - Uses for instant battles
- [[Combat System]] - System overview
- [[Exploration System]] - Encounter resolution
