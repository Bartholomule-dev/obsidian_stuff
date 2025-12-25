---
type: facade
domain: corruption
file: CorruptionFacade.gd
status: stable
---
# CorruptionFacade

Unified interface for corruption and mission operations.

## Purpose

Manages soul essence economy and the mission lifecycle (launch, track, complete, cancel).

## Dependencies

- [[RealmCoordinator]] - Soul essence, corruption fronts
- [[PlanningPhaseManager]] - Weekly plan
- [[PlanningWorkflowService]] - Mission workflows
- [[CorruptionManager]] - Soul essence operations
- [[RosterManager]] - Demon lookup

## Key Responsibilities

### Soul Essence
- `get_soul_essence()` - Current amount
- `add_soul_essence(amount)` - Add directly
- `spend_soul_essence(amount)` - Spend (returns success)
- `refund_soul_essence(amount)` - Silent refund

### Mission Lifecycle
- `launch_mission(config)` - Launch from opportunity card
- `get_active_missions()` - All active missions
- `get_mission_state(mission_id)` - Get specific mission
- `complete_mission(mission_id, outcome)` - Complete and remove
- `cancel_mission(mission_id)` - Cancel during planning

### Mission Queries
- `get_missions_for_demon(demon_id)` - Demon's missions
- `has_active_mission_for_demon(demon_id)` - Check status
- `cancel_mission_for_demon(demon_id)` - Cancel by demon

### Cost Management
- `apply_mission_costs()` - Apply deferred energy costs at week start

## Mission Config

```gdscript
{
    "demon_id": String,
    "target_id": String,
    "sin_focus": String,
    "opportunity_card_id": String,  # optional
    "active_verbs": Array[String],  # optional
    "pressure_subtlety": float      # optional, default 0.5
}
```

## Related

- [[Corruption System]] - System overview
- [[Mission System]] - Mission mechanics
- [[MissionExecutorService]] - Daily execution
