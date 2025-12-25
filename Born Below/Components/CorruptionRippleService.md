---
type: service
domain: corruption
file: CorruptionRippleService.gd
status: stable
---
# CorruptionRippleService

Manages secondary effects and narrative consequences that ripple through relationships when characters are corrupted.

## Purpose

Handles cascade effects when corruption spreads through social networks.

## Key Responsibilities

- Applies ripple effects to related characters (need modifications, vulnerabilities)
- Manages scheme effectiveness modifiers from corruption
- Orchestrates signature ripples (unique narrative events)
- Tracks ripple history to prevent duplicates

## Key Methods

| Method | Purpose |
|--------|---------|
| `apply_ripple_effects(corrupted_id)` | Execute relationship cascades |
| `check_signature_ripples(char_id, stage)` | Check for narrative triggers |
| `get_scheme_modifier(char_id, sin)` | Effectiveness multipliers |
| `is_special_scheme_unlocked(scheme_id)` | Check ripple-unlocked schemes |

## Ripple Effects by Relationship

| Relationship | Effect |
|--------------|--------|
| Strong Ally (60+) | -15 Security |
| Ally (30-59) | -10 Security |
| Rival (-30 to -59) | -5 Standing |
| Enemy (-60-) | -10 Standing |

## Scheme Modifiers

Post-corruption modifiers:
- **Ally of corrupted:** +20% pressure effectiveness
- **Enemy of corrupted:** -10% pressure effectiveness

## Special Scheme Unlocks

Corruption can unlock:
- `scheme_blackmail_accomplice`
- `scheme_corrupt_network`

## Related

- [[Corruption Ripple]] - Concept overview
- [[Corruption System]] - System overview
- [[MortalCharacterService]] - Triggers ripples
