---
type: autoload
domain: system
file: GameState.gd
status: stable
tags:
  - autoload
  - core
  - state
---
# GameState

The central data hub and service locator for the entire game. Initializes and manages the lifecycle of all core managers, services, and facades.

## Overview

GameState is the primary autoload that bootstraps the entire game architecture. It owns references to all managers and provides facade accessors for clean API access.

## Key Responsibilities

- Initialize all managers, services, and facades
- Provide unified API for state access via facades
- Manage story flags and variables
- Coordinate save/load operations

## Facade Accessors

```gdscript
GameState.get_demon_facade()        # Demon management
GameState.get_corruption_facade()   # Corruption state
GameState.get_planning_facade()     # Weekly planning
GameState.get_inventory_facade()    # Items and equipment
GameState.get_mortal_character_facade()  # Mortal targets
GameState.get_story_facade()        # Story progression
GameState.get_realm_facade()        # Realm resources
GameState.get_combat_facade()       # Combat operations
GameState.get_cult_facade()         # Cult management
GameState.get_unlock_facade()       # Unlock system
```

## Key Methods

| Method | Purpose |
|--------|---------|
| `get_*_facade()` | Access domain-specific APIs |
| `get_story_value()` | Read story flag |
| `set_story_value()` | Write story flag |
| `save_all_data()` | Trigger full save |
| `create_state_snapshot()` | Serialize current state |

## Key Constants

| Constant | Purpose |
|----------|---------|
| `REALM_OWNER_ID` | Hell realm identifier |
| `REALM_OWNER_KEY` | Resource ownership key |

## Initialization

GameState uses `GameStateInitializer` to bootstrap in phases:
1. **Phase 1**: Core managers
2. **Phase 2**: Services with dependencies
3. **Phase 3**: Facades

## Related

- [[GameFlow]] - Phase state machine
- [[Autoloads]] - All autoloads
- [[Facades]] - API layer
- [[Managers]] - State owners
- [[PersistenceManager]] - Save/load
