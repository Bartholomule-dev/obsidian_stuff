---
type: autoload
domain: corruption
file: CorruptionManager.gd
status: stable
---
# CorruptionManager

Coordinates dual-realm mechanics, translating demon activities in Hell into corruption and divine heat in the Mortal Realm.

## Purpose

Primary interface for applying corruption pressure and managing the soul essence economy.

## Key Responsibilities

- Acts as primary interface for applying pressure to mortal character needs
- Manages Soul Essence economy (generation, spending, refunds)
- Processes scheme/mission outcomes with realm stat changes
- Calculates "Divine Heat" based on sin loudness and target holiness

## Key Methods

| Method | Purpose |
|--------|---------|
| `apply_character_pressure()` | Apply need pressure |
| `generate_soul_essence()` | Create soul essence |
| `process_scheme_completion()` | Handle scheme end |
| `increase_intervention_risk()` | Add divine risk |

## Divine Heat Formula

```
Heat = Sin Loudness × Target Holiness × Scheme Visibility
```

**Sin Loudness:**
- Wrath: High (visible violence)
- Lust: Medium (scandalous)
- Sloth: Low (subtle)

## Soul Essence Flow

```
Sources                      Sinks
────────                     ─────
Corrupted Characters    →    Demon Recruitment
Cult Income            →    Training Activities
Mission Rewards        →    Mission Costs
                       →    Morale Restoration
```

## Related

- [[CorruptionFacade]] - Public API layer
- [[Corruption System]] - System overview
- [[Intervention Risk]] - Heat effects
- [[RealmCoordinator]] - Soul essence storage
