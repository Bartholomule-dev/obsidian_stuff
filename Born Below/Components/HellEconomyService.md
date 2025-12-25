---
type: service
domain: economy
file: HellEconomyService.gd
status: stable
---
# HellEconomyService

Handles soul generation and currency income derived from the corruption stages of mortal characters.

## Overview

HellEconomyService calculates weekly soul essence income based on how corrupted the mortal characters are. More corruption = more souls flowing to Hell.

## Key Responsibilities

- Calculate weekly income from corruption
- Integrate corruption stages with economy
- Feed income data to realm coordinator

## Key Methods

| Method | Purpose |
|--------|---------|
| `calculate_weekly_corruption_income()` | Compute income from all corrupted mortals |
| `_init()` | Initialize with dependencies |

## Dependencies

- [[MortalCharacterFacade]] - Character corruption states
- [[CorruptionManager]] - Corruption data
- [[GameState]] - State access

## Income Calculation

Income scales with corruption stage:

| Stage | Income Multiplier |
|-------|-------------------|
| Innocent | 0 |
| Tempted | Low |
| Falling | Medium |
| Breaking | High |
| Corrupted | Maximum |

## Income Sources

Total weekly income combines:
- Corruption income (this service)
- Cult income: `floor(Size × Fervor / 10)`
- Mission rewards

## Related

- [[Economy System]] - Parent system
- [[Corruption System]] - Income source
- [[Cult System]] - Additional income
- [[RealmCoordinator]] - Resource management
