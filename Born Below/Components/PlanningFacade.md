---
type: facade
domain: planning
file: PlanningFacade.gd
status: stable
---
# PlanningFacade

Unified interface for planning phase operations.

## Purpose

Manages threat intel, weekly plans, opportunity cards, activity selection, and planning completeness checks.

## Dependencies

- [[PlanningPhaseManager]] - Content registries, weekly plan
- [[PlanningWorkflowService]] - Workflows
- [[RealmCoordinator]] - Realm state
- [[OpportunityGenerationService]] - Card generation
- [[OpportunityCooldownService]] - Cooldown tracking
- [[ActivitySelectionService]] - Character activities

## Key Responsibilities

### Threat Intel
- `get_threat_intel_level()` - Current level
- `set_threat_intel_level(level)` - Set level
- `increase_threat_intel(amount)` - Increase

### Weekly Plan
- `get_hell_weekly_plan()` - Current plan
- `reset_week_plan()` - Reset for new week

### Content Access
- `get_unlocked_explorations()` - Available explorations
- `get_unlocked_tournaments()` - Available tournaments
- `get_all_domains()` - All domains

### Opportunity System
- `get_available_opportunities(context)` - Generate cards
- `get_current_opportunities()` - Persisted cards
- `set_current_opportunities(cards)` - Set board
- `clear_opportunity(card_id)` - Remove used card
- `add_opportunity_cooldown(key, weeks)` - Add cooldown
- `tick_opportunity_cooldowns()` - End-of-week decrement
- `tick_opportunity_expirations()` - Remove expired

### Activity Selection
- `get_activity_for_character(character)` - Weekly activity
- `reset_activity_selection_cache()` - Clear cache

### Planning Completeness
- `is_planning_complete()` - All demons assigned?
- `get_unassigned_demon_ids()` - Who needs assignment?

## Related

- [[Week Flow]] - Phase timing
- [[Mission System]] - What opportunities lead to
- [[PlanningPhaseManager]] - State owner
