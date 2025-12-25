---
type: autoload
domain: system
file: GameFlow.gd
status: stable
tags:
  - autoload
  - core
  - flow
---
# GameFlow

Orchestrates the high-level game loop, managing transitions between week phases and tracking calendar progression.

## Overview

GameFlow is the state machine that drives the weekly cycle. It tracks which phase the game is in and coordinates transitions between Planning, Executing, Results, and End Week.

## Phase Enum

```gdscript
enum Phase {
    PLANNING,    # Player assigns demons to activities
    EXECUTING,   # 7-day simulation runs
    RESULTS,     # Week summary displayed
    END_WEEK     # Reset and prepare next week
}
```

## Phase Flow

```
PLANNING → EXECUTING → RESULTS → END_WEEK
    ↑                                 |
    └─────────────────────────────────┘
```

## Key Properties

| Property | Purpose |
|----------|---------|
| `current_phase` | Current Phase enum value |
| `current_week` | Week number (via GameCalendar) |
| `current_day` | Day within week (1-7) |

## Key Methods

| Method | Purpose |
|--------|---------|
| `advance_phase()` | Transition to next phase |
| `advance_day()` | Increment day, check week end |
| `is_phase(phase)` | Check current phase |
| `transition_to(phase)` | Direct phase change |

## Phase Responsibilities

| Phase | What Happens |
|-------|--------------|
| **PLANNING** | Player assigns activities, equips verbs |
| **EXECUTING** | [[WeekManager]] runs 7-day simulation |
| **RESULTS** | [[EndOfWeekSummaryModal]] displays |
| **END_WEEK** | Resets, cooldowns, prepare next week |

## Coordinates With

- [[GameState]] - Data retrieval for resets
- `GameCalendar` - Time tracking
- [[WeekManager]] - Triggers phase logic
- `EventBus` - Emits flow signals

## Signals

- `phase_changed(old_phase, new_phase)`
- `day_advanced(day)`
- `week_completed(week_number)`

## Related

- [[Week Flow]] - Conceptual overview
- [[GameState]] - Central state hub
- [[WeekManager]] - Execution coordinator
- [[Autoloads]] - All autoloads
