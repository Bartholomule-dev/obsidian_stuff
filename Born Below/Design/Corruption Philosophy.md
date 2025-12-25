---
type: design
domain: philosophy
status: stable
tags:
  - design
  - philosophy
  - corruption
---
# Corruption Philosophy

The design rationale behind the corruption and sin systems in Born Below.

## Why Seven Sins?

The Seven Deadly Sins provide an immediately recognizable moral framework that players intuitively understand. Each sin maps to a psychological vulnerability:

| Sin | Human Need | Corruption Vector |
|-----|------------|-------------------|
| **Wrath** | Security | Fear, threat, protection |
| **Envy** | Standing | Status, comparison, jealousy |
| **Pride** | Esteem | Recognition, validation, ego |
| **Greed** | Wealth | Money, possessions, power |
| **Lust** | Desire | Pleasure, forbidden wants |
| **Gluttony** | Comfort | Excess, indulgence, escape |
| **Sloth** | Purpose | Meaning, motivation, despair |

### Design Goals

1. **Dual Nature** - Same stats work for demons (offensive power) and mortals (defensive needs)
2. **Strategic Matching** - Players match demon specialties to mortal vulnerabilities
3. **Moral Ambiguity** - Needs are legitimate; corruption exploits them, not creates them

## The Needs System

### Why Needs Instead of Hit Points?

Traditional "corruption meters" feel gamey and disconnected. Needs create:

- **Narrative Coherence** - Characters act desperately when needs are low
- **Emergent Stories** - Low Security + High Pride = paranoid tyrant
- **Strategic Depth** - Multiple paths to the same corruption stage

### Need Decay Philosophy

Needs naturally recover unless pressured. This creates:

- **Urgency** - Sustained pressure required, not spike damage
- **Resource Management** - Can't corrupt everyone simultaneously
- **Tactical Retreat** - Sometimes backing off is strategic

## Corruption Stages

### The Four-Stage Model

| Stage | Description | Player Fantasy |
|-------|-------------|----------------|
| 0 | Virtuous | Untouched, pure |
| 1 | Tempted | Seeds planted |
| 2 | Compromised | Actively struggling |
| 3 | Fallen | Embracing darkness |
| 4 | Corrupted | Victory condition |

### Why Stages Instead of Percentage?

- **Clear Milestones** - Players know when they've progressed
- **Narrative Beats** - Each stage unlocks new schemes/events
- **Consequence Thresholds** - Divine intervention scales with stages

## Desperate Behaviors

The bridge between mechanical needs and narrative corruption:

```
Low Need → Desperate Behavior → Scandal → Stage Advancement
```

### Design Intent

Characters aren't evil - they're **desperate**. The Knight doesn't become corrupt because he's bad; he becomes corrupt because:
- His Pride is crushed (esteem need critical)
- He seeks validation through increasingly extreme acts
- Each desperate act deepens his fall

This frames players as **tempters, not destroyers**.

## The Intervention Risk Balance

### Philosophy

Power should have consequences. Aggressive corruption attracts divine attention because:

1. **Narrative Logic** - Heaven notices when Hell succeeds
2. **Strategic Tension** - Risk/reward on every mission
3. **Catch-Up Mechanic** - Protects the simulation from runaway success

### The Slider Mechanic

The Pressure/Subtlety slider embodies this philosophy:
- **Aggressive** = Fast progress, high risk
- **Subtle** = Slow progress, safe play
- **No "correct" answer** - Context determines optimal choice

## Related

- [[Seven Sins]] - Stat implementation
- [[Corruption System]] - Mechanical systems
- [[Intervention Risk]] - Risk mechanics
- [[Beats]] - Narrative decision points
