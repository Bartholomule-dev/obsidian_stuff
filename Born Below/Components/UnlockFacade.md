---
type: facade
domain: unlock
file: UnlockFacade.gd
status: stable
---
# UnlockFacade

Public API for unlock state management. Centralizes unlock logic for demons, schemes, items, and other game elements.

## Purpose

Provides consistent unlock checking and unlocking operations across diverse game elements, ensuring unlock state is synchronized with story flags and manager states.

## Dependencies

- `_unlockable_manager` - UnlockableManager
- `_roster_manager` - RosterManager
- `_planning_manager` - PlanningManager
- `_inventory_manager` - InventoryManager

## Key Responsibilities

### Decree Unlocks
- `is_decree_unlocked(decree_id: String) -> bool`
- `unlock_decree(decree_id: String) -> void`

### Defense Unlocks
- `is_defense_unlocked(defense_id: String) -> bool`
- `unlock_defense(defense_id: String) -> void`

### Demon Unlocks
- `is_demon_unlocked(demon_id: String) -> bool`
- `unlock_demon(demon_id: String) -> void`

### Scheme Unlocks
- `is_scheme_unlocked(scheme_id: String) -> bool`
- `unlock_scheme(scheme_id: String) -> void`

### Item Unlocks
- `is_item_unlocked(item_id: String) -> bool`
- `unlock_item(item_id: String) -> void`

### Requirement Checking
- `check_scheme_demon_requirements(scheme_data, roster_manager) -> Dictionary`

## Usage

```gdscript
var unlock = GameState.get_unlock_facade()

# Check if scheme is available
if unlock.is_scheme_unlocked("knight_tournament_training"):
    show_scheme_option()

# Unlock demon after milestone
unlock.unlock_demon("night_terror")

# Check scheme requirements
var req_check = unlock.check_scheme_demon_requirements(scheme, roster_manager)
if req_check.met:
    enable_scheme_button()
else:
    show_requirements(req_check.missing)
```

## Unlock Sources

| Element | Unlocked By |
|---------|------------|
| Demons | Story progression, corruption milestones |
| Schemes | Target corruption stage |
| Items | Discovery, crafting, rewards |
| Decrees | Story flags |
| Defenses | Character awareness level |

## Signal Connections

UnlockableManager connects to `EventBus.character_corrupted` to automatically trigger corruption-based unlocks when characters advance stages.

## Related

- [[UnlockableManager]] - State owner
- [[StoryFacade]] - Story flag checks
- [[Demon System]] - Demon unlocks
- [[Corruption System]] - Stage-based unlocks
