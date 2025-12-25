---
type: resource
domain: cult
file: CultState.gd
status: stable
tags:
  - data
  - cult
  - resource
---
# CultState

Resource class tracking the player's surface cult status and growth.

## Overview

CultState tracks all cult meters, the selected weekly action, and derived values like identity and murmurs level.

## Visible Meters

| Meter | Range | Purpose |
|-------|-------|---------|
| `size` | 0-100 | Number of cultists |
| `fervor` | 0-100 | Zealotry and dedication |
| `secrecy` | 0-100 | Hidden from authorities |
| `heat` | 0-100 | Divine attention level |

## Hidden Meters

| Meter | Range | Purpose |
|-------|-------|---------|
| `dissent` | 0-100 | Internal strife (hidden from player) |

## Derived Values

### Identity
Calculated from meter balance:

| Identity | Condition | Bonus |
|----------|-----------|-------|
| **Zealot** | Fervor ≥ 70 | +20% preach/punish |
| **Shadow** | Secrecy ≥ 70 | +20% recruit/cover_up |
| **Merchant** | Size ≥ 50 + balanced | +20% fundraise |
| **None** | Default | No bonus |

### Murmurs
Internal stability from Dissent:

| Level | Dissent Range |
|-------|---------------|
| Quiet | 0-24 |
| Restless | 25-49 |
| Volatile | 50-74 |
| Fracturing | 75-100 |

## Weekly Action

| Property | Description |
|----------|-------------|
| `selected_action` | This week's cult task |
| `action_power` | Effectiveness modifier |

## Income Formula

```
weekly_income = floor(size * fervor / 10)
```

## Used By

- [[CultManager]] - State owner
- [[CultExecutionService]] - Action execution
- [[HellEconomyService]] - Income calculation
- [[InterventionRiskMeter]] - Heat contribution

## Related

- [[Cult System]] - System overview
- [[Cult Situations]] - Narrative events
- [[Economy System]] - Income integration
