---
type: manager
domain: realm
file: RealmCoordinator.gd
status: stable
---
# RealmCoordinator

Orchestrates the dual-realm system (Hell and Mortal) and provides unified interface for realm-wide statistics and resources.

## Purpose

Owns and initializes both realms, managing the central Soul Reservoir and providing standardized stat access.

## Key Responsibilities

- Owns and initializes `HellRealm` (Soul Essence, Power) and `MortalRealm` (Prosperity, Corruption)
- Maintains legacy `RealmData` reference for backwards compatibility
- Provides standardized stat accessors abstracting realm differences
- Manages the central "Soul Reservoir" - primary currency for Hell

## Key Methods

| Method | Purpose |
|--------|---------|
| `initialize_realms()` | Set up dual-realm system |
| `get_soul_essence()` | Current soul essence |
| `adjust_soul_essence()` | Modify soul essence |
| `get_realm_stat()` | Get stat from either realm |
| `set_realm_stat()` | Set stat on either realm |
| `get_mortal_realm()` | Access mortal realm |
| `get_hell_realm()` | Access hell realm |

## Dual Realm System

```
RealmCoordinator
    ├── HellRealm
    │   ├── Soul Essence (currency)
    │   └── Power (influence)
    └── MortalRealm
        ├── Prosperity
        └── Corruption levels
```

## Related

- [[RealmFacade]] - Public API layer
- [[Economy System]] - Soul essence usage
- [[CorruptionManager]] - Corruption tracking
