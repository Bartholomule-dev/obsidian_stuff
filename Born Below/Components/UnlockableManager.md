---
type: manager
domain: unlock
file: UnlockableManager.gd
status: stable
---
# UnlockableManager

Generic, centralized system for managing the unlocked/locked state of all game resources via story flags.

## Purpose

Standardizes unlock logic across all content types, eliminating duplicated unlock checks throughout the codebase.

## Key Responsibilities

- Standardizes unlock logic for Decrees, Demons, Schemes, Items, Quests, and more
- Checks for `unlocked_by_default` flags on resource data
- Evaluates "unlock gates" for schemes (required demon levels, stat thresholds)
- Processes permanent unlocks granted as corruption rewards

## Key Methods

| Method | Purpose |
|--------|---------|
| `is_unlocked()` | Check if resource is unlocked |
| `unlock()` | Unlock a resource |
| `check_scheme_demon_requirements()` | Validate scheme prerequisites |
| `process_corruption_benefits()` | Apply corruption rewards |

## Unlock Flow

```
is_unlocked(category, id, resource)
    ├── Check unlocked_by_default on resource
    ├── Check story flag: {category}.{id}.unlocked
    └── Return true/false
```

## Categories

- `demons` - Demon unlocks
- `schemes` - Corruption scheme unlocks
- `decrees` - Infernal decree unlocks
- `items` - Item unlocks
- `quests` - Quest unlocks
- `abilities` - Character ability unlocks

## Related

- [[UnlockFacade]] - Public API layer
- [[StoryStateManager]] - Flag storage
- [[RosterManager]] - Demon unlock effects
