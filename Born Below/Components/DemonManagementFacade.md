---
type: facade
domain: demon
file: DemonManagementFacade.gd
status: stable
---
# DemonManagementFacade

Unified interface for all demon operations. The largest facade with ~68 methods.

## Purpose

Coordinates demon retrieval, progression, equipment, training, quests, slots, cooldowns, stress, and history.

## Dependencies

- [[RosterManager]] - Demon data, progression
- [[InventoryManager]] - Equipment
- [[QuestManager]] - Quest assignment
- [[UnlockableManager]] - Unlock checks
- [[PlanningWorkflowService]] - Training workflows
- [[PlanningPhaseManager]] - Training activities

## Key Responsibilities

### Demon Retrieval
- `get_demon(demon_id)` - Get demon by ID
- `get_unlocked_demons()` - All unlocked demons (for UI)
- `get_available_demons()` - Unlocked AND not busy (for assignments)
- `get_roster_demons()` - Demons in active slots

### Progression
- `award_xp(demon_id, amount, source)` - Award XP
- `get_level(demon_id)` - Current level
- `get_progression_view(demon_id)` - Lightweight read-only view

### Equipment
- `equip_item(demon_id, item_id)` - Equip item
- `unequip_item(demon_id, slot)` - Unequip from slot
- `get_equipment(demon_id)` - Get equipped items
- `calculate_equipment_bonuses(demon_id)` - Total stat bonuses

### Training
- `can_assign_training(demon_id, activity_id)` - Validation
- `assign_training(demon_id, activity_id)` - Assign to training
- `is_in_training(demon_id)` - Check status
- `process_training_week()` - End-of-week processing

### Quests
- `assign_quest(demon_id, quest_id)` - Assign quest
- `get_active_quest(demon_id)` - Current quest
- `has_active_quest(demon_id)` - Check status

### Slots
- `get_slot(slot_index)` - Get demon in slot
- `assign_to_slot(slot_index, demon_id)` - Assign
- `is_slot_unlocked(slot_index)` - Check unlock

### Stress & Energy
- `get_stress_level(demon_id)` - Stress tier name
- `can_perform_schemes(demon_id)` - Burnout check
- `add_energy(demon_id, amount)` - Modify energy

## Related

- [[Demon System]] - System overview
- [[DemonManager]] - State owner
- [[RosterManager]] - Entity storage
