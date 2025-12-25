---
type: facade
domain: story
file: StoryFacade.gd
status: stable
---
# StoryFacade

Unified interface for story state operations.

## Purpose

Manages story flags and narrative state using nested path syntax.

## Dependencies

- [[StoryStateManager]] - Story flags, nested paths

## Key Responsibilities

### Story State Operations
- `get_story_value(path, default)` - Get value at path
- `has_story_value(path)` - Check existence
- `set_story_value(path, value)` - Set value
- `increment_story_value(path, delta)` - Increment numeric
- `clear_story_value(path)` - Remove value

### Full State
- `get_story_state()` - Complete state dictionary
- `set_story_state(state)` - Load from save

## Path Syntax

Story values use dot-notation paths:

```gdscript
# Set a flag
story_facade.set_story_value("demons.asmodeus.unlocked", true)

# Check a flag
if story_facade.get_story_value("quests.first_corruption.completed", false):
    # ...

# Increment a counter
story_facade.increment_story_value("stats.total_corruptions")
```

## Common Paths

| Path Pattern | Purpose |
|-------------|---------|
| `demons.{id}.unlocked` | Demon unlock flags |
| `schemes.{id}.unlocked` | Scheme unlock flags |
| `quests.{id}.completed` | Quest completion |
| `achievements.{id}` | Achievement flags |
| `stats.*` | Numeric counters |

## Related

- [[StoryStateManager]] - State owner
- [[UnlockFacade]] - Uses story flags for unlocks
