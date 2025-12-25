---
type: service
domain: divine
file: InterventionService.gd
status: stable
---
# InterventionService

Handles the detection and application of divine interventions, coordinating outcome effects for characters and demons.

## Overview

InterventionService manages divine intervention events - the consequences of accumulated heat/risk from aggressive corruption activities. When triggered, interventions can affect both mortals and demons.

## Key Responsibilities

- Check for daily intervention triggers
- Apply character intervention outcomes
- Apply demon intervention outcomes
- Format intervention messages for display

## Key Methods

| Method | Purpose |
|--------|---------|
| `check_daily_interventions()` | Roll for intervention based on risk |
| `apply_character_outcome()` | Process effects on mortals |
| `apply_demon_outcome()` | Process effects on demons |
| `format_intervention_message()` | Create display text |

## Dependencies

- [[GameState]] - State access
- [[Intervention Risk]] - Risk meter for trigger calculation

## Intervention Outcomes

Interventions can cause:
- **Miracle**: Divine protection for mortals
- **Wrath**: Punishment for demons
- **Cleanse**: Reset corruption progress
- **Expose**: Reveal hidden schemes

## Game Loop Integration

Invoked daily by [[SimulationPhaseCoordinator]] during the "Divine Phase" to check for triggered interventions based on global heat.

## Risk Accumulation

Risk builds from:
- Active mission heat
- Cult Heat (15% rate, max 3/week)
- Aggressive corruption tactics

## Related

- [[Intervention Risk]] - Risk tracking
- [[DivineCleanseService]] - Cleanse execution
- [[Corruption System]] - Heat sources
