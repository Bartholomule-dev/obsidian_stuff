---
type: manager
domain: economy
file: CraftingManager.gd
status: partial
---
# CraftingManager

Handles item creation logic, including recipe validation, material consumption, and automatic rollback on failure.

## Overview

CraftingManager enables players to create items from materials. It validates recipes, consumes ingredients, and applies item effects through the effect pipeline.

## Key Responsibilities

- Validate crafting recipe requirements
- Consume crafting materials
- Create crafted items
- Handle rollback on crafting failure
- Apply item effects via EffectProcessor

## State

Functional manager - uses item registry reference and inventory callbacks for state manipulation.

## Key Methods

| Method | Purpose |
|--------|---------|
| `can_craft_item()` | Check if crafting is possible |
| `craft_item()` | Execute crafting with material consumption |
| `_resolve_crafting_owner()` | Determine item owner |
| `_prepare_item_effects()` | Set up effects for crafted item |

## Dependencies

- [[RosterManager]] - Demon access for crafting owner
- `EffectProcessor` - Apply item effects
- [[GameState]] - State access for effects

## Crafting Flow

1. Validate recipe requirements
2. Check material availability
3. Consume materials from inventory
4. Create new item
5. Apply any immediate effects
6. Rollback if any step fails

## Related

- [[InventoryManager]] - Material storage
- [[Economy System]] - Resource consumption
- [[Data Resources]] - Recipe definitions
