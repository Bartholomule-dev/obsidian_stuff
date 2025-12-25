---
type: concept
domain: core
status: stable
---
# Intervention Risk

Divine opposition to your corruption activities. Aggressive play raises the risk of heavenly intervention.

## The Meter

Intervention Risk is tracked as a global meter (0-100):
- 0 = No divine attention
- 50 = Moderate scrutiny
- 100 = Guaranteed intervention

## What Raises Risk

| Action | Risk Increase |
|--------|---------------|
| Corruption stage advancement | +5-10 |
| Aggressive mission tactics | +3-5 |
| High cult Heat | +2/week |
| Exposed corruption | +10 |

## What Lowers Risk

| Action | Risk Decrease |
|--------|---------------|
| Subtle mission tactics | -2 |
| Cover Up cult action | -5 |
| Time (natural decay) | -3/week |
| Low profile weeks | -5 |

## Intervention Events

When risk is high, divine intervention may occur:
- **Cleansing** - Target's corruption progress reset
- **Protection** - Target becomes resistant
- **Exposure** - Cult Heat increases dramatically
- **Smiting** - Demon temporarily disabled

## Threshold Checks

At the end of each week:
1. Roll against intervention risk
2. If triggered, select intervention type
3. Apply consequences
4. Risk resets partially

## Strategy

Balance aggression with caution:
- Push hard on one target = high risk
- Spread pressure = lower risk but slower
- Use Cover Up to manage Heat

## Key Components

- InterventionRiskMeter (autoload) - Risk tracking
- [[InterventionService]] - Intervention logic
- [[DivineCleanseService]] - Cleansing effects

## Related

- [[Corruption System]] - What triggers risk
- [[Cult System]] - Cover Up action
