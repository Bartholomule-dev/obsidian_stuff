---
type: manager
domain: demon
file: RosterManager.gd
status: stable
---
# RosterManager

Central coordinator for the demon collection, managing lifecycle, slotting, and high-level activities of all demon entities.

## Purpose

Acts as the high-level orchestrator for demons, delegating complex state management to specialized services while providing unified access to demon data.

## Key Responsibilities

- Manages demon recruitment, retirement, and lifespan progression via specialized services
- Coordinates assignment of demons to active roster slots (max 3) and tracks availability
- Delegates complex state management (mood, progression, training, memory) to [[DemonManager]] and its 9+ services
- Orchestrates manual player interactions (praise/scold) including cooldown management
- Provides unified access to demon entity data with type-safety through `DemonEntityManager`

## Key Methods

| Method | Purpose |
|--------|---------|
| `initialize()` | Set up roster and dependencies |
| `add_entity()` | Add demon to roster |
| `get_demon()` | Retrieve demon by ID |
| `assign_demon_to_slot()` | Assign demon to active slot |
| `can_praise_demon()` | Check praise cooldown |
| `process_training_week()` | End-of-week training |
| `is_demon_on_mission()` | Check mission assignment |

## Architecture

```
RosterManager (coordinator)
    ├── DemonEntityManager (CRUD storage)
    ├── DemonManager (state coordination)
    │   └── 9+ specialized services
    └── DemonSlotManager (slot assignments)
```

## Related

- [[DemonManagementFacade]] - Public API layer
- [[DemonManager]] - State coordination
- [[Demon System]] - Parent system
- [[PlanningPhaseManager]] - Activity scheduling
