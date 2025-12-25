---
type: service
domain: exploration
file: ExplorationCoordinator.gd
status: stable
---
# ExplorationCoordinator

Unified public interface for exploration systems, routing calls to the underlying service and managing demon availability.

## Overview

ExplorationCoordinator serves as the facade-like entry point for all exploration operations. It coordinates between UI, service logic, and persistence.

## Key Responsibilities

- Route exploration calls to [[ExplorationService]]
- Manage demon availability during exploration
- Sync exploration state with persistent plan data
- Handle exploration assignment and unassignment

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_exploration()` | Entry point for starting node map mission |
| `process_node_encounter()` | Proxies UI interaction with map nodes |
| `restore_assignments_from_plan()` | Syncs RosterManager with saved plan on load |
| `unassign_demon_from_exploration()` | Clears mission data and releases demon |

## Dependencies

- [[ExplorationService]] - Core exploration logic
- [[PlanningPhaseManager]] - Weekly plan access
- [[RosterManager]] - Demon state management

## Data Structures

| Structure | Purpose |
|-----------|---------|
| `HellWeeklyPlan` | Persistent exploration assignments |
| `ExplorationMap` | Runtime map state |

## Game Loop Integration

- Orchestrates data flow between UI (Planning/Exploration screens) and persistent `HellWeeklyPlan`
- Acts as bridge during both [[Week Flow|Planning Phase]] and week execution

## Related

- [[ExplorationService]] - Underlying service
- [[Exploration System]] - System overview
- [[PlanningFacade]] - Planning access layer
