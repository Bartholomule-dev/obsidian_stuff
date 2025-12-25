---
type: manager
domain: inventory
file: EquipmentManager.gd
status: partial
---
# EquipmentManager

Manages the demon equipment system, including item validation, assignment to slots, and stat bonus calculation.

## Overview

EquipmentManager handles equipping and unequipping items on demons, validates requirements (level, rank), and calculates combat stat bonuses from equipped gear.

## Key Responsibilities

- Validate equipment requirements (level, rank)
- Assign items to demon gear slots
- Calculate equipment stat bonuses
- Track equipped items per demon

## State

Functional manager - does not own primary data but maintains references to item registry and inventory callbacks.

## Key Methods

| Method | Purpose |
|--------|---------|
| `equip_demon_item()` | Assign item to demon slot |
| `unequip_demon_item()` | Remove item from slot |
| `calculate_equipment_bonuses()` | Sum stat bonuses from gear |
| `get_demon_equipment()` | Retrieve all equipped items |

## Dependencies

- [[RosterManager]] - Demon data access
- [[DemonManager]] - Demon state
- `ItemData` registry - Item definitions

## Equipment Slots

Demons have defined gear slots for different equipment types:
- Weapon slots
- Armor slots
- Accessory slots

## Related

- [[InventoryManager]] - Item storage
- [[DemonProgressionService]] - Level requirements
- [[Combat System]] - Stat bonuses apply here
