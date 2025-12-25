---
type: index
domain: root
status: stable
tags:
  - index
  - hub
  - navigation
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
- [[GameState]] - Central state hub
- [[GameFlow]] - Phase state machine

### All Facades
| Facade | Domain | Purpose |
|--------|--------|---------|
| [[DemonManagementFacade]] | Demon | Roster, progression, training |
| [[CorruptionFacade]] | Corruption | Soul essence, missions |
| [[CultFacade]] | Cult | Meters, actions, bonuses |
| [[PlanningFacade]] | Planning | Weekly plans, opportunities |
| [[CombatFacade]] | Combat | Battles, tournaments |
| [[InventoryFacade]] | Inventory | Items, crafting |
| [[MortalCharacterFacade]] | Mortal | Characters, pressure |
| [[RealmFacade]] | Realm | Realms, entity stats |
| [[StoryFacade]] | Story | Narrative flags |
| [[UnlockFacade]] | Unlock | Unlock state |

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

---

## Game Content
- [[Content Catalog]] - Complete content inventory
- [[Demo Targets]] - Knight, Queen, Bishop profiles
- [[Starting Demons]] - Available demon roster (10)
- [[Corruption Schemes]] - Mission definitions (21)
- [[Verbs]] - Demon abilities (13+)
- [[Mission Beats]] - Narrative decision points (30+)
- [[Event Packs]] - All event packs (87 events)
- [[Training Activities]] - Stat improvement (14)
- [[Explorations]] - Domain maps (5)
- [[Tournaments]] - Combat gauntlets (3)
- [[Weekly Activities]] - Rest and recovery (4)
- [[Cult Situations]] - Cult narrative events

### Data Resources
- [[Data Resources]] - Resource overview
- [[DemonData]] - Demon data structure
- [[MissionStateData]] - Mission runtime state
- [[CultState]] - Cult meters and identity
- [[HellWeeklyPlan]] - Weekly planning data
- [[Mortal Character Data]] - Character structure

---

## Design Philosophy
Why systems work the way they do:

- [[Corruption Philosophy]] - Seven sins, needs, desperation
- [[Demon Economy]] - Mutually exclusive activities, progression
- [[Risk-Reward Balance]] - Intervention, slider, beats

---

## Development Guides
Practical guides for developers:

- [[Testing Guide]] - Running and writing tests
- [[Adding a New Demon]] - Step-by-step demon creation
- [[Adding a New Scheme]] - Step-by-step scheme creation
- [[Common Patterns]] - Code patterns and idioms

---

## Project Status
- [[Roadmap]] - Planned features and direction
- [[Known Issues]] - Current bugs and limitations

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

### Key File Locations

| Content | Path |
|---------|------|
| Demons | `data/demons/` |
| Schemes | `data/planning/corruption_schemes/` |
| Events | `data/events/packs/` |
| Verbs | `data/planning/verbs/` |
| Training | `data/planning/training_activities/` |
| Characters | `data/mortal_characters/` |

---

## Graph View

Use Obsidian's graph view to see how systems connect:
- **Facades** link to their **Managers** and **Services**
- **Systems** link to their **Concepts**
- **Concepts** cross-link to related mechanics
- **Design** docs explain the **why** behind systems
- **Development** docs show **how** to work with code

The graph reveals the architecture's structure at a glance.
