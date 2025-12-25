---
type: service
domain: mission
file: MissionMeterService.gd
status: stable
---
# MissionMeterService

Orchestrates numerical progression of missions via three core meters: Leverage, Suspicion, and Moral Fatigue.

## Purpose

The math engine behind mission progression - calculates daily changes and detects narrative triggers.

## Key Responsibilities

- Calculates daily meter deltas based on demon effectiveness, verbs, and pressure/subtlety
- Detects and sequences zone crossings for narrative beats at thresholds
- Enforces grace rule limiting beats to one per day
- Handles weekly decay (Suspicion resets, others persist partially)

## Key Methods

| Method | Purpose |
|--------|---------|
| `calculate_daily_deltas()` | Compute day's meter changes |
| `detect_zone_crossings()` | Find threshold triggers |
| `apply_grace_rule()` | Limit beats per day |
| `apply_weekly_decay()` | End-of-week reset |

## Zone Thresholds

| Threshold | Trigger |
|-----------|---------|
| 20 | Early zone |
| 40 | Mid zone |
| 60 | Late zone |
| 80 | Critical zone |

## Meter Formulas

**Leverage:** Demon effectiveness × Verb bonus × Pressure setting
**Suspicion:** Base rate × (1 - Subtlety) × Target awareness
**Moral Fatigue:** Leverage overflow + sustained pressure bonus

## Grace Rule

Only one beat can trigger per day. Additional crossings queue for subsequent days to prevent narrative overload.

## Related

- [[Mission System]] - System overview
- [[MissionExecutorService]] - Uses this for daily updates
- [[Beats]] - What zone crossings trigger
