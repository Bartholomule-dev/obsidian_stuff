---
type: concept
domain: demon
status: stable
---
# Personality Evolution

Demons evolve their personality archetype based on accumulated experiences, triggering mutation events with player choices.

## Base Archetypes

| Archetype | Trait | Description | Stress Threshold |
|-----------|-------|-------------|------------------|
| **aggressive** | prideful | Demands glory and recognition | 60 |
| **arrogant** | prideful | Craves status, sensitive to slights | 60 |
| **sadistic** | cruel | Enjoys suffering, may sabotage | 40 |
| **cunning** | deceitful | Manipulative, may steal | 70 |
| **analytical** | obsessive | Perfectionist, prone to burnout | 80 |
| **zealous** | fanatical | Ideology-driven, demands religious missions | 50 |

## Drift Stats

Demons accumulate drift based on experiences:
- `scheme_successes` - Successful schemes
- `praised` - Times praised by player
- `combat_wins` - Tournament victories
- `scheme_failures` - Failed schemes
- `scolded` - Times scolded
- `combat_losses` - Combat defeats

## Mutation Pathways

| Base | Stage 1 (50) | Stage 2 (100) | Drift Stat |
|------|-------------|---------------|------------|
| aggressive | tyrannical | despotic | pride_accumulation |
| cunning | manipulative | machiavellian | deception_success |
| arrogant | narcissistic | megalomaniacal | ego_inflation |
| analytical | obsessive | neurotic | obsession_level |
| sadistic | torturous | sociopathic | cruelty_score |
| zealous | fanatical | extremist | ideology_fervor |

## Mutation Events

When drift reaches threshold, player chooses:

| Choice | Effect |
|--------|--------|
| **Embrace** | Full archetype change |
| **Moderate** | Hybrid traits (original + new) |
| **Reject** | Keep original, reset drift |

## Drift Thresholds

- **15 (Early):** Notification about emerging patterns
- **30 (Notable):** Significant narrative event
- **50/100 (Mutation):** Full transformation event

## Weekly Decay

Drift stats decay if experiences stop reinforcing patterns, preventing unintended mutations from isolated incidents.

## Signals

```gdscript
personality_drift_threshold_reached.emit({demon_id, drift_type, threshold})
demon_personality_mutated.emit({demon_id, old_archetype, new_archetype, choice})
```

## Related

- [[Demon System]] - Parent system
- [[Memory System]] - Mutations create memories
- [[Autonomous Behavior]] - Personality affects actions
