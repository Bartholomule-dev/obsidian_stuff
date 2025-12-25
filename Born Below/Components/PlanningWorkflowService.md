---
type: service
domain: planning
file: PlanningWorkflowService.gd
status: stable
---
# PlanningWorkflowService

Orchestrates the workflow for assigning demons to various activity types during planning.

## Purpose

Provides unified assignment logic across all activity types while enforcing mutual exclusion rules.

## Key Responsibilities

- Validates activity assignments (availability, requirements, conflicts)
- Manages assignment state during planning phase
- Enforces one-activity-per-demon rule
- Coordinates with specialized services for each activity type

## Activity Types Handled

| Type | Destination Service |
|------|---------------------|
| Mission/Scheme | [[MissionExecutorService]] |
| Training | DemonTrainingService |
| Quest | DemonQuestService |
| Exploration | ExplorationCoordinator |
| Tournament | TournamentService |
| Rest/Idle | IdleActivityService |

## Validation Flow

```
can_assign_demon(demon_id, activity_type, activity_id)
    ├── Check demon exists and available
    ├── Check not already assigned this week
    ├── Check activity-specific requirements
    │   ├── Level requirements
    │   ├── Stat requirements
    │   └── Unlock requirements
    └── Return validation result
```

## Assignment Flow

```
assign_demon(demon_id, activity_type, activity_id)
    ├── Validate assignment
    ├── Clear any existing assignment
    ├── Record in weekly plan
    ├── Notify activity-specific service
    └── Emit assignment signal
```

## Related

- [[PlanningFacade]] - Public API
- [[PlanningPhaseManager]] - Plan state
- [[Week Flow]] - Planning phase
- [[Demon System]] - Activity participants
