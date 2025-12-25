---
type: facade
domain: inventory
file: InventoryFacade.gd
status: stable
---
# InventoryFacade

Unified interface for inventory operations.

## Purpose

Manages items, inventories (realm/character), crafting, equipment access, and event unlocks.

## Dependencies

- [[InventoryManager]] - All inventory operations

## Key Responsibilities

### Item Retrieval
- `get_item(item_id)` - Get item definition
- `get_items()` - All items
- `get_items_by_tag(tag)` - Filter by tag
- `get_items_for_character(character_id)` - Usable items

### Inventory Operations
- `get_item_quantity(item_id, owner_id)` - Quantity in inventory
- `has_item(item_id, owner_id, quantity)` - Check availability
- `add_item(item_id, quantity, owner_id)` - Add to inventory
- `remove_item(item_id, quantity, owner_id)` - Remove from inventory
- `consume_item(item_id, quantity, owner_id)` - Use and remove

### Inventory Views
- `get_character_inventory(character_id)` - Character's items
- `get_realm_inventory()` - Hell realm items
- `get_all_inventories()` - Everything
- `get_inventory_state()` - Full snapshot

### Equipment
- `get_equipped_items(demon_id)` - Demon's equipment
  - Returns `{weapon: "", armor: "", accessory: ""}`

### Crafting
- `can_craft_item(item_id, crafter_id)` - Check craftability
- `craft_item(item_id, crafter_id)` - Execute craft

### Passive Effects
- `get_item_passive_effects(owner_id)` - Active passive effects

### Event Unlocks
- `is_event_unlocked(event_id)` - Check event access
- `is_event_pack_unlocked(pack_id)` - Check pack access

## Related

- [[InventoryManager]] - State owner
- [[EquipmentManager]] - Equipment logic
- [[CraftingManager]] - Crafting logic
