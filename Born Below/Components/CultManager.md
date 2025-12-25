---
type: manager
domain: cult
file: CultManager.gd
status: stable
---
# CultManager

Exclusive owner of the cult's state, managing meters, weekly actions, and the evolving identity of the player's following.

## Purpose

Owns all cult state and derives emergent properties like Identity and Murmurs from meter values.

## Key Responsibilities

- Tracks core cult meters: Size, Fervor, Secrecy, Heat, Dissent
- Manages weekly cult action selection (Recruit, Preach, Fundraise, etc.)
- Derives cult "Identity" (Zealot, Shadow, Merchant) based on action trends
- Coordinates "Murmurs" and situation cooldowns for narrative events

## Key Methods

| Method | Purpose |
|--------|---------|
| `adjust_size()` | Modify cult size |
| `adjust_fervor()` | Modify fervor |
| `adjust_secrecy()` | Modify secrecy |
| `adjust_heat()` | Modify heat |
| `adjust_dissent()` | Modify dissent |
| `select_action()` | Choose weekly action |
| `record_action_taken()` | Track action history |
| `get_identity()` | Get current identity |
| `queue_action_modifier()` | Queue meter modifier |

## Cult Identity

| Identity | Condition | Bonus |
|----------|-----------|-------|
| Zealot | Fervor ≥ 70 | +20% preach/punish |
| Shadow | Secrecy ≥ 70 | +20% recruit/cover_up |
| Merchant | Size ≥ 50 | +20% fundraise |

## Murmurs (Hidden Stability)

Based on Dissent level:
- **Quiet** - Low dissent, stable
- **Restless** - Rising concerns
- **Volatile** - High risk of events
- **Fracturing** - Critical instability

## Related

- [[CultFacade]] - Public API layer
- [[Cult System]] - System overview
- [[CultExecutionService]] - Action execution
