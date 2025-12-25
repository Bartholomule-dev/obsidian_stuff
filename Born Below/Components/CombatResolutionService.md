---
type: service
domain: combat
file: CombatResolutionService.gd
status: stable
---
# CombatResolutionService

Orchestrates multi-turn visual combat simulation between demons and enemies.

## Purpose

Simulates complete multi-turn combat with HP pools, attack rounds, and damage calculations.

## Key Responsibilities

- Simulates multi-turn combat loops with HP pools and damage calculations
- Manages combat state (health tracking, turn counts, combat log)
- Determines victory conditions and populates reward/penalty data
- Integrates with memory system for lasting records of victories/defeats

## Key Methods

| Method | Purpose |
|--------|---------|
| `resolve_combat(demon_id, enemy_data)` | Execute full simulation, return CombatOutcomeEvent |
| `_execute_turn(...)` | Process single round of mutual attacks |
| `_calculate_demon_damage(...)` | Calculate damage from offensive stats |
| `_create_combat_memories(...)` | Record narrative memories |

## Combat Flow

```
resolve_combat()
    ├── Initialize HP pools
    ├── Loop: _execute_turn()
    │   ├── Demon attacks
    │   ├── Enemy attacks (if alive)
    │   └── Check victory conditions
    ├── Determine winner
    ├── Create memories
    └── Return CombatOutcomeEvent
```

## Damage Calculation

Uses composite of offensive stats:
- **Wrath** - Primary damage
- **Envy** - Bonus damage
- **Pride** - Defense/mitigation

## Related

- [[CombatFacade]] - Public API layer
- [[Combat System]] - System overview
- [[CombatSessionService]] - Visual presentation
- [[Memory System]] - Combat memories
