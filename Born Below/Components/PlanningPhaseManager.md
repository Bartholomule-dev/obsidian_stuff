---
type: manager
domain: planning
file: PlanningPhaseManager.gd
status: stable
---
# PlanningPhaseManager

Manages state and resource registries for the weekly planning loop, including activity availability and threat intelligence.

## Purpose

Central registry for all planning-related content and enforcer of the "One Activity Per Week" rule.

## Key Responsibilities

- Maintains `HellWeeklyPlan` resource tracking all scheduled demon activities
- Manages "Threat Intel" level (0-3) for divine intervention knowledge
- Acts as registry for training, explorations, tournaments, and domains
- Enforces mutual exclusion - prevents demons from being double-booked
- Handles automatic unlocking of default-available activities

## Key Methods

| Method | Purpose |
|--------|---------|
| `set_threat_intel_level()` | Update intel level |
| `get_unlocked_training_activities()` | Available training |
| `reset_weekly_plan()` | Clear for new week |
| `can_assign_demon_to_activity()` | Validate assignment |
| `get_domains_for_target()` | Get target domains |

## Threat Intel Levels

| Level | Knowledge |
|-------|-----------|
| 0 | No divine insight |
| 1 | Basic warnings |
| 2 | Detailed forecasts |
| 3 | Full intervention visibility |

## Content Registries

- Training Activities
- Weekly Activities
- Explorations
- Tournaments
- Domains

## Related

- [[PlanningFacade]] - Public API layer
- [[Week Flow]] - Planning phase
- [[RosterManager]] - Demon assignments
- [[UnlockableManager]] - Content unlocks
