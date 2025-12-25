---
type: service
domain: mission
file: MissionExecutorService.gd
status: stable
---
# MissionExecutorService

Executes daily mission simulation logic, including meter updates and narrative beat detection.

## Purpose

The engine that runs mission simulation each day, updating meters and triggering narrative events.

## Key Responsibilities

- Calculates and applies daily changes to Leverage, Suspicion, Moral Fatigue
- Detects "zone crossings" that trigger narrative beats at thresholds
- Enforces grace rules and cooldowns to prevent beat spam
- Coordinates with InterventionRiskMeter for divine interventions

## Key Methods

| Method | Purpose |
|--------|---------|
| `execute_day(state, context)` | Primary daily simulation entry |
| `get_meter_preview(state, context)` | Forecast next-day changes for UI |
| `prepare_week_end(state)` | Weekly decay and cooldown reset |
| `_check_intervention_checkpoint(...)` | Divine intervention check |

## Daily Flow

```
execute_day()
    ├── Calculate meter deltas
    ├── Apply changes to state
    ├── Detect zone crossings
    ├── Check for beats to trigger
    ├── Check intervention threshold
    └── Return updated state + events
```

## Zone Thresholds

Meters trigger beats when crossing:
- **25%** - Early threshold
- **50%** - Mid threshold
- **75%** - Late threshold
- **90%** - Critical threshold

## Grace Rules

- No duplicate beats same day
- Weekly cooldowns per beat type
- Minimum days between same beat

## Related

- [[Mission System]] - System overview
- [[MissionBeatService]] - Beat event construction
- [[Beats]] - Threshold mechanics
- [[Intervention Risk]] - Divine checks
