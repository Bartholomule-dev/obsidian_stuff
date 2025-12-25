---
type: system
domain: combat
status: stable
---
# Combat System

Turn-based battles between demons and enemies. Used in explorations, tournaments, and random encounters.

## Combat Modes

| Mode | Use Case | Visual |
|------|----------|--------|
| **Instant** | Quick encounters | No |
| **Visual** | Important battles | Yes |

## Combat Stats

Demons use their seven sin stats in combat:
- **Wrath** - Primary damage stat
- **Pride** - Defense/HP contribution
- **Sloth** - Speed/initiative
- Others provide secondary bonuses

## Visual Combat Flow

```
Setup → Turn Loop → Resolution
  ↓         ↓           ↓
Load     Attack/     Victory/
sprites  Defend      Defeat
```

### Turn Structure
1. Determine initiative (speed check)
2. Attacker deals damage (stat + roll)
3. Defender takes damage (reduced by defense)
4. Check for defeat (HP ≤ 0)
5. Swap attacker/defender
6. Repeat until victor

## HP Calculation

```
Demon Max HP = 60 + (Pride * 3) + (Level * 5)
Enemy Max HP = Defined in EnemyData
```

## Damage Calculation

```
Base Damage = Wrath + (Level * 2)
Variance = ±20%
Final = Base * Variance - Defense
```

## Combat Outcomes

Victory rewards:
- XP for demon
- Possible item drops
- Tournament advancement

Defeat penalties:
- Stress increase
- Energy drain
- Tournament elimination

## Key Components

- [[CombatFacade]] - Public API
- [[CombatResolutionService]] - Turn simulation
- [[CombatSessionService]] - Visual management
- [[EncounterResolutionService]] - Instant battles
- [[RewardDistributionService]] - Outcome application

## Related Systems

- [[Exploration System]] - Combat encounters
- [[Demon System]] - Combatant stats
