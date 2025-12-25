---
type: manager
domain: demon
file: DemonTrainingManager.gd
status: stable
---
# DemonTrainingManager

Stores and manages active training assignment state, including durations and elapsed time.

## Overview

DemonTrainingManager tracks which demons are in training, what training they're doing, and how long they've been at it. Training is a multi-week activity that improves demon stats.

## Key Responsibilities

- Store active training assignments
- Track training duration and progress
- Progress training by week
- Handle training completion/cancellation

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_training()` | Start training assignment |
| `unassign_demon_from_training()` | Cancel training |
| `progress_training_week()` | Advance training by one week |

## Dependencies

None - pure state manager.

## Training State

| Field | Purpose |
|-------|---------|
| Training ID | Which training activity |
| Duration | Total weeks required |
| Elapsed | Weeks completed |
| Target Stats | Stats being improved |

## Training Flow

1. Player assigns demon to training during Planning
2. Training locks demon for duration
3. Each week, `progress_training_week()` advances
4. On completion, stat bonuses applied
5. Demon freed for new assignment

## Related

- [[Demon System]] - Parent system
- [[DemonProgressionService]] - Stat application
- [[PlanningFacade]] - Training assignment
- [[Week Flow]] - Weekly progression
