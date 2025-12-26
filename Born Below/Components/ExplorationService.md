---
type: service
domain: exploration
file: ExplorationService.gd
status: stable
---
# ExplorationService

Orchestrates node-based procedural map explorations. Delegates node resolution to specialized services while managing exploration lifecycle.

## Overview

ExplorationService handles the turn-based procedural dungeon-crawling system. When a demon is assigned to exploration, it generates a node map and coordinates encounters as the demon traverses it.

**Post-Refactor (Dec 2025):** Reduced from 1,212 to 520 lines by extracting node resolution and buff handling to dedicated services.

## Architecture

```
ExplorationService (lifecycle orchestration)
    ├── NodeEncounterResolver (node type resolution)
    │   └── BuffEffectProcessor (buff/curse effects)
    ├── DiscoveryManager (discovery generation)
    └── EncounterResolutionService (combat resolution)
```

## Key Responsibilities

- Generate procedural exploration maps
- Coordinate node encounter processing (delegates to NodeEncounterResolver)
- Manage exploration lifecycle (start, progress, complete)
- Handle visual combat integration
- Distribute rewards on completion

## Key Methods

| Method | Purpose |
|--------|---------|
| `assign_demon_to_node_exploration()` | Validates costs and generates procedural map |
| `process_node_encounter()` | Coordinates turn-based traversal |
| `apply_visual_combat_result()` | Syncs manual combat outcome |
| `complete_node_exploration()` | Finalizes rewards |

## Dependencies

- [[NodeEncounterResolver]] - Node type resolution
- [[BuffEffectProcessor]] - Buff and curse effect application
- [[DiscoveryManager]] - Discovery generation
- [[EncounterResolutionService]] - Combat encounter resolution
- [[RosterManager]] - Demon availability
- [[PlanningPhaseManager]] - Weekly plan management

## Data Structures

| Structure | Purpose |
|-----------|---------|
| `ExplorationMap` | Runtime map state |
| `ExplorationMapGenerator` | Procedural generation |
| `NodeDefinition` | Individual node types |
| `DiscoveryData` | Found items/secrets |

## Game Loop Integration

- **Planning Phase**: Demons assigned to exploration
- **Execution Phase**: Node encounters processed via NodeEncounterResolver
- **Results Phase**: Rewards finalized via [[Week Flow|WeekManager]]

## Related

- [[ExplorationCoordinator]] - Public interface layer
- [[NodeEncounterResolver]] - Node resolution logic
- [[BuffEffectProcessor]] - Buff effect handling
- [[Combat System]] - Battle resolution
