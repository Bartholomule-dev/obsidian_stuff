---
type: concept
domain: mortal
status: stable
---
# Awareness System

Characters track suspicion of demonic influence. Higher awareness makes characters harder to corrupt.

## Awareness Tiers

| Tier | Range | Pressure Modifier | State |
|------|-------|-------------------|-------|
| **Unaware** | 0-25 | 1.0x (full) | No suspicion |
| **Suspicious** | 26-50 | 0.85x | Noticing patterns |
| **Alert** | 51-75 | 0.70x | Actively watching |
| **Vigilant** | 76-100 | 0.50x | On high guard |

## Awareness Gain

Each successful scheme adds awareness:

```
awareness_gain = (100 - scheme_subtlety) / 10
```

- High subtlety (90+): ~1 awareness
- Low subtlety (30): ~7 awareness

## Awareness Decay

**-3 to -5 per week** (only if no schemes targeted character)

## Defense Triggers

| Awareness | Defense Activated |
|-----------|-------------------|
| 51+ (Alert) | [[Character Defenses#Seek Allies\|Seek Allies]] |
| 76+ (Vigilant) | [[Character Defenses#Divine Prayer\|Divine Prayer]] |

## Strategy Implications

- **High subtlety:** Slower but sustainable corruption
- **Low subtlety:** Fast but character becomes resistant
- **Rotate targets:** Let awareness decay
- **Avoid vigilance:** Prayer permanently increases intervention risk

## Related

- [[Corruption System]] - Parent system
- [[Character Defenses]] - Awareness triggers defenses
- [[Mission System]] - Subtlety affects awareness
