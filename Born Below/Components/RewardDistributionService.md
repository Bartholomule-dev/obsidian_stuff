---
type: service
domain: economy
file: RewardDistributionService.gd
status: stable
---
# RewardDistributionService

Provides centralized, authoritative source for distributing all game rewards and applying failure penalties.

## Purpose

Single source of truth for all reward distribution - ensures consistent XP, soul essence, and item grants.

## Key Responsibilities

- Distributes Soul Essence rewards from encounters, enemies, quests
- Manages XP distribution and stat adjustments using Read-Bypass pattern
- Orchestrates item acquisition with configurable drop chances
- Processes CombatOutcomeEvent for unified combat rewards/penalties

## Key Methods

| Method | Purpose |
|--------|---------|
| `award_soul(source, category)` | Add SE to global pool |
| `award_xp(demon_id, amount, category, source_id)` | Increment demon XP |
| `apply_stat_rewards(demon_id, stat_rewards)` | Update demon stats |
| `apply_combat_outcome(outcome)` | Handle combat results |

## Reward Categories

| Category | Examples |
|----------|----------|
| Combat | Enemy drops, victory bonuses |
| Quest | Quest completion rewards |
| Exploration | Node rewards, discoveries |
| Mission | Scheme completion |
| Tournament | Per-round and victory |

## Combat Outcome Handling

```
apply_combat_outcome(outcome)
    ├── If victory:
    │   ├── Award XP
    │   ├── Award soul essence
    │   ├── Grant stat rewards
    │   └── Process item drops
    └── If defeat:
        ├── Apply stress penalty
        └── Apply energy penalty
```

## Related

- [[Economy System]] - Soul essence flow
- [[Combat System]] - Combat rewards
- [[Demon System]] - XP/progression
- [[Exploration System]] - Exploration rewards
