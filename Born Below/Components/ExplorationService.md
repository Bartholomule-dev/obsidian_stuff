---
type: service
domain: exploration
file: ExplorationService.gd
status: stable
---
# ExplorationService

Manages the logic and state for node-based procedural map explorations, including encounter resolution, expedition buffs, and discovery generation.

## Overview

ExplorationService handles the turn-based procedural dungeon-crawling system. When a demon is assigned to exploration, it generates a node map and processes encounters as the demon traverses it.

## Key Responsibilities

- Generate procedural exploration maps
- Process node encounters (campfire, battle, mystery, boss)
- Apply expedition buffs during exploration
- Handle combat integration and visual combat results
- Distribute rewards (soul essence, items, XP) on completion

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_node_exploration()` | Validates costs and generates procedural map |
| `process_node_encounter()` | Handles turn-based traversal and node logic |
| `apply_visual_combat_result()` | Syncs manual combat outcome to exploration state |
| `complete_node_exploration()` | Finalizes and distributes accumulated rewards |

## Dependencies

- [[RosterManager]] - Demon availability
- [[PlanningPhaseManager]] - Weekly plan management
- [[EncounterResolutionService]] - Combat encounter resolution
- [[GameState]] - State access

## Data Structures

| Structure | Purpose |
|-----------|---------|
| `ExplorationMap` | Runtime map state |
| `ExplorationMapGenerator` | Procedural generation |
| `NodeDefinition` | Individual node types |
| `DiscoveryData` | Found items/secrets |

## Game Loop Integration

- **Planning Phase**: Demons assigned to exploration
- **Execution Phase**: Node encounters processed
- **Results Phase**: Rewards finalized via [[Week Flow|WeekManager]]

## Related

- [[ExplorationCoordinator]] - Public interface layer
- [[Exploration System]] - System overview
- [[Combat System]] - Battle resolution
