---
type: manager
domain: system
file: PersistenceManager.gd
status: stable
---
# PersistenceManager

Orchestrates serialization and restoration of entire game state via snapshots and resource saving.

## Overview

PersistenceManager handles save/load functionality. It coordinates with all managers to create complete state snapshots that can be saved to disk and restored.

## Key Responsibilities

- Save all game data to persistent storage
- Create in-memory state snapshots
- Restore game state from snapshots
- Coordinate with all managers for serialization

## State

Functional manager - orchestrates state across GameState and its child managers rather than owning data directly.

## Key Methods

| Method | Purpose |
|--------|---------|
| `save_all_data()` | Persist complete game state |
| `create_state_snapshot()` | Create in-memory snapshot |
| `restore_state_snapshot()` | Load state from snapshot |
| `_update_demon_from_snapshot()` | Restore individual demon state |

## Dependencies

- [[GameState]] - Central state access
- `ResourceLoader` - Godot resource loading
- `VariantUtils` - Serialization utilities
- All core Managers - State sources

## Snapshot Contents

A complete snapshot includes:
- Demon roster and progression
- Mortal character states
- Corruption progress
- Inventory contents
- Story flags
- Week/calendar state

## Use Cases

- **Save/Load System**: Player saving and loading games
- **Testing**: State isolation between tests
- **Game Lifecycle**: Clean state restoration

## Related

- [[GameState]] - Central state coordination
- [[Autoloads]] - Global state access
- All [[Managers]] - State providers
