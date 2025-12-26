---
type: status
domain: project
status: living
tags:
  - status
  - roadmap
  - planning
---
# Roadmap

Planned features and development direction for Born Below.

## Current Status: Demo Build

The demo showcases core systems with three corruption targets (Knight, Queen, Bishop).

---

## Completed Systems

### Core Loop
- [x] Weekly planning → execution → results cycle
- [x] Phase state machine (GameFlow)
- [x] Calendar and week progression

### Demon System
- [x] Demon roster management
- [x] Stats (Seven Sins)
- [x] Personality archetypes
- [x] Memory and loyalty
- [x] Mood and stress
- [x] XP and leveling
- [x] Verb system
- [x] Autonomous behaviors

### Mission System
- [x] Meter-based missions (leverage, suspicion, moral fatigue)
- [x] Beat system with player choices
- [x] Pressure/subtlety slider
- [x] Grace rules for beat pacing
- [x] Mission completion and rewards

### Corruption System
- [x] Seven needs per character
- [x] Corruption stages (0-4)
- [x] Desperate behaviors
- [x] Character defenses
- [x] Need recovery

### Cult System
- [x] Cult meters (size, fervor, secrecy, heat, dissent)
- [x] Weekly cult actions
- [x] Cult identity (zealot, shadow, merchant)
- [x] Cult income
- [x] Mission support bonuses

### Combat & Exploration
- [x] Visual combat system
- [x] Tournaments
- [x] Procedural exploration maps
- [x] Discovery system

### Divine Opposition
- [x] Intervention risk meter
- [x] Divine intervention events
- [x] Cleansing mechanics

---

## In Progress

### Polish & Balance
- [ ] Activity log enrichment
- [ ] Mission balance tuning
- [ ] Cult action balance
- [ ] Beat content expansion

### UI Improvements
- [ ] Improved tooltips
- [ ] Better meter visualization
- [ ] Activity preview enhancements

---

## Technical Debt & Refactoring

Priority areas identified from codebase analysis (December 2025).

### Critical: God Classes (Decomposition Needed)

| File | Lines | Issue |
|------|-------|-------|
| `ExplorationService.gd` | 1,212 | Map generation + encounters + buffs + UI coordination |
| `DemonMoodService.gd` | 1,144 | Happiness + energy + stress (3 distinct systems) |
| `DemonMemoryService.gd` | 1,045 | Memory CRUD + decay + loyalty + hardcoded templates |
| `SimulationPhaseCoordinator.gd` | 920 | 20 dependencies, 4 embedded phase executors |
| `ExplorationMapUI.gd` | 1,330 | 5 UI concerns, 43 methods, 2 cache systems |

**Recommended splits:**
- ExplorationService → MapGenerator + EncounterResolver + BuffCalculator
- DemonMoodService → HappinessState + StressState + EnergyState
- DemonMemoryService → MemoryDecayProcessor + LoyaltyCalculator + data file for templates
- SimulationPhaseCoordinator → HellPhaseExecutor + MortalPhaseExecutor + DivinePhaseExecutor

### Critical: Test Coverage Gaps

| Layer | Tested | Gap | Risk |
|-------|--------|-----|------|
| **Managers** | 5/21 | 76% untested | State corruption undetected |
| **Facades** | 3/10 | 70% untested | API regressions undetected |
| Services | 37/50 | 26% untested | Medium risk |

**Highest priority untested code:**
- [ ] `InventoryManager` (673 lines) - game economy
- [ ] `PlanningFacade` (523 lines) - mission system API
- [ ] `CorruptionFacade` (354 lines) - victory condition
- [ ] `DemonManagementFacade` (482 lines) - demon interaction API

### High: Architectural Violations

**Facade Bypasses (14+ instances):**
UI code directly accessing managers instead of facades.
- `QuestForecasting.gd` - chains through roster_manager → demon_manager → progression
- `DemonCardWidget.gd` - direct manager access
- `WeeklyPlannerPanel.gd` - mixed facade/manager access

**Service Self-Creation (7 instances):**
- `SimulationPhaseCoordinator` creates 4 services on-demand
- `MissionExecutorService` creates meter/beat services internally
- Facades creating services (should be injected via GameStateInitializer)

**Dead Code:**
- `WeeklyPlannerPanel.gd:174-177` connects to non-existent GameState signals

### High: Oversized Facades

| Facade | Lines | Methods | Recommendation |
|--------|-------|---------|----------------|
| `PlanningFacade` | 523 | 38 | Split: ThreatIntel + OpportunityBoard + ActivityPlanning |
| `DemonManagementFacade` | 482 | 58 | Split: Progression + Slots + core Roster |

### Medium: Manager Boundary Confusion

`RosterManager` (514 lines) and `DemonManager` (455 lines) have overlapping responsibilities. Clarify ownership boundaries.

### Refactoring Priority Order

1. **Immediate:** Add tests for InventoryManager, PlanningFacade, CorruptionFacade
2. **Short-term:** Decompose ExplorationService and DemonMoodService
3. **Medium-term:** Fix facade bypasses in UI, inject services properly
4. **Ongoing:** Split oversized facades as touched

---

## Planned Features

### Near Term
- [ ] More mission beats per character
- [ ] Additional demon verbs
- [ ] Cult situation events expansion
- [ ] New training activities

### Medium Term
- [ ] Additional corruption targets
- [ ] New demon archetypes
- [ ] Expanded exploration content
- [ ] Achievement system implementation

### Long Term
- [ ] Campaign structure beyond demo
- [ ] Persistent progression
- [ ] Additional realms/domains
- [ ] Mod support

---

## Design Considerations

### Under Evaluation
- Extended demon relationships
- Rival Hell factions
- Mortal allies/double agents
- Time pressure mechanics

### Deferred
- Multiplayer concepts
- Steam Workshop integration
- Mobile port considerations

## Related

- [[Known Issues]] - Current bugs
- [[Index]] - Full system overview
