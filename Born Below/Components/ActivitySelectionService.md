---
type: service
domain: mission
file: ActivitySelectionService.gd
status: stable
---
# ActivitySelectionService

Selects and generates weekly activities (authored or procedural) for mortal characters based on their goals and current state.

## Overview

ActivitySelectionService populates the opportunity board with missions by selecting appropriate activities for mortal characters. It combines authored content with procedural generation.

## Key Responsibilities

- Select weekly activities for characters
- Generate procedural activities
- Validate activity conditions
- Manage activity caching

## Key Methods

| Method | Purpose |
|--------|---------|
| `select_weekly_activity()` | Choose activity for character |
| `_generate_activity()` | Procedurally create activity |
| `_meets_conditions()` | Validate activity prerequisites |
| `clear_week_cache()` | Reset weekly activity cache |

## Dependencies

- `CharacterActivityData` - Character activity associations
- `ActivityTemplate` - Activity definitions

## Selection Logic

Activities are selected based on:
- Character goals and desires
- Current need states
- Previous activity history
- Available templates

## Activity Types

- **Authored**: Pre-designed activities with specific narratives
- **Procedural**: Generated based on character state and templates

## Game Loop Integration

Called during [[Week Flow|Planning Phase]] to populate the "Opportunity Board" for the upcoming week. Missions available to target are determined by this service.

## Related

- [[Mission System]] - Uses selected activities
- [[OpportunityGenerationService]] - Board population
- [[PlanningFacade]] - Planning access
