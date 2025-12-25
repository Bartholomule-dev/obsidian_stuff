---
type: facade
domain: story
file: StoryFacade.gd
status: stable
---
# StoryFacade

Public API for persistent story state. Manages narrative flags and nested story variables.

## Purpose

Provides a unified interface for interacting with story flags and nested narrative state. Follows read-bypass pattern for fast access.

## Dependencies

- `_story_state_manager` - StoryStateManager

## Key Responsibilities

### Value Access
- `get_story_value(path: String, default_value: Variant) -> Variant` - Get nested value
- `has_story_value(path: String) -> bool` - Check if path exists
- `set_story_value(path: String, value: Variant) -> Variant` - Set nested value
- `increment_story_value(path: String, delta: int) -> int` - Increment counter
- `clear_story_value(path: String) -> void` - Remove value

### State Bulk Operations
- `get_story_state() -> Dictionary` - Get entire state
- `set_story_state(state: Dictionary) -> void` - Replace entire state

## Path Syntax

Story values use dot-notation paths:

```gdscript
# Simple flags
story.set_story_value("knight.first_encounter", true)
story.set_story_value("bishop.corruption_started", true)

# Nested values
story.set_story_value("queen.schemes.betrayal_count", 3)

# Counters
story.increment_story_value("total_corruptions", 1)
```

## Usage

```gdscript
var story = GameState.get_story_facade()

# Check if player has seen tutorial
if not story.has_story_value("tutorial.completed"):
    show_tutorial()
    story.set_story_value("tutorial.completed", true)

# Track corruption milestones
var corruptions = story.get_story_value("stats.total_corruptions", 0)
story.set_story_value("stats.total_corruptions", corruptions + 1)

# Conditional unlocks
if story.get_story_value("knight.stage", 0) >= 2:
    unlock_knight_schemes()
```

## Common Story Paths

| Path | Type | Purpose |
|------|------|---------|
| `tutorial.completed` | bool | Tutorial state |
| `[character].first_encounter` | bool | First meeting flag |
| `[character].stage` | int | Corruption stage mirror |
| `achievements.[id]` | bool | Achievement unlocks |
| `stats.weeks_played` | int | Game duration |

## Related

- [[StoryStateManager]] - State owner
- [[Event System]] - Story-driven events
- [[UnlockFacade]] - Story-based unlocks
