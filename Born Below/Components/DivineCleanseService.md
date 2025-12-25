---
type: service
domain: divine
file: DivineCleanseService.gd
status: stable
---
# DivineCleanseService

Executes the "Divine Cleanse" consequence by identifying highly corrupted mortals and resetting their needs to a pure state.

## Overview

DivineCleanseService implements the most severe divine intervention outcome. It finds the most corrupted mortal and resets their corruption progress, potentially undoing weeks of player effort.

## Key Responsibilities

- Find the most corrupted target
- Execute cleanse by resetting needs
- Coordinate with mortal character system

## Key Methods

| Method | Purpose |
|--------|---------|
| `execute_divine_cleanse()` | Trigger full cleanse process |
| `find_most_corrupted_target()` | Identify cleanse victim |
| `cleanse_target()` | Reset target's corruption state |

## Dependencies

- [[MortalCharacterManager]] - Character state access

## Cleanse Effects

When a character is cleansed:
- All needs reset to healthy values
- Corruption stage resets
- Awareness may also reset
- Player loses progress on that target

## Game Loop Integration

Triggered as a high-impact outcome of divine intervention or specific narrative events. Can occur during:
- Daily intervention checks
- Special story events
- High-risk mission failures

## Strategic Impact

Cleanse represents a major setback, encouraging players to:
- Balance aggression with caution
- Manage heat/risk carefully
- Spread corruption across multiple targets

## Related

- [[InterventionService]] - Intervention triggering
- [[Intervention Risk]] - Risk management
- [[Corruption System]] - Corruption state
- [[CorruptionStageService]] - Stage mechanics
