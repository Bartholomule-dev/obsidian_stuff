---
type: system
domain: events
status: stable
---
# Event System

Unified system for all game events. Events are data-driven narratives that trigger based on context and conditions.

## Architecture

```
JSON Event Packs → EventSystem → Template Processing → UI Display
      ↓                ↓               ↓                  ↓
  data/events/    Load & queue    Apply effects      Modal/Toast
```

## Event Contexts

| Context | When Triggered | Example |
|---------|----------------|---------|
| `weekly` | Daily checks | Random demon events |
| `scheme` | During schemes | Mission complications |
| `queued` | High priority | Level-up celebrations |
| `end_of_week` | Results phase | Court whispers |

## Event Templates (11 Types)

| Template | Purpose | Autonomous |
|----------|---------|------------|
| DemonDemandTemplate | Demon demands | Yes |
| DemonActionTemplate | Demon behaviors | Yes |
| DemonMilestoneTemplate | Achievements | Yes |
| DemonFeedbackTemplate | Notifications | No |
| CorruptionStageTemplate | Stage changes | No |
| MortalEventTemplate | Desperate actions | No |
| DivineCleanseTemplate | Intervention | No |
| AchievementTemplate | Player achievements | No |
| MissionBeatTemplate | Mission decisions | No |
| CultEventTemplate | Cult outcomes | No |
| DiscoveryTemplate | Exploration finds | No |

## Event Pack Structure

```
data/events/packs/
├── cult/
│   ├── _pack.json
│   └── situation_*.json
├── demon/
│   ├── _pack.json
│   └── *.json
└── demo/
    └── _pack.json
```

## Event JSON Format

```json
{
  "event_id": "unique_id",
  "template": "DemonActionTemplate",
  "context": "weekly",
  "conditions": { ... },
  "content": {
    "title": "Event Title",
    "description": "What happened..."
  },
  "effects": [ ... ]
}
```

## Key Rules

1. **ALL events use EventSystem** - No separate event services
2. **Text is inline** - No separate text bundles
3. **JSON in packs** - No .tres files for events
4. **Templates register** - All in TemplateRegistry

## Key Components

- EventSystem (autoload) - Load, queue, process
- TemplateRegistry - Template registration
- `scripts/core/events/templates/` - Template classes

## Related Systems

- [[Week Flow]] - Event timing
- [[Demon System]] - Demon events
- [[Cult System]] - Cult events
