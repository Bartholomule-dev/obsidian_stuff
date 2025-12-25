---
type: service
domain: mission
file: OpportunityCooldownService.gd
status: stable
---
# OpportunityCooldownService

Manages rest periods for mission opportunities to ensure rotating variety of gameplay choices.

## Purpose

Prevents the same missions from appearing too frequently by tracking cooldowns.

## Key Responsibilities

- Tracks remaining weeks for opportunity keys
- Ticks down cooldowns during weekly reset
- Allows cooldown removal when missions are cancelled

## Key Methods

| Method | Purpose |
|--------|---------|
| `add_cooldown(key, weeks)` | Start cooldown timer |
| `tick_cooldowns()` | Decrement all timers |
| `is_on_cooldown(key)` | Check if blocked |
| `get_all_cooldowns()` | Debug/UI access |
| `remove_cooldown(key)` | Cancel cooldown |

## Cooldown Flow

```
Mission Completed
    → add_cooldown(opportunity_key, 2)
    
Weekly Reset
    → tick_cooldowns() // All timers -1
    
Mission Cancelled (before execution)
    → remove_cooldown(opportunity_key)
```

## Default Cooldowns

| Event | Cooldown |
|-------|----------|
| Mission completed | 2 weeks |
| Mission failed | 1 week |
| World event used | 3 weeks |

## Related

- [[Mission System]] - System overview
- [[OpportunityGenerationService]] - Uses cooldowns to filter
- [[PlanningFacade]] - Cooldown API access
