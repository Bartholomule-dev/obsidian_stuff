---
type: facade
domain: unlock
file: UnlockFacade.gd
status: stable
---
# UnlockFacade

Unified interface for unlock operations.

## Purpose

Checks and applies unlocks for demons, schemes, decrees, defenses, items, and abilities.

## Dependencies

- [[UnlockableManager]] - Unlock state, checks
- [[RosterManager]] - Demon slot management
- [[PlanningPhaseManager]] - Content lookups
- [[InventoryManager]] - Item lookups

## Key Responsibilities

### Decree Unlocks
- `is_decree_unlocked(decree_id)` - Check status
- `unlock_decree(decree_id)` - Unlock and set flag

### Defense Unlocks
- `is_defense_unlocked(defense_id)` - Check status
- `unlock_defense(defense_id)` - Unlock and set flag

### Demon Unlocks
- `is_demon_unlocked(demon_id)` - Check status
- `unlock_demon(demon_id)` - Unlock, auto-slot, set available

### Scheme Unlocks
- `is_scheme_unlocked(scheme_id)` - Check status
- `unlock_scheme(scheme_id)` - Unlock and set flag
- `check_scheme_demon_requirements(scheme, roster)` - Check if any demon qualifies

### Item Unlocks
- `is_item_unlocked(item_id)` - Check status
- `unlock_item(item_id)` - Unlock and set flag

### Character Ability Unlocks
- `is_character_ability_unlocked(ability_id)` - Check status
- `unlock_character_ability(ability_id)` - Unlock and set flag

## Unlock Pattern

Most unlocks follow this pattern:
1. Check `unlocked_by_default` on resource
2. If false, check story flag `{category}.{id}.unlocked`
3. Unlock sets the story flag to true

## Demon Auto-Slotting

When `unlock_demon()` is called:
1. Sets story flag
2. Finds first empty, unlocked slot
3. Assigns demon to slot
4. Sets demon as available

## Related

- [[StoryFacade]] - Story flags storage
- [[UnlockableManager]] - Unlock logic
