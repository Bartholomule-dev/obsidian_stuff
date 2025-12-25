---
type: manager
domain: inventory
file: InventoryManager.gd
status: stable
---
# InventoryManager

Manages core item storage, quantity tracking, and item effects while delegating specialized functions to equipment and crafting sub-managers.

## Purpose

Central item management with delegation to specialized sub-managers for equipment and crafting.

## Key Responsibilities

- Tracks item quantities across Realm inventory and character-specific inventories
- Handles "On Acquire" and "On Consume" effects through `EffectProcessor`
- Delegates demon equipment logic to [[EquipmentManager]]
- Coordinates crafting through [[CraftingManager]]
- Maintains "Story State" index of owned items for narrative reactions

## Key Methods

| Method | Purpose |
|--------|---------|
| `add_item()` | Add item to inventory |
| `consume_item()` | Use and remove item |
| `get_total_item_quantity()` | Count across all inventories |
| `equip_demon_item()` | Equip item to demon |
| `craft_item()` | Execute crafting recipe |
| `refresh_item_story_state()` | Update narrative index |

## Architecture

```
InventoryManager (coordinator)
    ├── Item Storage (quantities)
    ├── EquipmentManager (demon gear)
    ├── CraftingManager (recipes)
    └── Story State Index (narrative)
```

## Inventory Types

| Type | Owner | Purpose |
|------|-------|---------|
| Realm | Hell | Global storage |
| Character | Demon/Mortal | Personal items |

## Related

- [[InventoryFacade]] - Public API layer
- [[EquipmentManager]] - Equipment logic
- [[CraftingManager]] - Crafting logic
- [[Economy System]] - Item economy
