---
type: service
domain: mission
file: BeatResponseProcessor.gd
status: stable
---
# BeatResponseProcessor

Processes player decisions during mission "beats," applying mission state changes and delegating non-mission effects.

## Overview

BeatResponseProcessor handles the player's choices during mission threshold events (beats). It applies the effects of chosen options and updates mission state accordingly.

## Key Responsibilities

- Process player beat responses
- Apply mission state changes
- Delegate non-mission effects to EffectProcessor
- Provide effect previews for UI

## Key Methods

| Method | Purpose |
|--------|---------|
| `process_response()` | Execute chosen beat option |
| `process_delegated_effects()` | Apply non-mission effects |
| `get_effect_preview()` | Generate preview for UI |
| `_apply_heat_vent()` | Handle heat reduction effects |

## Dependencies

- `MissionEffect` - Effect definitions
- `EffectProcessor` - Effect execution
- [[Intervention Risk]] - Heat management

## Beat Response Flow

1. Player sees beat options in BeatDecisionModal
2. Player selects an option
3. BeatResponseProcessor executes choice
4. Mission meters updated
5. Side effects delegated to EffectProcessor
6. Mission continues or concludes

## Effect Types

Beat responses can trigger:
- Meter changes (Leverage, Suspicion, Moral Fatigue)
- Heat venting (risk reduction)
- Character state changes
- Story flag updates

## Game Loop Integration

Executed when player selects a choice in the [[Modals|BeatDecisionModal]] during daily mission execution phase.

## Related

- [[Beats]] - Beat system overview
- [[MissionBeatService]] - Beat triggering
- [[Mission System]] - Mission mechanics
- [[Event System]] - Effect processing
