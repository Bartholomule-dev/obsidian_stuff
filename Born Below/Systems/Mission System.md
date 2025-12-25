---
type: system
domain: mission
status: stable
---
# Mission System

The tactical layer connecting demons to corruption targets. Missions run over multiple days with meter-based progression.

## Mission Flow

```
Opportunity Card → Launch Mission → Daily Execution → Beat Decisions → Completion
       ↓                ↓                 ↓                ↓              ↓
   Select target    Assign demon    Update meters    Player choices   Rewards
```

## Mission Meters

Three meters track mission state:

| Meter | Purpose | Good/Bad |
|-------|---------|----------|
| **Leverage** | Progress toward corruption | Higher = better |
| **Suspicion** | Target awareness | Lower = better |
| **Moral Fatigue** | Target's resistance | Higher = better |

## Daily Execution

Each day of the week:
1. Calculate demon effectiveness
2. Apply pressure to target
3. Update mission meters
4. Check for beat thresholds
5. Check for mission completion

## Beats

Beats are narrative decision points triggered when meters hit thresholds:

| Beat Type | Trigger | Player Choice |
|-----------|---------|---------------|
| Opportunity | High leverage | Push advantage or play safe |
| Complication | High suspicion | Cover tracks or press on |
| Breakthrough | High fatigue | Exploit weakness or build trust |

## Mission State

```gdscript
MissionStateData:
  - mission_id: String
  - target_id: String
  - demon_id: String
  - sin_focus: String
  - meters: {leverage, suspicion, moral_fatigue}
  - available_beats: Array
```

## Key Components

- [[CorruptionFacade]] - Mission lifecycle
- [[MissionExecutorService]] - Daily updates
- [[MissionMeterService]] - Meter calculations
- [[MissionBeatService]] - Beat detection
- [[MissionRewardService]] - Completion rewards

## Related Systems

- [[Corruption System]] - What missions affect
- [[Demon System]] - Who runs missions
- [[Beats]] - Decision points
