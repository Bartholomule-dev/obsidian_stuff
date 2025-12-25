---
type: service
domain: cult
file: CultExecutionService.gd
status: stable
---
# CultExecutionService

Handles the execution of weekly cult actions, calculating meter changes, resource costs, and heat-driven intervention risks.

## Purpose

Executes cult actions with complex outcome calculation including identity bonuses and conditional modifiers.

## Key Responsibilities

- Calculates action outcomes by merging base effects with identity bonuses and modifiers
- Manages Soul Essence transactions (costs paid before effects)
- Converts cult heat into intervention risk with weekly caps
- Determines event trigger probabilities based on heat thresholds

## Key Methods

| Method | Purpose |
|--------|---------|
| `calculate_action_outcome(action_id, modifiers)` | Compute final deltas |
| `execute_weekly_action()` | Full execution flow |
| `calculate_and_apply_weekly_income()` | Passive SE generation |
| `apply_heat_to_intervention_risk()` | Feed heat to divine system |

## Action Outcome Calculation

```
Final Delta = Base Effect
            + Identity Bonus (if matching)
            + Conditional Modifier (if threshold met)
            - Penalties (if threshold triggered)
```

## Weekly Income Formula

```
Income = floor(Size * Fervor / 10)
```

## Heat to Intervention

- 15% of Heat feeds into Intervention Risk
- Maximum 3 risk points per week
- Applied during weekly processing

## Related

- [[CultFacade]] - Public API layer
- [[Cult System]] - System overview
- [[CultManager]] - Cult state
- [[Intervention Risk]] - Heat effects
