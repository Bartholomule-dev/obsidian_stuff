---
type: service
domain: combat
file: TournamentService.gd
status: stable
---
# TournamentService

Manages tournament assignments, validation, and reward distribution.

## Overview

TournamentService handles the "business logic" of tournaments: validating entry requirements, processing costs, and distributing rewards after completion.

**File:** `scripts/core/services/TournamentService.gd`

## Key Responsibilities

- Validate tournament entry requirements (level, energy, strike status)
- Process entry costs (soul essence + energy)
- Track tournament assignments in weekly plan
- Calculate and distribute rewards based on performance

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_tournament(demon_id, tournament_id)` | Validate + pay costs + store assignment |
| `unassign_demon_from_tournament(demon_id)` | Remove assignment, emit signal |
| `is_demon_in_tournament(demon_id)` | Check if demon has active assignment |
| `get_tournament_assignment(demon_id)` | Get tournament ID for demon |
| `get_all_tournament_assignments()` | Get all demon→tournament mappings |
| `complete_tournament(demon_id, rounds_won, total_soul, total_xp)` | Distribute rewards |

## Assignment Validation

Before assignment, validates:
1. Tournament exists in [[PlanningPhaseManager]] registry
2. Demon not on strike (`is_on_strike` flag)
3. Demon meets level requirement (`required_demon_level`)
4. Demon has sufficient energy (`energy_cost`)
5. Player can afford soul essence cost (`soul_essence_cost`)

## Reward Distribution

On completion, `complete_tournament()`:
1. Awards soul essence via [[RealmCoordinator]] (if any)
2. Awards XP via [[DemonProgressionService]]
3. Applies stat bonuses directly to demon (if all rounds won)
4. Adds items via [[InventoryFacade]] (if all rounds won)
5. Clears assignment from [[HellWeeklyPlan]]
6. Emits `tournament_completed` signal

## Dependencies

| Dependency | Purpose |
|------------|---------|
| [[RosterManager]] | Demon availability, strike status |
| [[PlanningPhaseManager]] | Tournament template registry |
| [[DemonProgressionService]] | XP awards |
| [[InventoryFacade]] | Item rewards |
| [[GameState]] | State access |

## Signals Emitted

```gdscript
EventBus.tournament_assigned.emit(demon_id, tournament_id)
EventBus.tournament_unassigned.emit(demon_id, tournament_id)
EventBus.tournament_completed.emit(demon_id, result_dict)
```

## Related

- [[TournamentController]] - Gauntlet execution and visuals
- [[Tournament System]] - System overview
- [[HellWeeklyPlan]] - Assignment storage
