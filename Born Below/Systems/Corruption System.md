---
type: system
domain: corruption
status: stable
tags:
  - system
  - corruption
  - core
---
# Corruption System

The corruption half of Born Below. Target mortal characters and exploit their needs until they break.

## Core Concepts

Mortal characters have seven **needs** mapped to the seven sins. When needs drop low, characters become desperate and eventually corrupt.

## Need → Sin Mapping

| Need | Sin | When Low... |
|------|-----|-------------|
| Security | Wrath | Feels threatened, lashes out |
| Standing | Envy | Covets others' status |
| Esteem | Pride | Craves validation |
| Wealth | Greed | Desperate for money |
| Desire | Lust | Seeks forbidden pleasure |
| Comfort | Gluttony | Overindulges to cope |
| Purpose | Sloth | Loses motivation |

## Corruption Stages

| Stage | Name | Description |
|-------|------|-------------|
| 0 | Innocent | Untouched by corruption |
| 1 | Tempted | Beginning to waver |
| 2 | Wavering | Seriously tempted |
| 3 | Falling | Near the edge |
| 4 | Corrupted | Fully fallen |

## Pressure System

Demons apply **pressure** to needs:
1. Demon targets a sin/need
2. Pressure reduces the need value
3. Low needs trigger desperate behaviors
4. Enough desperate behaviors → stage advancement
5. Stage 4 = victory for that target

## Recovery

If a character receives NO pressure in a week:
- Needs slowly recover toward baseline
- Recovery rate varies by need type
- Corrupted characters don't recover

## Awareness System

Characters can become aware of manipulation:

| Level | Range | Effect |
|-------|-------|--------|
| Unaware | 0-25 | Normal vulnerability |
| Suspicious | 26-50 | Minor resistance |
| Alert | 51-75 | Moderate resistance |
| Vigilant | 76-100 | Major resistance |

## Key Components

- [[MortalCharacterFacade]] - Public API
- [[CorruptionFacade]] - Soul essence, missions
- [[MortalCharacterService]] - Pressure logic
- [[CorruptionStageService]] - Stage advancement

## Related Systems

- [[Mission System]] - How corruption happens
- [[Seven Sins]] - Stat/need mapping
- [[Intervention Risk]] - Divine opposition

---

## See Also

### Design
- [[Corruption Philosophy]] - Why seven sins and needs
- [[Risk-Reward Balance]] - Intervention mechanics

### Development
- [[Adding a New Scheme]] - Creating corruption missions
- [[Testing Guide]] - Testing corruption flows

### Content
- [[Demo Targets]] - Knight, Queen, Bishop profiles
- [[Corruption Schemes]] - All available schemes
- [[Mission Beats]] - Narrative decision points
