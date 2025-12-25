---
type: content
domain: cult
status: stable
---
# Cult Situations

Narrative events triggered by cult state (identity, heat, dissent). Part of the [[Cult System]].

## Identity-Based Situations

### Merchant Identity
Triggered when `cult.identity == 'merchant'`

| Event | Choices | Effects |
|-------|---------|---------|
| **Merchant Deal** | Accept Investment / Recruit Merchant | +20 SE / Size +4, Heat +2 |

### Zealot Identity
Triggered when `cult.identity == 'zealot'`

| Event | Choices | Effects |
|-------|---------|---------|
| **Zealot Fervor** | Harness Fervor / Temper Passion | Fervor +5 / Dissent -3, Secrecy +2 |

### Shadow Identity
Triggered when `cult.identity == 'shadow'`

| Event | Choices | Effects |
|-------|---------|---------|
| **Shadow Opportunity** | Exploit Opening / Strengthen Cover | Heat -4 / Secrecy +6 |

## Pressure Situations

### External Pressure
Triggered when `cult.heat >= 60`

| Event | Choices | Effects |
|-------|---------|---------|
| **Under Scrutiny** | Go Underground / Brazen It Out | Heat -8, Action Power halved / Fervor +4, Heat +5 |

### Internal Strife
Triggered when `cult.dissent >= 40`

| Event | Choices | Effects |
|-------|---------|---------|
| **Murmurs of Dissent** | Assert Dominance / Compromise | Dissent -6, Heat +3 / Action Power -3, Dissent -4 |

## Random Opportunities

### General Opportunity
Random trigger, no conditions.

| Event | Choices | Effects |
|-------|---------|---------|
| **Opportunity Arises** | Expand Operations / Gather Resources | Size/Fervor +4 / +15 SE, Size +2 |

## Situation Mechanics

Situations are processed by [[CultExecutionService]] during the cult phase:

1. Check trigger conditions (identity, meters)
2. Present choices to player
3. Apply selected effects
4. Log to activity feed

## Related

- [[Cult System]] - Parent system
- [[CultExecutionService]] - Situation processing
- [[CultManager]] - Cult state
- [[CultFacade]] - Cult access
- [[Event System]] - Event handling
