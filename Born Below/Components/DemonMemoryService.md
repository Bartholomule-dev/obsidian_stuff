---
type: service
domain: demon
file: DemonMemoryService.gd
status: stable
---
# DemonMemoryService

Manages creation, decay, and gameplay impact of demon memories while tracking long-term loyalty and defection risk.

## Purpose

Core service for the memory and loyalty system - memories shape demon behavior and player relationships.

## Key Responsibilities

- Curates up to 20 memories per demon with emotional sentiment and intensity
- Calculates loyalty-based gameplay modifiers (XP, efficiency, costs)
- Monitors defection risk and triggers warnings at critical thresholds
- Handles weekly memory decay and morale restoration

## Key Methods

| Method | Purpose |
|--------|---------|
| `create_memory(demon_id, trigger, context)` | Add new memory |
| `get_loyalty(demon_id)` | Current loyalty value |
| `get_loyalty_modifiers(demon_id)` | Gameplay modifiers |
| `get_memory_bonuses(demon_id)` | Memory-based bonuses |
| `apply_memory_decay(demon_id)` | Weekly decay processing |
| `restore_morale(demon_id, game_state)` | Heal trauma memories |

## Loyalty Modifiers

| Loyalty | XP Modifier | Efficiency | Soul Costs |
|---------|-------------|------------|------------|
| 0 | -15% | -10% | +10% |
| 50 | 0% | 0% | 0% |
| 100 | +15% | +10% | -10% |

## Defection Thresholds

- **< 20:** Defection warning emitted
- **< 10:** High defection risk
- **0:** Demon may leave permanently

## Related

- [[Memory System]] - Concept overview
- [[DemonManager]] - Parent coordinator
- [[Demon System]] - System overview
