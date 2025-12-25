---
type: service
domain: demon
file: DemonHistoryService.gd
status: stable
---
# DemonHistoryService

Tracks historical events, performance snapshots, and milestone accomplishments for individual demons.

## Overview

DemonHistoryService maintains the complete history of each demon's career - every mission, achievement, and weekly performance. This feeds into legacy calculations and the Hall of Fame.

## Key Responsibilities

- Record significant demon events
- Create weekly performance snapshots
- Build demon timelines
- Calculate lifetime statistics

## Key Methods

| Method | Purpose |
|--------|---------|
| `record_event()` | Log significant event to history |
| `record_weekly_snapshot()` | Capture weekly performance |
| `get_demon_timeline()` | Retrieve full event history |
| `get_lifetime_stats()` | Calculate career statistics |

## Dependencies

- `GameCalendar` - Timestamp events

## History Events

Events recorded include:
- Mission completions
- Level-ups
- Training completions
- Quest achievements
- Notable combat victories
- Personality shifts

## Use Cases

- **Retirement**: Calculate legacy bonuses from accomplishments
- **Hall of Fame**: Display career highlights
- **UI**: Show demon timeline in roster panel
- **Memories**: Context for memory formation

## Related

- [[Demon System]] - Parent system
- [[DemonLifecycleService]] - Uses for retirement
- [[Memory System]] - Feeds memory formation
- [[DemonProgressionService]] - Level-up events
