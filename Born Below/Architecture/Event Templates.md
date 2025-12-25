---
type: moc
domain: events
status: stable
---
# Event Templates

Templates define how different event types are processed, displayed, and resolved.

## All Templates

| Template | Purpose | Autonomous |
|----------|---------|------------|
| **DemonDemandTemplate** | Demon requests (rest, glory, schemes) | Yes |
| **DemonActionTemplate** | Autonomous behaviors (theft, sabotage) | Yes |
| **DemonMilestoneTemplate** | Achievements (level-up, training complete) | Yes |
| **DemonFeedbackTemplate** | State notifications (mood, loyalty) | No |
| **CorruptionStageTemplate** | Corruption progression, danger zones | No |
| **MortalEventTemplate** | Desperate actions, vulnerabilities | No |
| **DivineCleanseTemplate** | Divine intervention consequences | No |
| **AchievementTemplate** | Player achievements | No |
| **MissionBeatTemplate** | Mission threshold decisions | No |
| **CultEventTemplate** | Cult action outcomes, situation events | No |
| **DiscoveryTemplate** | Exploration discoveries | No |

## Template Structure

All templates extend `EventTemplate` base class:

```gdscript
class_name DemonDemandTemplate extends EventTemplate

func get_template_id() -> String:
    return "demon_demand"

func generate_event(context: Dictionary) -> GameEvent:
    # Build event based on context
    pass
```

## Registration

Templates register in `TemplateRegistry._ready()`:
```gdscript
register_template("demon_demand", DemonDemandTemplate.new())
```

## Template Categories

### Autonomous Templates
Triggered by game simulation without player action:
- DemonDemandTemplate
- DemonActionTemplate
- DemonMilestoneTemplate

### Notification Templates
Inform player of state changes:
- DemonFeedbackTemplate
- CorruptionStageTemplate
- MortalEventTemplate
- AchievementTemplate

### Decision Templates
Require player choice:
- MissionBeatTemplate
- CultEventTemplate

### Consequence Templates
Result from other actions:
- DivineCleanseTemplate
- DiscoveryTemplate

## Related

- [[Event System]] - Event processing
- [[Beats]] - MissionBeatTemplate usage
- [[Autonomous Behavior]] - DemonActionTemplate triggers
- [[Mission Beats]] - Beat content catalog
- [[Cult Situations]] - CultEventTemplate content
- [[GameState]] - Event context access
