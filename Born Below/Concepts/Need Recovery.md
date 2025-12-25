---
type: concept
domain: mortal
status: stable
---
# Need Recovery

Mortal needs recover at different rates when not under pressure. Recovery is the primary counter to corruption.

## Recovery Rates

| Category | Needs | Recovery/Week | Rationale |
|----------|-------|---------------|-----------|
| **Fast** | Security, Purpose | +7 | Core human drives restore quickly |
| **Medium** | Standing, Esteem, Comfort | +5 | Social needs recover moderately |
| **Slow** | Wealth, Desire | +3 | Material/physical needs linger |

## Recovery Conditions

Recovery only applies when:
1. Character is **not corrupted**
2. Character received **no scheme pressure** that week

## Weekly Pressure Tracking

`MortalCharacterData.received_pressure_this_week`:
- Set to `true` when `apply_pressure()` called
- Reset to `false` at week start

## Strategy Implications

- **Sustained pressure matters:** Single-week attacks get undone
- **Fast needs are harder:** Security/Purpose bounce back quickly
- **Slow needs stick:** Wealth/Desire pressure accumulates
- **Multi-target spreading:** Gives victims time to recover
- **Focused assault:** Prevents any recovery

## Related

- [[Corruption System]] - Parent system
- [[Seven Sins]] - Need definitions
- [[Character Defenses]] - Fortify Weakness boosts recovery
