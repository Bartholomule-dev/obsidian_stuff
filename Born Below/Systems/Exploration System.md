---
type: system
domain: exploration
status: stable
---
# Exploration System

Procedural turn-based exploration maps where demons discover resources, fight enemies, and find treasures.

## Core Concepts

Explorations are roguelike-style maps with:
- **Nodes** - Locations to visit
- **Encounters** - Events at nodes
- **Paths** - Connections between nodes

## Exploration Flow

```
Select Exploration → Generate Map → Navigate Nodes → Resolve Encounters → Complete
        ↓                ↓               ↓                  ↓              ↓
    Choose demon      Procedural     Player choice      Combat/loot     Rewards
```

## Node Types

| Type | Content | Risk |
|------|---------|------|
| Combat | Enemy encounter | High |
| Treasure | Item reward | Low |
| Rest | Energy recovery | None |
| Mystery | Random event | Variable |
| Boss | Difficult enemy | Very High |

## Map Generation

Maps are procedurally generated with:
- Starting node
- Branching paths
- Difficulty scaling
- Boss at end

## Encounter Resolution

At each node:
1. Reveal encounter type
2. Player chooses to engage or retreat
3. Resolve (combat, loot, etc.)
4. Advance or return

## Discoveries

Special finds during exploration:
- Rare items
- Demon upgrades
- Story unlocks
- Soul essence caches

## Key Components

- [[ExplorationService]] - Map generation, state
- [[ExplorationCoordinator]] - Flow orchestration
- [[EncounterResolutionService]] - Node resolution
- [[DiscoveryManager]] - Discovery tracking

## Related Systems

- [[Combat System]] - Combat encounters
- [[Demon System]] - Exploration participants
