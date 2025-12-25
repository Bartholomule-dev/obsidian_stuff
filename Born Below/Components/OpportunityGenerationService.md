---
type: service
domain: mission
file: OpportunityGenerationService.gd
status: stable
---
# OpportunityGenerationService

Creates the pool of available mission opportunities each week by polling character activities and world state.

## Purpose

Generates the mission cards players choose from during planning phase.

## Key Responsibilities

- Generates cards from character activities with exposed sins and starting meters
- Injects world-event and demon-driven opportunities for variety
- Modifies card stats based on active Discoveries from exploration
- Prioritizes and filters to present balanced 3-5 card selection

## Key Methods

| Method | Purpose |
|--------|---------|
| `generate_opportunities()` | Create full opportunity pool |
| `generate_activity_card()` | Single activity-based card |
| `_apply_discovery_enhancements()` | Boost cards with discoveries |
| `_select_final_cards()` | Filter to final selection |

## Card Sources

| Source | Description |
|--------|-------------|
| Activity | Character's weekly activity exposes vulnerabilities |
| World Event | Global events create opportunities |
| Demon-Driven | Demon abilities unlock special missions |
| Discovery | Exploration findings enhance existing cards |

## Card Selection

1. Generate all possible cards
2. Apply discovery enhancements
3. Filter by cooldowns
4. Score by variety and relevance
5. Select top 3-5 cards

## Discovery Enhancements

Discoveries can:
- Increase starting Leverage
- Decrease starting Suspicion
- Reveal hidden vulnerabilities

## Related

- [[Mission System]] - System overview
- [[PlanningFacade]] - Exposes opportunities
- [[OpportunityCooldownService]] - Prevents repeats
