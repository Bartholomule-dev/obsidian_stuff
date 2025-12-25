---
type: concept
domain: demon
status: stable
---
# Autonomous Behavior

Demons act independently based on personality and loyalty, requiring player response or notification.

## Overview

**Service:** `AutonomousBehaviorService`
**Actions:** 18 distinct autonomous actions

## Action Categories

### Demand Actions (5) - Require Response

| Action | Description |
|--------|-------------|
| Request Glory | Wants tournament assignment |
| Request Rest | Wants week off |
| Request Crusade | Wants specific scheme type |
| Request Scheme Type | Wants particular category |
| Request Resource | Wants item/equipment |

**Player Choices:**
- **Approve:** Grant request (+loyalty, +mood)
- **Deny:** Refuse request (-loyalty, -mood)
- **Compromise:** Partial fulfillment (neutral)

### Notification Actions (13) - Inform Only

**Helpful:** Training self, mentoring, improving relationships
**Harmful:** Sabotage, theft, bullying, scheme interference
**Neutral:** Socializing, brooding, preparing

## Loyalty Effects

| Loyalty | Effect |
|---------|--------|
| > 70 | +20% helpful actions |
| < 30 | +30% harmful actions |

## Risk Indicators

Shown on demon cards:
- **Red (>30%):** High risk warning
- **Yellow (15-30%):** Medium risk
- **No icon (<15%):** Low risk

## Personality Modifiers

Each archetype has probability modifiers for specific actions:
- Aggressive demons more likely to demand glory
- Cunning demons more likely to steal
- Zealous demons demand religious missions

## Processing

Autonomous behavior is checked during weekly execution. Results appear in demon timeline with:
- Success/failure color coding
- Probability percentages
- Narrative description
- Impact on loyalty/mood/stats

## Signals

```gdscript
demon_demand_issued.emit({demon_id, demand_type, urgency})
demon_autonomous_action.emit({
    demon_id, action_type, action_category, success, effects
})
```

## Related

- [[Demon System]] - Parent system
- [[Memory System]] - Actions create memories
- [[Personality Evolution]] - Personality affects probabilities
