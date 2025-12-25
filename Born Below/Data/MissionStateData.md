---
type: resource
domain: mission
file: MissionStateData.gd
status: stable
tags:
  - data
  - mission
  - resource
---
# MissionStateData

Resource class tracking the runtime state of an active corruption mission.

## Overview

MissionStateData is created when a demon is assigned to a corruption scheme. It tracks all dynamic state during mission execution including meters, beats triggered, and active verbs.

## Key Properties

### Mission Meters
| Meter | Range | Purpose |
|-------|-------|---------|
| `leverage` | 0-100 | Progress toward corruption |
| `suspicion` | 0-100 | Detection risk |
| `moral_fatigue` | 0-100 | Target's willpower erosion |

### Configuration
| Property | Description |
|----------|-------------|
| `pressure_subtlety` | Balance: speed vs stealth (0.0-1.0) |
| `active_verbs` | Currently equipped [[Verbs]] |
| `target_id` | [[Mortal Character Data|MortalCharacterData]] reference |
| `demon_id` | [[DemonData]] reference |

### History
| Property | Description |
|----------|-------------|
| `beats_triggered` | List of [[Mission Beats]] fired |
| `day_started` | When mission began |
| `days_active` | Duration so far |

## Meter Thresholds

Meters trigger [[Mission Beats]] at thresholds:

| Level | Threshold | Beat Type |
|-------|-----------|-----------|
| Low | 20 | Setup |
| Medium | 40 | Milestone |
| High | 60 | Advantage |
| Critical | 80 | Finisher |

## Used By

- [[MissionExecutorService]] - Daily updates
- [[MissionMeterService]] - Meter calculations
- [[MissionBeatService]] - Beat detection
- [[PlanningFacade]] - Mission assignment

## Related

- [[Mission System]] - System overview
- [[Corruption Schemes]] - Mission definitions
- [[Mission Beats]] - Decision points
- [[Verbs]] - Mission abilities
