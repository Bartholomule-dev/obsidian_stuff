---
type: service
domain: exploration
file: exploration/BuffEffectProcessor.gd
status: stable
---
# BuffEffectProcessor

Applies expedition buff and curse effects to demons during exploration.

## Overview

Extracted from ExplorationService to handle buff effect application. Processes energy restoration from buffs and applies curse penalties (energy drain, stress).

## Key Methods

| Method | Purpose |
|--------|---------|
| `apply_energy_restoration()` | Applies energy buffs based on trigger type |
| `apply_curse_effects()` | Applies curse penalties (drain, stress) |

## Buff Types

### Energy Restoration
| Modifier Type | Trigger |
|---------------|---------|
| `restore_energy` | Always applies |
| `restore_energy_on_success` | Only on successful encounters |

### Curse Effects
| Curse Type | Effect |
|------------|--------|
| `drain_energy` | Reduces demon energy |
| `add_stress` | Increases demon stress |

## Usage

```gdscript
# Apply energy buffs after successful encounter
processor.apply_energy_restoration(demon_id, active_buffs, "success")

# Apply curse effects at end of node
processor.apply_curse_effects(demon_id, active_buffs)
```

## Dependencies

- [[DemonMoodService]] - Energy and stress modification

## Related

- [[NodeEncounterResolver]] - Primary consumer
- [[ExplorationService]] - Exploration orchestration
