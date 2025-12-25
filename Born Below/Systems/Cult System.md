---
type: system
domain: cult
status: stable
tags:
  - system
  - cult
  - core
---
# Cult System

Manage a mortal cult that supports your infernal operations. The cult provides income, mission bonuses, and strategic options.

## Cult Meters

| Meter | Description | Visible |
|-------|-------------|---------|
| **Size** | Number of followers | Yes |
| **Fervor** | Religious intensity | Yes |
| **Secrecy** | How hidden the cult is | Yes |
| **Heat** | Suspicion from authorities | Yes |
| **Dissent** | Internal discontent | No (hidden) |

## Cult Identity

Based on dominant meters, cult develops an identity:

| Identity | Condition | Bonus |
|----------|-----------|-------|
| Zealot | Fervor highest | +Fervor effects |
| Shadow | Secrecy highest | +Secrecy effects, +Leverage |
| Merchant | Size highest | +Size effects |
| Unformed | No clear leader | No bonus |

## Weekly Actions

Each week, choose ONE cult action:

| Action | Primary Effect | Trade-off |
|--------|----------------|-----------|
| Recruit | +Size | +Heat |
| Preach | +Fervor | -Secrecy |
| Fundraise | +Soul Essence | +Dissent |
| Cover Up | +Secrecy, -Heat | -Size, costs SE |
| Punish | -Dissent | +Heat |
| Support Mission | +Leverage bonus | +Heat, -Fervor |

## Conditional Bonuses

Actions have bonus/penalty conditions:

```
Recruit: +4 Size if Secrecy ≥60
         -3 Size if Heat ≥50
```

## Weekly Income

Cult generates soul essence based on:
- Base income from Size
- Fervor multiplier
- Secrecy protection

## Key Components

- [[CultFacade]] - Public API
- [[CultManager]] - State owner
- [[CultExecutionService]] - Action execution

## Related Systems

- [[Mission System]] - Support Mission bonus
- [[Week Flow]] - When actions execute
