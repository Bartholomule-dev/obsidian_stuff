---
type: concept
domain: demon
status: stable
tags:
  - concept
  - demon
  - loyalty
---
# Memory System

Demons maintain curated emotional highlights from significant events, affecting loyalty and behavior over time.

## Overview

**Service:** `DemonMemoryService`
**Storage:** Max 20 memories per demon (oldest pruned when limit reached)

## Memory Structure

Each memory contains:
- `type` - Memory category
- `intensity` - Emotional weight (0-100)
- `description` - Narrative text
- `week` - When it occurred
- `decay_rate` - How fast it fades

## Memory Types

| Type | Trigger | Loyalty Effect |
|------|---------|----------------|
| `praised` | Player praises demon | +5 |
| `scolded` | Player scolds demon | -5 |
| `level_up` | Demon gains level | +3 |
| `scheme_success` | Scheme succeeds | +2 |
| `scheme_fail` | Scheme fails | -2 |
| `combat_victory` | Wins tournament/combat | +3 |
| `combat_defeat` | Loses combat | -3 |
| `trauma` | Traumatic event | -10 (special decay) |
| `personality_mutation` | Personality evolves | Narrative record |

## Memory Decay

**Normal Memories:** 5% intensity reduction per week
**Trauma Memories:** 2% decay per week (persist longer)

When intensity drops below 10, memory is automatically pruned.

## Loyalty System

**Scale:** 0-100

### Loyalty Effects

| Mechanic | Impact |
|----------|--------|
| XP Gain | ±15% at extremes |
| Efficiency | ±10% at extremes |
| Soul Costs | ±10% at extremes |
| Defection Risk | Triggered at loyalty < 20 |

### Loyalty Thresholds

- **< 20:** Defection warning, may leave permanently
- **< 30:** +30% chance of harmful autonomous actions
- **> 70:** +20% chance of helpful autonomous actions

## Morale Restoration

**Cost:** 50 soul essence
**Effects:**
- Reduces trauma intensity by 60%
- Grants +25 loyalty
- Creates positive memory

## Signals

```gdscript
demon_memory_created.emit({demon_id, memory})
demon_loyalty_changed.emit({demon_id, old_loyalty, new_loyalty})
demon_defection_risk.emit({demon_id, loyalty})
```

## Related

- [[Demon System]] - Parent system
- [[Autonomous Behavior]] - Loyalty affects actions
- [[Personality Evolution]] - Mutations create memories
