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
- [[Managers]] - State owners (21 managers)
- [[Services]] - Domain logic (49 services)
- [[Autoloads]] - Global singletons

### Systems
- [[Demon System]] - Demon mechanics, progression, moods, quests
- [[Corruption System]] - Mortal corruption, needs, pressure
- [[Mission System]] - Weekly missions, meters, beats
- [[Cult System]] - Cult management, actions, meters
- [[Combat System]] - Battles, tournaments, visual combat
- [[Exploration System]] - Procedural maps, encounters
- [[Event System]] - Unified events, templates, DSL

### Concepts
- [[Seven Sins]] - Core stat system
- [[Week Flow]] - Game phases and timing
- [[Intervention Risk]] - Divine opposition
- [[Beats]] - Mission narrative thresholds

### Data
- [[Demon Data]] - Demon resource structure
- [[Mortal Character Data]] - Character resource structure
- [[Activity Templates]] - Weekly activity definitions

---

## Quick Reference

| Layer | Purpose | Count |
|-------|---------|-------|
| Facades | Focused API, cached reads | 10 |
| Managers | State owners, CRUD | 21 |
| Services | Domain logic, orchestration | 49 |

**Signal Pattern:** All signals through EventBus
- State changes: past-tense verbs via `publish_*()`
- UI events: `*_requested`, `*_selected` via `.emit()`
