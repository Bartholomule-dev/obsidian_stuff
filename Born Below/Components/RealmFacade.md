---
type: facade
domain: realm
file: RealmFacade.gd
status: stable
---
# RealmFacade

Unified interface for realm and entity stat operations.

## Purpose

Provides access to Hell/Mortal realms, entity stat operations, and effect application.

## Dependencies

- [[RealmCoordinator]] - Realm initialization, accessors
- [[RosterManager]] - Entity lookups
- EffectProcessor - Effect application
- [[CorruptionManager]] - Late-bound

## Key Responsibilities

### Realm Accessors
- `get_realm()` - Legacy realm (backward compat)
- `get_hell_realm()` - Hell realm
- `get_mortal_realm()` - Mortal realm
- `get_realm_coordinator()` - Advanced operations

### Realm Initialization
- `initialize_realms()` - Initialize dual-realm system

### Entity Stat Operations
- `set_entity_stat(entity_id, stat, value)` - Set with notification
- `adjust_entity_stat(entity_id, stat, delta)` - Adjust with notification

### Effect Application
- `apply_effect(effect)` - Single effect
- `apply_multiple_effects(effects)` - Multiple effects

## Dual Realm System

The game has two realms:
- **Hell Realm** - Where demons reside, soul essence stored
- **Mortal Realm** - Where corruption targets live

## Effect Dictionary Format

```gdscript
{
    "type": "stat_change",
    "target": "demon_id",
    "stat": "wrath",
    "value": 5
}
```

## Related

- [[RealmCoordinator]] - State owner
- [[CorruptionManager]] - Corruption state
