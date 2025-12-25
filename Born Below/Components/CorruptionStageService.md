---
type: service
domain: corruption
file: CorruptionStageService.gd
status: stable
---
# CorruptionStageService

Calculates and manages corruption stage progression based on numerical need thresholds.

## Purpose

Maps need values to corruption stages and handles stage transitions.

## Key Responsibilities

- Maps need values to five stages: Innocent, Tempted, Wavering, Falling, Corrupted
- Monitors for stage transitions and emits signals
- Updates character metadata and legacy `is_corrupted` flag
- Provides UI metadata (stage names, colors)

## Key Methods

| Method | Purpose |
|--------|---------|
| `calculate_stage_from_needs(needs)` | Compute stage from need values |
| `update_character_stage(character_id)` | Recalculate and persist |
| `get_stage_name(stage)` | Display string |
| `get_stage_color(stage)` | UI color |

## Stage Calculation

| Stage | Condition |
|-------|-----------|
| 0 - Innocent | All needs > 30 |
| 1 - Tempted | 1 need ≤ 30 |
| 2 - Wavering | 2 needs ≤ 30 |
| 3 - Falling | 1 need ≤ 10 OR 3 needs ≤ 30 |
| 4 - Corrupted | 3+ needs ≤ 10 |

## Stage Colors

| Stage | Color |
|-------|-------|
| Innocent | Green |
| Tempted | Yellow |
| Wavering | Orange |
| Falling | Red |
| Corrupted | Purple |

## Related

- [[Corruption System]] - System overview
- [[MortalCharacterService]] - Triggers stage checks
- [[Corruption Flavors]] - Stage 4 outcomes
