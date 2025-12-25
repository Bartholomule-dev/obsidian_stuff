---
type: system
domain: ui
status: stable
tags:
  - ui
  - widgets
  - system
---
# UI Widgets

Reusable UI components that display game state and provide interaction points.

## Widget Categories

### Information Display

| Widget | Purpose | Location |
|--------|---------|----------|
| **DemonCardWidget** | Demon portrait, stats, status | Roster panel, selection |
| **StatBarWidget** | Sin stat visualization | Demon details |
| **TargetProgressWidget** | Corruption stage display | Mission HUD |
| **DangerGaugeWidget** | Intervention risk meter | Top bar |

### Mission UI

| Widget | Purpose | Location |
|--------|---------|----------|
| **MissionHUDWidget** | Active mission meters | Center during execution |
| **OpportunityCardWidget** | Mission card in board | Opportunity panel |
| **ActionPickerCard** | Verb/action selection | Assignment modal |

### Panels

| Panel | Purpose | Region |
|-------|---------|--------|
| **DemonRosterPanel** | Full roster view | Left panel |
| **OpportunityBoardPanel** | Weekly missions | Right panel |
| **ActivityLog** | Real-time event feed | Right panel |
| **HallOfFamePanel** | Retired demon records | Codex |
| **ExplorationMapUI** | Node map display | Center |

### Demon Roster Sections

| Section | Content |
|---------|---------|
| **DemonRosterPersonalitySection** | Archetype, traits |
| **DemonRosterEquipmentSection** | Equipped items |
| **DemonRosterHistorySection** | Timeline, achievements |
| **MemoriesSection** | Significant memories |

### Narrative

| Widget | Purpose |
|--------|---------|
| **DialogueBox** | Story text display |
| **NarratorDialogWidget** | Mordessa guidance |
| **NotificationToast** | Transient alerts |

### Utility

| Widget | Purpose |
|--------|---------|
| **FilterSortWidget** | List filtering |
| **PanelHeaderWidget** | Section headers |

## Region Layout

```
┌─────────────────────────────────────────────┐
│                  TopBar                      │
│  Phase | Calendar | Soul Essence | Risk     │
├────────────┬───────────────────┬────────────┤
│            │                   │            │
│  LeftPanel │   CenterViewport  │ RightPanel │
│  (Demon)   │   (Diorama/Combat)│ (Log/Plan) │
│            │                   │            │
├────────────┴───────────────────┴────────────┤
│                 BottomBar                    │
│           Codex | Unleash buttons           │
└─────────────────────────────────────────────┘
```

## Widget Patterns

### State Binding
Widgets observe [[GameState]] via signals:
```gdscript
EventBus.demon_stats_changed.connect(_update_display)
```

### Theme Integration
All widgets use the central theme system for consistent styling.

## Controllers

| Controller | Purpose |
|------------|---------|
| **UIManager** | Widget lifecycle |
| **ModalManager** | Modal stacking |
| **UIEventManager** | UI signal routing |
| **ViewToggleController** | Panel visibility |

## Related

- [[UI System]] - System overview
- [[Modals]] - Full-screen overlays
- [[GameState]] - State binding
- [[Week Flow]] - Phase-dependent UI
