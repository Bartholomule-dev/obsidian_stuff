---
type: concept
domain: core
status: stable
---
# Week Flow

The core game loop operates on a weekly cycle with distinct phases.

## Phase Sequence

```
PLANNING → EXECUTING → RESULTS → END_WEEK
    ↓          ↓          ↓          ↓
 Assign     Simulate    Review     Reset
 demons     7 days      events     state
```

## Planning Phase

**What happens:**
- View opportunity cards
- Assign demons to activities (mission/training/quest/etc.)
- Select cult action
- Review intel on targets

**Player actions:**
- Choose targets and approaches
- Manage demon roster
- Spend soul essence

**Exit condition:** Player clicks "Execute Week"

## Executing Phase

**What happens (per day, 7 times):**
1. Process active missions (meter updates)
2. Check for beat triggers
3. Process training progress
4. Process quest progress
5. Check for random events
6. Process autonomous demon behaviors

**Player actions:**
- Respond to beat decisions
- Handle demon demands

## Results Phase

**What happens:**
- Collect end-of-week events
- Display weekly summary
- Show corruption progress
- Present "whispers" (court gossip)

**Player actions:**
- Review outcomes
- Acknowledge events

## End Week Phase

**What happens:**
- Reset weekly flags
- Tick cooldowns
- Process recovery for unpressured characters
- Award weekly income
- Clear temporary state

**Transition:** Automatically returns to PLANNING

## Key Components

- GameFlow (autoload) - Phase state machine
- [[SimulationPhaseCoordinator]] - Day execution
- WeekManager - Weekly lifecycle

## Related

- [[Mission System]] - Executes during week
- [[Cult System]] - Actions execute during week
