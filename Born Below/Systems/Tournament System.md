---
type: system
domain: combat
status: stable
---
# Tournament System

Multi-round combat gauntlets where demons fight through increasingly difficult opponents with visual battles.

## Overview

| Component | Purpose |
|-----------|---------|
| [[TournamentService]] | Assignment, validation, rewards |
| [[TournamentController]] | Gauntlet orchestration, visual combat |
| [[CombatFacade]] | Visual battle presentation |

**Data:** `data/planning/tournaments/*.tres`

## Key Features

- **Multi-Round Gauntlets:** 3-5 sequential visual battles
- **HP Carry-Over:** Damage persists between rounds
- **Between-Round Healing:** 20% max HP restored after each victory
- **Difficulty Scaling:** Enemy stats multiplied each round
- **Entry Costs:** Soul essence + demon energy
- **Progressive Rewards:** XP per round + completion bonus + stat boosts

## Tournament Data Structure

```gdscript
# TournamentData.tres
tournament_id = "pit_fighters_trial"
tournament_name = "Pit Fighter's Trial"
tier = 1                          # Unlock tier (1-3)
required_demon_level = 1          # Minimum demon level
soul_essence_cost = 30            # Entry fee (soul essence)
energy_cost = 25                  # Demon energy consumed
rounds = 3                        # Number of battles
enemy_pool = ["slime", "skeleton", "void_beast"]  # Opponents in order
difficulty_scaling = 1.1          # Enemy stat multiplier (1.1 = +10% per round)
xp_reward_per_victory = 25        # XP per round won
xp_reward_completion = 60         # Bonus XP for sweeping
stat_rewards = {wrath: 2, pride: 1}  # Permanent stats (completion only)
item_rewards = []                 # Items awarded (completion only)
```

## Available Tournaments

| Tournament | Tier | Level | Rounds | Entry Cost | Scaling | XP (per/bonus) |
|------------|------|-------|--------|------------|---------|----------------|
| Pit Fighter's Trial | 1 | 1 | 3 | 30 soul, 25 energy | 1.1x | 25/60 |
| Arena of Wrath | 2 | 3 | 4 | 80 soul, 40 energy | 1.2x | 40/100 |
| Infernal Colosseum | 3 | 5 | 5 | 150 soul, 60 energy | 1.3x | 60/150 |

## Execution Flow

```
┌─────────────────────────────────────────────────────────────┐
│  PLANNING PHASE                                             │
│  UnifiedAssignmentModal → TournamentService.assign()        │
│  - Validate level, energy, strike status                    │
│  - Pay soul essence + energy costs                          │
│  - Store in HellWeeklyPlan                                  │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│  EXECUTION PHASE (WeekManager → VisualsCoordinator)         │
│  TournamentController.present_tournament()                  │
│                                                             │
│  for each round:                                            │
│    1. Show round intro (ActivityLog)                        │
│    2. Visual combat (CombatVisualController)                │
│       - HP carries over from previous round                 │
│       - Enemy stats × difficulty_scaling                    │
│    3. If victory:                                           │
│       - Award per-round XP                                  │
│       - Heal 20% max HP                                     │
│    4. If defeat: tournament ends early                      │
└─────────────────────────────────────────────────────────────┘
                           ↓
┌─────────────────────────────────────────────────────────────┐
│  COMPLETION (TournamentService.complete_tournament())       │
│  - Award total XP via DemonProgressionService               │
│  - Award stat bonuses (if all rounds won)                   │
│  - Award items (if all rounds won)                          │
│  - Clear assignment from weekly plan                        │
│  - Emit tournament_completed signal                         │
└─────────────────────────────────────────────────────────────┘
```

## Combat Mechanics

### HP Management
- Demon starts at full HP (calculated from Pride + Level)
- Damage persists between rounds
- 20% of max HP healed after each victory (not after final round)
- Defeat in any round = tournament over (keeps partial rewards)

### Difficulty Scaling
Enemy stats multiplied by `difficulty_scaling` value:
- Tier 1: 1.1x (10% stronger each round)
- Tier 2: 1.2x (20% stronger)
- Tier 3: 1.3x (30% stronger)

## Weekly Activity

Tournament counts as demon's weekly activity:
- Mutually exclusive with scheme/quest/training/exploration
- Validated during assignment (energy + level checks)
- Strike status blocks entry

## Signals

```gdscript
# Assignment (during planning)
EventBus.tournament_assigned.emit(demon_id, tournament_id)
EventBus.tournament_unassigned.emit(demon_id, tournament_id)

# Completion (after gauntlet)
EventBus.tournament_completed.emit(demon_id, result_dict)
# result_dict: {tournament_id, rounds_won, total_rounds, completed, xp_gained, stat_rewards, items_awarded}
```

## Design Notes

- **Soul rewards deprecated:** Souls now come from exploration/corruption; tournament soul rewards set to 0
- **Visual-first:** Every round shows a full animated battle via [[CombatSessionService]]
- **Risk-reward:** Higher tiers offer better rewards but require more investment and skill

## Related

- [[Combat System]] - Battle resolution and visuals
- [[CombatFacade]] - Visual combat API
- [[Demon System]] - Tournament participants
- [[Economy System]] - Entry costs and rewards
- [[Week Flow]] - When tournaments execute
