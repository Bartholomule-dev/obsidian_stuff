---
type: manager
domain: demon
file: DemonManager.gd
status: stable
---
# DemonManager

Central orchestration hub for all demon mechanics, delegating specific logic to 8+ specialized services and 4 sub-managers.

## Purpose

Coordinates the complex web of demon systems, providing unified API while delegating to specialized services.

## Key Responsibilities

- Manages active roster including slot assignments and unlocking
- Coordinates demon progression (XP/Leveling) and training assignments
- Handles player interactions (Praise/Scold) with cooldowns
- Provides unified API for history, memories, and personality evolution

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_slot()` | Slot assignment |
| `award_demon_xp()` | Grant experience |
| `praise_demon()` | Player praise action |
| `scold_demon()` | Player scold action |
| `assign_demon_to_training()` | Start training |
| `record_demon_event()` | Log to history |

## Service Delegation

```
DemonManager (hub)
    ├── DemonProgressionService (XP, levels)
    ├── DemonMoodService (stress, energy)
    ├── DemonMemoryService (memories, loyalty)
    ├── DemonTrainingService (training execution)
    ├── DemonDialogueService (personality dialogue)
    ├── DemonHistoryService (timeline)
    ├── DemonQuestService (personal quests)
    └── PersonalityEvolutionService (drift, mutation)
```

## Sub-Managers

- `DemonProgressionManager` - XP/Level state
- `DemonTrainingManager` - Training state
- `DemonSlotManager` - Slot assignments
- `DemonCooldownManager` - Interaction cooldowns

## Related

- [[RosterManager]] - Parent coordinator
- [[DemonManagementFacade]] - Public API layer
- [[Demon System]] - System overview
