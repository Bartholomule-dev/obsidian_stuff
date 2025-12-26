---
type: service
domain: exploration
file: exploration/NodeEncounterResolver.gd
status: stable
---
# NodeEncounterResolver

Resolves node encounters during exploration by dispatching to type-specific handlers.

## Overview

Extracted from ExplorationService to handle the resolution logic for all 11 node types. Each node type (campfire, cave, battle, etc.) has dedicated resolution logic that returns a standardized result dictionary.

## Node Types Handled

| Node Type | Resolution Logic |
|-----------|-----------------|
| `campfire` | Energy restoration based on roll |
| `cave` | Risk/reward with discovery chance |
| `battle` | Combat with visual combat detection |
| `boss` | High-stakes combat encounter |
| `mystery` | Random encounter selection |
| `treasure` | Guaranteed rewards |
| `trap` | Damage with evasion chance |
| `shrine` | Buff application |
| `merchant` | Item transactions |
| `portal` | Map transitions |
| `exit` | Exploration completion |

## Visual Combat Detection

For battle and boss nodes, checks exploration template settings:
- `enable_visual_battles` - Whether visual combat is available
- `default_battle_mode` - "visual", "auto", or threshold-based
- `battle_enemy_pool` - Available enemies for visual combat

Returns `requires_visual_combat: true` when visual combat should trigger.

## Key Methods

| Method | Purpose |
|--------|---------|
| `resolve()` | Main entry point, dispatches by node type |
| `_resolve_battle()` | Battle resolution with visual combat detection |
| `_resolve_campfire()` | Rest and energy restoration |
| `_calculate_buff_multiplier()` | Stacks applicable buff modifiers |

## Dependencies

- [[BuffEffectProcessor]] - Buff and curse effect application
- [[EncounterResolutionService]] - Combat outcome calculation
- [[DemonManagementFacade]] - Demon stat access
- [[InterventionRiskMeter]] - Divine intervention tracking

## Result Dictionary

All resolvers return a standardized dictionary:

```gdscript
{
    "success": bool,
    "message": String,
    "rewards": Dictionary,  # Optional
    "discovery": DiscoveryData,  # Optional
    "requires_visual_combat": bool,  # For battles
    "visual_combat_config": Dictionary  # Enemy, difficulty
}
```

## Related

- [[ExplorationService]] - Parent orchestrator
- [[BuffEffectProcessor]] - Effect application
- [[Combat System]] - Battle resolution
