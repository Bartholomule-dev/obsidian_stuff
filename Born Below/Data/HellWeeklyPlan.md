---
type: resource
domain: planning
file: HellWeeklyPlan.gd
status: stable
tags:
  - data
  - planning
  - resource
---
# HellWeeklyPlan

Resource class storing all player assignments and allocations for the upcoming week.

## Overview

HellWeeklyPlan is the central data structure created during the Planning Phase. It captures what each demon will do and what resources are allocated.

## Key Properties

### Assignments
| Property | Description |
|----------|-------------|
| `demon_assignments` | Map of demon → activity |
| `mission_assignments` | Demons on corruption schemes |
| `training_assignments` | Demons in training |
| `exploration_assignments` | Demons exploring |
| `tournament_assignments` | Demons in tournaments |
| `idle_assignments` | Demons resting |

### Resources
| Property | Description |
|----------|-------------|
| `soul_essence_allocated` | Budget for week's activities |
| `cult_action` | Selected cult action |

### State
| Property | Description |
|----------|-------------|
| `week_number` | Which week this plan is for |
| `is_locked` | True once execution begins |

## Assignment Types

Each demon can have exactly ONE assignment:

| Type | Duration | Outcome |
|------|----------|---------|
| Mission | 1 week | Corruption progress |
| Training | 1+ weeks | Stat gains |
| Exploration | 1 week | Resources, discoveries |
| Tournament | 1 week | XP, stat gains |
| Idle/Rest | 1 week | Recovery |

## Lifecycle

```
Planning Phase:
  1. Create empty plan
  2. Player makes assignments
  3. Lock plan

Execution Phase:
  4. Read assignments daily
  5. Process each activity

Results Phase:
  6. Plan archived
```

## Used By

- [[PlanningPhaseManager]] - Plan creation/storage
- [[PlanningFacade]] - Assignment API
- [[WeekManager]] - Execution coordination
- [[SimulationPhaseCoordinator]] - Daily processing

## Related

- [[Week Flow]] - Phase timing
- [[PlanningFacade]] - Assignment interface
- [[Content Catalog]] - Available activities
