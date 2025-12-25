---
type: concept
domain: mission
status: stable
tags:
  - concept
  - mission
  - narrative
---
# Beats

Narrative decision points during missions. Beats trigger when meters cross thresholds and present meaningful choices.

## What Are Beats?

Beats are mid-mission events that:
- Pause mission execution
- Present player with choices
- Have mechanical and narrative consequences
- Create dramatic tension

## Beat Types

### Opportunity Beats
**Trigger:** Leverage crosses high threshold

*"Your demon has gained significant influence. How do you proceed?"*

| Choice | Effect |
|--------|--------|
| Push Advantage | +Leverage, +Suspicion |
| Consolidate | +Leverage (small), safe |
| Retreat | End mission early, keep gains |

### Complication Beats
**Trigger:** Suspicion crosses threshold

*"The target is growing wary. Your demon must adapt."*

| Choice | Effect |
|--------|--------|
| Cover Tracks | -Suspicion, -Leverage |
| Double Down | +Leverage, +Suspicion |
| Abort | End mission, avoid detection |

### Breakthrough Beats
**Trigger:** Moral Fatigue crosses threshold

*"The target's resolve is crumbling. The moment is now."*

| Choice | Effect |
|--------|--------|
| Exploit Weakness | Major corruption progress |
| Build Trust | Slower but safer progress |
| Patience | Defer decision |

## Beat Resolution

1. Meter crosses threshold
2. Beat queued for display
3. Player presented with choices
4. Effects applied to mission state
5. Mission continues or completes

## Available Beats

Missions can specify which beats are available:
- Some missions have all beats
- Others have limited options
- Activity type affects beat availability

## Key Components

- [[MissionBeatService]] - Detection and queuing
- [[BeatResponseProcessor]] - Choice application
- MissionBeatTemplate - Event template

## Related

- [[Mission System]] - Where beats occur
- [[Week Flow]] - When beats are processed
