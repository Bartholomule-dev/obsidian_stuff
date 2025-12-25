---
type: system
domain: economy
status: stable
---
# Economy System

Resource management for Hell's operations, primarily centered on Soul Essence.

## Resources

| Resource | Purpose | Manager |
|----------|---------|---------|
| **Soul Essence** | Primary currency | RealmCoordinator |
| **Action Points** | Weekly activity budget | ResourceTransactionManager |

## Soul Essence Sources

| Source | Amount | Condition |
|--------|--------|-----------|
| Corrupted Characters | Variable | Based on character importance |
| Cult Income | `floor(Size * Fervor / 10)` | Weekly from cult |
| Mission Rewards | Variable | Mission completion |
| Tournament Winnings | Per-round rewards | Combat victories |

## Soul Essence Costs

| Cost | Purpose |
|------|---------|
| Demon Recruitment | Unlock new demons |
| Training Activities | Stat improvement |
| Mission Launch | Some missions have costs |
| Morale Restoration | 50 SE to heal trauma |
| Cult Cover Up | Reduce Heat |
| Tournament Entry | Some tournaments have fees |

## Transaction System

`ResourceTransactionManager` provides atomic operations:

```gdscript
# Spend with automatic rollback on failure
if not transaction_manager.spend_soul_essence(amount, validation_callback):
    # Automatically refunded if callback fails
    return false
```

## Upkeep

`HellEconomyService` processes weekly upkeep:
- Demon maintenance costs
- Facility operating costs
- Cult operating costs

## Key Components

- [[RealmFacade]] - Soul essence access
- [[CultFacade]] - Cult income
- `ResourceTransactionManager` - Transactions
- `HellEconomyService` - Economy logic

## Related

- [[Cult System]] - Cult income source
- [[Mission System]] - Mission rewards
- [[Combat System]] - Tournament rewards
