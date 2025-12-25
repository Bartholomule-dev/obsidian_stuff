---
type: service
domain: demon
file: DemonLifecycleService.gd
status: stable
---
# DemonLifecycleService

Manages demon aging, personality-based lifespan calculations, and the end-of-service retirement workflow.

## Overview

DemonLifecycleService handles the full lifecycle of demons from recruitment through retirement. Demons age over time and eventually retire based on their personality archetype.

## Key Responsibilities

- Track demon age progression
- Calculate personality-based lifespans
- Detect retirement eligibility
- Execute retirement workflow with legacy bonuses

## Key Methods

| Method | Purpose |
|--------|---------|
| `increment_age()` | Age demon by one week |
| `check_retirement_due()` | Determine if retirement triggered |
| `retire_demon()` | Execute full retirement workflow |
| `calculate_legacy_bonuses()` | Compute career accomplishment bonuses |

## Dependencies

- [[RosterManager]] - Demon roster access
- [[DemonHistoryService]] - Career history for legacy
- `DemonDialogueService` - Retirement dialogue
- `GameCalendar` - Time tracking

## Retirement Flow

1. Demon reaches personality-based lifespan
2. Retirement warning event triggered
3. Final week of service
4. Legacy bonuses calculated from history
5. Demon removed from active roster
6. Career summary preserved

## Related

- [[Demon System]] - Parent system
- [[DemonHistoryService]] - Lifetime accomplishments
- [[Memory System]] - Retirement memories
- [[Personality Evolution]] - Lifespan modifiers
