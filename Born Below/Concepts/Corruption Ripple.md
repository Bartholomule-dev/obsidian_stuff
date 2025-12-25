---
type: concept
domain: mortal
status: stable
---
# Corruption Ripple

When a character becomes corrupted, it affects related characters based on their relationships.

## Trigger

Character reaches "Corrupted" stage (3+ needs ≤ 10)

## Relationship-Based Effects

| Relationship | Strength | Effect on Related Character |
|--------------|----------|----------------------------|
| Strong Ally | 60+ | -15 Security ("trusted friend fell") |
| Ally | 30-59 | -10 Security |
| Neutral | -29 to 29 | No effect |
| Rival | -30 to -59 | -5 Standing (hollow victory) |
| Enemy | -60 or below | -10 Standing |

## Cascade Mechanics

1. Find all characters with relationship to corrupted
2. Apply need pressure based on relationship strength/type
3. Strong allies lose Security (fear)
4. Enemies lose Standing (vindication backfires)

## Special Unlocks

Corruption can unlock special scheme opportunities:
- `scheme_blackmail_accomplice`
- `scheme_corrupt_network`

## Scheme Effectiveness Modifiers

Related characters have modified vulnerability:
- **Ally of corrupted:** +20% pressure (demoralized)
- **Enemy of corrupted:** -10% pressure (emboldened)

## Strategy Implications

- **Target connected characters:** Ripple effects accelerate corruption
- **Corrupt leaders first:** More relationships = more cascade
- **Watch ally networks:** Strong ally relationships create fear cascades

## Related

- [[Corruption System]] - Parent system
- [[Mission System]] - Unlocks new opportunities
