---
type: resource
domain: demon
file: DemonData.gd
status: stable
tags:
  - data
  - demon
  - resource
---
# DemonData

Resource class defining a demon's identity, stats, and progression state.

## Overview

DemonData is the core data structure for demons in the game. It contains static identity information, dynamic stats, and runtime state like mood and energy.

## Key Properties

### Identity
| Property | Type | Description |
|----------|------|-------------|
| `id` | String | Unique identifier |
| `display_name` | String | Demon's name |
| `demon_rank` | Enum | Lesser, Greater, Archdemon |
| `personality_archetype` | String | Behavioral pattern |

### Stats ([[Seven Sins]])
| Stat | Range | Purpose |
|------|-------|---------|
| `wrath` | 0-100 | Combat, intimidation |
| `envy` | 0-100 | Manipulation, whispers |
| `pride` | 0-100 | Intel, read soul |
| `greed` | 0-100 | Bargains, gifts |
| `lust` | 0-100 | Charm, seduction |
| `gluttony` | 0-100 | Excess, gorging |
| `sloth` | 0-100 | Dreams, patience |

### Runtime State
| Property | Range | Description |
|----------|-------|-------------|
| `happiness` | 0-100 | Mood level |
| `energy` | 0-100 | Work capacity |
| `stress` | 0-100 | Burnout risk |
| `loyalty` | -100 to 100 | Defection risk |
| `level` | 1+ | Progression level |
| `xp` | 0+ | Experience points |

### History
| Property | Description |
|----------|-------------|
| `memories` | List of significant events |
| `age` | Weeks of service |

## Used By

- [[RosterManager]] - Entity storage
- [[DemonManager]] - State management
- [[MissionExecutorService]] - Mission assignment
- [[DemonProgressionService]] - XP and leveling

## Data Location

`data/demons/*.tres`

## Related

- [[Demon System]] - System overview
- [[Memory System]] - Memory mechanics
- [[Personality Evolution]] - Archetype changes
- [[Seven Sins]] - Stat system
