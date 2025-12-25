---
type: system
domain: ui
status: stable
---
# UI System

The user interface layer built on Godot's Control nodes with a region-based layout and modal system.

## Screen Regions

| Region | Content |
|--------|---------|
| **TopBar** | Phase indicator, Calendar, Soul Essence, Intervention Risk |
| **BottomBar** | Codex button, Cult button, Mission HUD, Target Progress |
| **LeftPanel** | Selected demon details, demon roster |
| **RightPanel** | Activity Log, Weekly Planner |
| **CenterViewport** | Diorama (3D scene) or Combat arena |

## Modal System

Modals are managed by `ModalManager` and displayed above all regions.

### Key Modals

| Modal | Purpose | Trigger |
|-------|---------|---------|
| **UnifiedAssignmentModal** | Assign demons to activities | Click action card in planner |
| **EndOfWeekSummaryModal** | Week results summary | Results phase start |
| **ChoiceEventModal** | Player-driven choices | Demon demands, events |
| **NotificationModal** | Milestones, unlocks, warnings | Level-ups, corruption |
| **CodexModal** | Game reference/lore | Codex button |
| **CultManagementModal** | Cult management | Cult button |
| **BeatDecisionModal** | Mid-mission decisions | Mission beat triggered |
| **MortalCharacterDetailModal** | Character deep-dive | Click mortal character |
| **DemonSelectionModal** | Select demon from roster | Assignment flows |
| **DialogueBox** | Narrative progression | Game events |

## Widget Library

| Widget | Purpose |
|--------|---------|
| **ActionPickerCard** | Radio-style selection cards |
| **ActivityLog** | Event chronicle with sentiment coloring |
| **DangerGaugeWidget** | Risk/loyalty visualization |
| **DemonCardWidget** | Comprehensive demon info display |
| **FilterSortWidget** | Dropdown filter/sort controls |
| **MissionHUDWidget** | Active mission meters |
| **OpportunityCardWidget** | Mission selection cards |
| **PanelHeaderWidget** | Standardized panel headers |
| **StatBarWidget** | Stat display with progress bar |
| **TargetProgressWidget** | Corruption stage visualization |

## Key Controllers

- `MainController` - Root UI orchestration
- `UIManager` - UI state management
- `ModalManager` - Modal lifecycle
- `InfernalCommand` - Tab hub for demon management

## Observers

- `GameStateObserver` - Watches game state changes
- `UIObserver` - Watches UI state changes

## Related

- [[UI Widgets]] - Detailed widget documentation
- [[Modals]] - Detailed modal documentation
- [[Week Flow]] - UI changes per phase
- [[GameState]] - State binding for widgets
