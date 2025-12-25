---
type: service
domain: mission
file: MissionRewardService.gd
status: stable
---
# MissionRewardService

Translates mission performance into progression rewards for demons and corruption pressure on targets.

## Purpose

Converts mission outcomes into tangible gameplay effects - XP for demons, pressure for targets.

## Key Responsibilities

- Calculates demon XP based on duration and Leverage, penalized by Suspicion
- Converts final Leverage and Fatigue into corruption pressure burst
- Maps Sin categories to Character Needs for pressure application
- Generates reward breakdowns for UI display

## Key Methods

| Method | Purpose |
|--------|---------|
| `calculate_xp_reward()` | Compute demon XP |
| `calculate_final_pressure()` | Compute target pressure |
| `apply_mission_rewards()` | Execute all rewards |
| `get_reward_breakdown()` | UI-friendly summary |

## XP Calculation

```
Base XP = Duration × 10
Leverage Bonus = Leverage / 10
Suspicion Penalty = Suspicion / 20
Final XP = (Base + Leverage Bonus) - Suspicion Penalty
```

## Pressure Application

Final mission pressure = Leverage + (Moral Fatigue / 2)

Applies to the sin/need targeted by the mission.

## Sin → Need Mapping

| Sin | Need |
|-----|------|
| Wrath | Security |
| Pride | Esteem |
| Greed | Wealth |
| Lust | Desire |
| etc. | etc. |

## Related

- [[Mission System]] - System overview
- [[Corruption System]] - Pressure effects
- [[RewardDistributionService]] - XP distribution
