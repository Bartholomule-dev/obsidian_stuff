---
type: manager
domain: demon
file: QuestManager.gd
status: stable
---
# QuestManager

Orchestrates demon-specific quests, managing assignments, completion tracking, and failure cooldowns.

## Overview

QuestManager handles the personal quest system where demons pursue individual narrative goals with trials and rewards. Quests are mutually exclusive with other weekly activities.

## Key Responsibilities

- Track available quests per demon
- Manage quest assignments and unassignments
- Handle quest completion and rewards
- Process failure cooldowns

## State

| State | Type | Purpose |
|-------|------|---------|
| `_available_quests` | Quest ID → DemonQuestData | Available quest definitions |
| `_active_quests` | Instance ID → QuestInstanceState | Currently active quests |

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_quest()` | Start demon on personal quest |
| `unassign_quest()` | Remove demon from quest |
| `can_assign_quest()` | Validate quest eligibility |
| `process_cooldowns()` | Update failure cooldowns |
| `mark_quest_completed()` | Finalize quest and distribute rewards |

## Dependencies

- [[UnlockableManager]] - Quest unlock requirements
- [[RosterManager]] - Demon availability
- [[RealmCoordinator]] - Resource rewards
- [[PlanningPhaseManager]] - Weekly plan integration

## Quest Flow

1. Quest becomes available (unlock conditions met)
2. Player assigns demon during Planning Phase
3. Quest progresses through trials during week
4. Completion/failure at week end
5. Cooldown applied on failure

## Related

- [[Demon System]] - Quest-eligible demons
- [[Week Flow]] - Quest execution timing
- [[PlanningFacade]] - Assignment interface
