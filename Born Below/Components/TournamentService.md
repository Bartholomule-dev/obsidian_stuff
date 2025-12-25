---
type: service
domain: combat
file: TournamentService.gd
status: stable
---
# TournamentService

Manages demon participation in combat tournaments, including requirement validation, entry costs, and reward distribution.

## Overview

TournamentService handles the tournament gauntlet system where demons compete in multi-round combat challenges for progressive rewards.

## Key Responsibilities

- Validate tournament entry requirements (level, energy)
- Process entry costs (soul essence payment)
- Track tournament progress through rounds
- Calculate and distribute rewards based on performance

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_tournament()` | Validates requirements and handles entry payment |
| `complete_tournament()` | Calculates rewards based on rounds won |
| `is_demon_in_tournament()` | Checks assignment status |
| `unassign_demon_from_tournament()` | Removes demon and clears plan data |

## Dependencies

- [[RosterManager]] - Demon availability
- [[PlanningPhaseManager]] - Weekly plan management
- [[DemonProgressionService]] - XP and stat rewards
- [[GameState]] - State access

## Data Structures

| Structure | Purpose |
|-----------|---------|
| `HellWeeklyPlan` | Tournament assignments |
| `TournamentTemplate` | Tournament definitions (Resource) |

## Reward System

Rewards scale with rounds won:
- Soul essence bonuses
- XP for participating demons
- Potential stat bonuses
- Item drops

## Game Loop Integration

- **Planning Phase**: Tournament entry locked in
- **Execution Phase**: Rounds simulated or played
- **Results Phase**: Completion triggered by [[Week Flow|WeekManager]] or combat controllers

## Related

- [[Combat System]] - Battle resolution
- [[CombatResolutionService]] - Combat mechanics
- [[Tournament System]] - System overview
