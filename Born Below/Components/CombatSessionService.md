---
type: service
domain: combat
file: CombatSessionService.gd
status: stable
---
# CombatSessionService

Centralizes the visual combat lifecycle, managing viewport transitions and controller orchestration.

## Purpose

Manages the full visual combat experience including viewport setup, animation control, and outcome reporting.

## Key Responsibilities

- Resolves and manages combat viewport via CenterViewportRegion
- Orchestrates CombatVisualController instances for animated battles
- Handles environmental scaling (HP carry-over, enemy scaling) for tournaments
- Ensures consistent UI state restoration after combat

## Key Methods

| Method | Purpose |
|--------|---------|
| `present_visual_combat(...)` | Primary async method for visual battle |
| `initialize(facade, state, viewport)` | Set up dependencies |
| `_create_error_outcome(...)` | Safe fallback for failures |

## Visual Combat Flow

```
present_visual_combat()
    ├── Acquire viewport from CenterViewportRegion
    ├── Create CombatVisualController
    ├── Run animated battle sequence
    │   ├── Show combatants
    │   ├── Animate turns
    │   └── Display outcome
    ├── Restore UI state
    └── Return CombatOutcomeEvent
```

## Tournament Support

Special handling for tournaments:
- **HP Carry-Over:** Damage persists between rounds
- **Enemy Scaling:** Later rounds have stat multipliers
- **Progressive Rewards:** Per-round reward tracking

## Related

- [[CombatFacade]] - Public API layer
- [[Combat System]] - System overview
- [[CombatResolutionService]] - Battle math
- [[Tournament System]] - Tournament integration
