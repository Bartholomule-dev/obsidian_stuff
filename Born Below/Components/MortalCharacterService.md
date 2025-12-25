---
type: service
domain: mortal
file: MortalCharacterService.gd
status: stable
---
# MortalCharacterService

Manages the psychological erosion and corruption of mortal characters through pressure, awareness, and trauma mechanics.

## Purpose

Core logic for corrupting mortals - calculates pressure, triggers desperate behaviors, and manages breaking points.

## Key Responsibilities

- Calculates effective pressure scaling against holiness, vulnerabilities, awareness
- Triggers desperate behaviors and manages permanent vulnerabilities
- Oversees "Breaking Point" system for full corruption transition
- Orchestrates weekly recovery, memory decay, and defensive modifiers

## Key Methods

| Method | Purpose |
|--------|---------|
| `apply_pressure(char_id, need, amount, demon_id)` | Primary corruption entry |
| `calculate_effective_pressure(...)` | Determine final impact |
| `adjust_awareness(char_id, delta)` | Manage alertness tiers |
| `process_weekly_recovery()` | Passive healing |

## Pressure Calculation

```
Effective = Base Pressure
          × Vulnerability Modifier (1.5x if vulnerable)
          × Awareness Modifier (0.5x - 1.0x)
          × Holiness Modifier
```

## Desperate Behavior Flow

```
Need drops below 30
    → Trigger desperate behavior
    → Record in character history
    → Check for breaking point (5+ behaviors)
    → If breaking point: full corruption
```

## Recovery Mechanics

Characters not targeted recover needs:
- Fast needs: +7/week
- Medium needs: +5/week
- Slow needs: +3/week

## Related

- [[MortalCharacterFacade]] - Public API layer
- [[Corruption System]] - System overview
- [[Awareness System]] - Alertness mechanics
- [[Need Recovery]] - Recovery rates
