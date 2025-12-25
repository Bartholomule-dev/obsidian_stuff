---
type: system
domain: demon
status: stable
tags:
  - system
  - demon
  - core
---
# Demon System

The demon raising half of Born Below. Recruit, train, and develop demons with personalities, memories, loyalty, and progression.

## Core Concepts

Demons are your primary agents for corrupting mortals. Each demon has:
- **Stats** - Seven sins (wrath, envy, pride, greed, lust, gluttony, sloth)
- **Personality** - Traits that affect behavior and mood
- **Memory** - Records of experiences that shape relationships
- **Mood & Energy** - Current emotional and physical state
- **Loyalty** - Trust level affecting autonomous behavior

## Demon Lifecycle

```
Recruitment → Training/Quests → Mission Deployment → Rest/Recovery
     ↓              ↓                    ↓                 ↓
  Unlock       Stat Growth          XP Gain          Energy Restore
```

## Weekly Activities (Mutually Exclusive)

A demon can do ONE activity per week:
- **Mission** - Deploy to corrupt a mortal
- **Training** - Improve stats
- **Quest** - Personal quest for rewards
- **Exploration** - Explore procedural maps
- **Tournament** - Compete for glory
- **Rest/Idle** - Recover energy

## Progression System

| Level | XP Required | Unlocks |
|-------|-------------|---------|
| 1 | 0 | Starting |
| 2 | 100 | Stat point |
| 3+ | Scaling | More points |

## Mood & Stress

| Stress Level | Performance | Effect |
|--------------|-------------|--------|
| Peak | 100% | Normal |
| Fatigued | 90% | Minor penalty |
| Exhausted | 75% | Major penalty |
| Burnout | 0% | Cannot work |

## Key Components

- [[DemonManagementFacade]] - Public API
- [[RosterManager]] - Entity storage
- [[DemonManager]] - State owner
- [[DemonMoodService]] - Mood logic
- [[DemonMemoryService]] - Memory system
- [[DemonProgressionService]] - XP/leveling

## Related Systems

- [[Mission System]] - Where demons are deployed
- [[Combat System]] - Battle mechanics
- [[Seven Sins]] - Stat system
