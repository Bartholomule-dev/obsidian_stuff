---
type: facade
domain: realm
file: RealmFacade.gd
status: stable
---
# RealmFacade

Public API for realm and entity operations. Manages high-level realm initialization and stat modifications.

## Purpose

Provides access to Hell and Mortal realm coordinators, entity stat operations, and effect application across realms.

## Dependencies

- `_realm_coordinator` - RealmCoordinator
- `_roster_manager` - RosterManager
- `_corruption_manager` - CorruptionManager
- `_game_state` - GameState

## Key Responsibilities

### Realm Access
- `get_hell_realm()` - Access Hell realm state
- `get_mortal_realm()` - Access Mortal realm state
- `get_realm_coordinator()` - Direct coordinator access
- `initialize_realms() -> void` - Initialize both realms

### Entity Stats
- `set_entity_stat(entity_id: String, stat: String, value: int) -> void`
- `adjust_entity_stat(entity_id: String, stat: String, delta: int) -> void`

### Effect Application
- `apply_effect(effect: Dictionary) -> void` - Apply single effect
- `apply_multiple_effects(effects: Array) -> void` - Apply effect batch

## Usage

```gdscript
var realm_facade = GameState.get_realm_facade()

# Get soul essence (via realm coordinator)
var souls = realm_facade.get_realm_coordinator().get_soul_essence()

# Adjust demon stat
realm_facade.adjust_entity_stat(demon_id, "wrath", 5)

# Apply effects from event
realm_facade.apply_multiple_effects([
    {"type": "stat", "target": demon_id, "stat": "pride", "delta": 3},
    {"type": "resource", "resource": "soul_essence", "delta": 50}
])
```

## Related

- [[RealmCoordinator]] - Underlying coordinator
- [[CorruptionFacade]] - Soul essence management
- [[DemonManagementFacade]] - Demon stat access
- [[Economy System]] - Resource flow
