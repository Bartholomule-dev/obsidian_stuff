---
type: manager
domain: system
file: WeekManager.gd
status: stable
---
# WeekManager

Orchestrates the core weekly simulation loop, transitioning the game from planning through a 7-day execution cycle to result finalization and state reset.

## Overview

WeekManager is the heartbeat of the game. It drives the weekly cadence that defines the core gameplay loop: plan activities, execute the week day-by-day, then review results.

## Key Responsibilities

- Initiate and manage week execution flow
- Iterate through 7-day cycle
- Coordinate visual presentations during execution
- Execute cult phase (actions, income, heat)
- Finalize week (resources, decay, tracking)
- Evaluate victory/defeat conditions

## Key Methods

| Method | Purpose |
|--------|---------|
| `execute_week()` | Initiate simulation and visual flow |
| `_execute_week_async()` | Iterate 7-day cycle with daily logic |
| `_finalize_week()` | End-of-week wrap-up and resets |
| `_execute_cult_phase()` | Cult actions, income, heat conversion |
| `_evaluate_demo_conditions()` | Check victory/defeat triggers |

## Phase Flow

```
PLANNING → EXECUTING (7 days) → RESULTS → END_WEEK
```

WeekManager advances `GameFlow` through these phases, with the bulk of its work during EXECUTING.

## Coordination

| Component | Role |
|-----------|------|
| [[SimulationPhaseCoordinator]] | Daily phase logic |
| `VisualsCoordinator` | UI and animations |
| `DemonLifecycleCoordinator` | Progression and mood |
| `WeekPerformanceTracker` | Analytics |

## Signals/Events

- `publish_week_completed` - All execution data
- `victory_achieved` - Win state triggers
- `activity_log_*` - Real-time activity feed

## Victory Condition

Demo victory: Corrupt Knight, Bishop, and Queen to Stage 4.
Evaluated via `_evaluate_demo_conditions()` each week.

## Related

- [[Week Flow]] - Phase concepts
- [[SimulationPhaseCoordinator]] - Daily execution
- [[Cult System]] - Cult phase execution
- [[GameFlow]] - Phase state machine
