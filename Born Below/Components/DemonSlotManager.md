---
type: manager
domain: demon
file: DemonSlotManager.gd
status: stable
---
# DemonSlotManager

Maintains the pure state of the 3-slot roster system, including slot assignments and unlock statuses.

## Overview

DemonSlotManager tracks which demons are assigned to the active 3-slot roster and which slots are unlocked. Only slotted demons can be assigned to weekly activities.

## Key Responsibilities

- Track slot assignments (3 slots)
- Manage slot unlock state
- Validate slot availability
- Handle slot reassignment

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_to_slot()` | Place demon in roster slot |
| `remove_from_slot()` | Remove demon from slot |
| `unlock_slot()` | Enable additional slot |
| `is_demon_slotted()` | Check if demon is in roster |

## Dependencies

- `TypingUtils` - Type utilities

## Slot System

| Slot | Default State |
|------|---------------|
| Slot 1 | Unlocked |
| Slot 2 | Unlocked |
| Slot 3 | Locked (demo: unlocked) |

## Constraints

- Only 3 active slots maximum
- One demon per slot
- Unslotted demons cannot be assigned activities
- Slot unlock is permanent progression

## Related

- [[RosterManager]] - Demon entity storage
- [[Demon System]] - Parent system
- [[PlanningFacade]] - Activity assignment checks
- [[UnlockableManager]] - Slot unlock triggers
