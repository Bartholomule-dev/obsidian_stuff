---
type: index
domain: root
status: stable
---
# Born Below

A demon-raising corruption simulator built in Godot 4.5 with GDScript.

## Game Overview

**Two Interconnected Systems:**
1. **Demon Raising** - Recruit, train, and develop demons with personalities, memories, loyalty, and progression
2. **Corruption Simulator** - Deploy demons on missions to corrupt mortal characters through their seven needs

**Core Loop:** Planning → Execution → Results → End Week Reset

**Demo Victory:** Corrupt the Knight, Bishop, and Queen to Corruption Stage 4

---

## Navigation

### Architecture
- [[Facades]] - Public API layer (10 facades)
- [[Managers]] - State owners (21+ managers)
- [[Services]] - Domain logic (49+ services)
- [[Autoloads]] - Global singletons

### Core Systems
- [[Demon System]] - Demon mechanics, progression, moods, quests
- [[Corruption System]] - Mortal corruption, needs, pressure
- [[Mission System]] - Weekly missions, meters, beats
- [[Cult System]] - Cult management, actions, meters
- [[Combat System]] - Battles, tournaments, visual combat
- [[Tournament System]] - Multi-round gauntlets
- [[Exploration System]] - Procedural maps, encounters
- [[Event System]] - Unified events, templates, DSL
- [[Economy System]] - Soul essence, income, costs
- [[UI System]] - Modals, widgets, regions

### Demon Mechanics
- [[Seven Sins]] - Core stat system
- [[Demon Ranks]] - Lesser, Greater, Archdemon
- [[Memory System]] - Memories and loyalty
- [[Personality Evolution]] - Archetypes and mutation
- [[Autonomous Behavior]] - Demon AI actions

### Corruption Mechanics
- [[Corruption Flavors]] - Outcome types
- [[Corruption Ripple]] - Cascade effects
- [[Awareness System]] - Target suspicion
- [[Character Defenses]] - AI resistance
- [[Need Recovery]] - Natural healing

### Game Flow
- [[Week Flow]] - Game phases and timing
- [[Intervention Risk]] - Divine opposition
- [[Beats]] - Mission narrative thresholds

### Data & Content
- [[Data Resources]] - Resource types and locations

### Game Content
- [[Content Catalog]] - Complete content inventory
- [[Verbs]] - Demon abilities (13+)
- [[Corruption Schemes]] - Mission definitions (21)
- [[Mission Beats]] - Narrative decision points (30+)
- [[Training Activities]] - Stat improvement (14)
- [[Explorations]] - Domain maps (5)
- [[Tournaments]] - Combat gauntlets (3)
- [[Weekly Activities]] - Rest and recovery (4)
- [[Cult Situations]] - Cult narrative events

---

## Quick Reference

| Layer | Purpose | Count |
|-------|---------|-------|
| Facades | Focused API, cached reads | 10 |
| Managers | State owners, CRUD | 21+ |
| Services | Domain logic, orchestration | 49+ |

### Signal Pattern
All signals through EventBus:
- State changes: past-tense verbs via `publish_*()`
- UI events: `*_requested`, `*_selected` via `.emit()`

### Event Contexts
| Context | When Triggered |
|---------|----------------|
| `weekly` | Daily checks during execution |
| `scheme` | During mission execution |
| `queued` | High-priority explicit events |
| `end_of_week` | Results phase whispers |

---

## Graph View

Use Obsidian's graph view to see how systems connect:
- **Facades** link to their **Managers** and **Services**
- **Systems** link to their **Concepts**
- **Concepts** cross-link to related mechanics

The graph reveals the architecture's structure at a glance.
