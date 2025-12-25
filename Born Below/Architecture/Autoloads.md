---
type: moc
domain: architecture
layer: autoload
status: stable
---
# Autoloads

Global singletons that provide core infrastructure. These are the entry points for the game's systems.

## Core Autoloads

| Autoload | Purpose |
|----------|---------|
| **[[GameState]]** | Central access point for all facades |
| **EventBus** | Signal hub for all game events |
| **[[Event System\|EventSystem]]** | Event loading, queuing, template registration |
| **[[GameFlow]]** | Phase state machine |
| **CorruptionManager** | Corruption state, soul essence |
| **InterventionRiskMeter** | Divine intervention tracking |
| **GameLogger** | Logging infrastructure |
| **GameConstants** | Global constants |

## GameState

The primary access point for game systems:

```gdscript
# Get facades
var demon_facade = GameState.get_demon_facade()
var corruption_facade = GameState.get_corruption_facade()
var planning_facade = GameState.get_planning_facade()
# ... 10 facades total
```

## EventBus

Central signal hub. All signals flow through EventBus:

```gdscript
# UI events (fire-and-forget)
EventBus.scheme_ui_selected.emit(scheme_id)

# State changes (with history)
EventBus.publish_demon_retired(demon_id, career_summary)
```

## GameFlow

Phase state machine:
- PLANNING → EXECUTING → RESULTS → END_WEEK

```gdscript
GameFlow.transition_to(GameFlow.Phase.EXECUTING)
var current = GameFlow.get_current_phase()
```

## EventSystem

Manages event packs and templates:

```gdscript
EventSystem.get_events_for_context("weekly")
EventSystem.collect_end_of_week_events()
```
