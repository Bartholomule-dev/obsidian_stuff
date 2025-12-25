---
type: catalog
domain: content
status: stable
---
# Content Catalog

Complete inventory of game content - the actual missions, abilities, and activities available in Born Below.

## Content Overview

| Category | Count | Description |
|----------|-------|-------------|
| [[Verbs]] | 13+ | Demon abilities for missions |
| [[Corruption Schemes]] | 21 | Character-specific mission types |
| [[Mission Beats]] | 30+ | Narrative decision points |
| [[Training Activities]] | 14 | Stat improvement activities |
| [[Explorations]] | 5 | Domain exploration maps |
| [[Tournaments]] | 3 | Combat gauntlets |
| [[Weekly Activities]] | 4 | Rest and recovery options |

## Content Relationships

```
Training → Stat Requirements → Verbs
    ↓              ↓
Tournaments    Schemes ← Beats
    ↓              ↓
  XP/Stats    Explorations/Domains
```

### Progression Flow

1. **Train demons** to raise [[Seven Sins]] stats
2. **Unlock verbs** via stat thresholds
3. **Equip verbs** for corruption missions
4. **Execute schemes** against targets
5. **Navigate beats** during execution
6. **Explore domains** for discoveries

## By Target Character

### The Knight
- 7 corruption schemes (combat/honor focus)
- Activity beats for each scheme
- Martial Quarter domain exploration

### The Queen
- 7 corruption schemes (power/intrigue focus)
- Activity beats for each scheme
- Royal Court domain exploration

### The Bishop
- 7 corruption schemes (faith/doubt focus)
- Activity beats for each scheme
- Sacred District domain exploration

## Data Locations

| Content Type | Path |
|--------------|------|
| Schemes | `data/planning/corruption_schemes/` |
| Verbs | `data/planning/verbs/` |
| Training | `data/planning/training_activities/` |
| Tournaments | `data/planning/tournaments/` |
| Explorations | `data/planning/explorations/` |
| Beats | `data/events/packs/mission/` |
| Activities | `data/activities/templates/` |

## Related Systems

- [[Mission System]] - Executes schemes and beats
- [[Demon System]] - Uses verbs and training
- [[Exploration System]] - Domain content
- [[VerbService]] - Verb management
- [[MissionBeatService]] - Beat triggering
