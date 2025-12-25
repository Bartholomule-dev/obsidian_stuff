---
type: manager
domain: story
file: StoryStateManager.gd
status: stable
---
# StoryStateManager

Manages a hierarchical, persistent dictionary of game state flags using dot-notated paths.

## Purpose

Central storage for all narrative flags and unlock states with safe path-based access.

## Key Responsibilities

- Provides safe, validated access to nested state values
- Enforces limits on path depth and length
- Automatically cleans up empty dictionary branches
- Triggers state-change events via EventBus

## Key Methods

| Method | Purpose |
|--------|---------|
| `get_story_value(path, default)` | Read value at path |
| `set_story_value(path, value)` | Write value at path |
| `increment_story_value(path, delta)` | Increment numeric |
| `has_story_value(path)` | Check existence |
| `clear_story_value(path)` | Remove value |

## Path Syntax

Dot-notation for nested access:

```gdscript
# Set a flag
set_story_value("unlocked.demons.asmodeus", true)

# Read with default
get_story_value("stats.total_corruptions", 0)

# Increment counter
increment_story_value("stats.schemes_completed")
```

## Common Path Patterns

| Pattern | Purpose |
|---------|---------|
| `unlocked.demons.{id}` | Demon unlock flags |
| `unlocked.schemes.{id}` | Scheme unlock flags |
| `quests.{id}.completed` | Quest completion |
| `achievements.{id}` | Achievement flags |
| `stats.*` | Numeric counters |

## Safety Features

- Maximum path depth enforced
- Maximum path length enforced
- Auto-cleanup of empty branches
- Validation on all operations

## Related

- [[StoryFacade]] - Public API layer
- [[UnlockableManager]] - Uses story flags
- [[PersistenceManager]] - Save/load state
