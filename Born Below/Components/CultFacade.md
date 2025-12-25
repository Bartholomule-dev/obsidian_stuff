---
type: facade
domain: cult
file: CultFacade.gd
status: stable
---
# CultFacade

Public API for cult operations. Follows StoryFacade pattern with read-bypass caching.

## Purpose

Manages cult meters (size, fervor, secrecy, heat, dissent), weekly actions, and mission support bonuses.

## Dependencies

- [[CultManager]] - Cult state owner

## Key Responsibilities

### Meter Access (Read-Bypass)
- `get_size()` - Cult membership count
- `get_fervor()` - Religious intensity
- `get_secrecy()` - How hidden the cult is
- `get_heat()` - Suspicion from authorities
- `get_dissent()` - Internal discontent (hidden)
- `get_identity()` - zealot/shadow/merchant/unformed
- `get_all_meters()` - All visible meters

### Meter Modification
- `adjust_size(delta)`
- `adjust_fervor(delta)`
- `adjust_secrecy(delta)`
- `adjust_heat(delta)`
- `adjust_dissent(delta)`

### Action Selection
- `get_action_definitions()` - All available actions
- `select_action(action_id)` - Choose weekly action
- `get_selected_action()` - Current selection
- `clear_action()` - Clear selection

### Income
- `get_weekly_income()` - Soul essence from cult

### Mission Support
- `get_mission_leverage_bonus()` - Bonus if support_mission selected

## Action Definitions

| Action | Effect | Bonus Condition |
|--------|--------|-----------------|
| recruit | +Size, +Heat | Secrecy ≥60 |
| preach | +Fervor, -Secrecy | Size ≥40 |
| fundraise | +SE, +Dissent | Fervor ≥60 |
| cover_up | +Secrecy, -Heat | Heat ≥70 |
| punish | -Dissent, +Heat | Fervor ≥50 |
| support_mission | +Leverage | Shadow identity |

## Related

- [[Cult System]] - System overview
- [[CultManager]] - State owner
- [[CultExecutionService]] - Action execution
