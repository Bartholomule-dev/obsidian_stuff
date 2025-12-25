---
type: service
domain: system
file: SimulationPhaseCoordinator.gd
status: stable
---
# SimulationPhaseCoordinator

Orchestrates the daily execution of simulation phases (Hell, Mortal, Divine, Event) during the game's weekly cycle.

## Overview

SimulationPhaseCoordinator is the central orchestrator for daily simulation. It processes each phase in order and coordinates between all active systems during week execution.

## Key Responsibilities

- Execute daily simulation phases in order
- Coordinate mission execution
- Handle mission beat triggers
- Finalize missions at week end
- Register idle demons for background processing

## Daily Phases

| Phase | Systems Processed |
|-------|-------------------|
| Hell Phase | Demon activities, idle processing |
| Cult Phase | Cult actions, income |
| Mortal Phase | Character updates, need changes |
| Divine Phase | Intervention checks |
| Event Phase | Random event triggers |
| Interruption Phase | Player decisions |

## Key Methods

| Method | Purpose |
|--------|---------|
| `execute_day()` | Process all phases for one day |
| `_execute_missions()` | Run active mission updates |
| `_handle_mission_beat()` | Trigger beat decision flow |
| `finalize_missions_at_week_end()` | Clean up and reward |
| `register_idle_demons()` | Track demons not on activities |

## Dependencies

- [[CorruptionFacade]] - Corruption state access
- [[DemonManagementFacade]] - Demon state access
- [[PlanningFacade]] - Weekly plan access
- [[MissionExecutorService]] - Mission processing
- [[InterventionService]] - Divine intervention checks
- [[Intervention Risk]] - Risk meter access

## Game Loop Integration

Called by [[Week Flow|WeekManager]] to process each day. Iterates through phases and advances the GameFlow calendar.

## Related

- [[Week Flow]] - Weekly cadence
- [[Mission System]] - Mission execution
- [[Event System]] - Event triggering
