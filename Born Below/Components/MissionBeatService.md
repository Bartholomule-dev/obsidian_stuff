---
type: service
domain: mission
file: MissionBeatService.gd
status: stable
---
# MissionBeatService

Maps mission threshold crossings to specific narrative events and constructs their execution context.

## Purpose

Translates mechanical threshold crossings into narrative events with proper context and choices.

## Key Responsibilities

- Categorizes crossings into narrative types (complications, milestones, breaking points)
- Builds full data context for EventSystem with name injection
- Resolves dynamic "verb choices" by injecting demon abilities
- Filters crossings against available authored content

## Key Methods

| Method | Purpose |
|--------|---------|
| `get_beat_event_id(crossing)` | Generate standardized event ID |
| `build_beat_context(crossing, state)` | Prepare variable dictionary |
| `build_choices_with_verbs(...)` | Inject demon abilities into choices |
| `filter_crossings_by_available_beats(...)` | Validate content exists |

## Beat Categories

| Category | Trigger | Example |
|----------|---------|---------|
| Complication | High suspicion | Target notices something |
| Milestone | High leverage | Significant progress |
| Breaking Point | Critical fatigue | Target near corruption |

## Context Building

Injects into event templates:
- `{demon_name}` - Active demon's name
- `{target_name}` - Target character's name
- `{sin_type}` - Current sin focus
- `{verb_1}`, `{verb_2}` - Demon's available verbs

## Related

- [[Mission System]] - System overview
- [[MissionExecutorService]] - Triggers beats
- [[Beats]] - Beat mechanics
- [[Event System]] - Event processing
