---
type: service
domain: mission
file: VerbService.gd
status: stable
---
# VerbService

Manages demon verb definitions, eligibility checks, and mission loadout validation.

## Overview

VerbService handles the "Verb" system - abilities that demons can use during corruption schemes. Verbs are equipped into loadouts and affect mission meter calculations.

## Key Responsibilities

- Load verb definitions from data files
- Check demon eligibility for specific verbs
- Validate mission loadouts
- Calculate loadout meter modifiers

## Key Methods

| Method | Purpose |
|--------|---------|
| `load_all_verbs()` | Load verb definitions from data |
| `get_eligible_verbs()` | Filter verbs for specific demon |
| `validate_loadout()` | Check loadout validity |
| `get_loadout_meter_modifiers()` | Calculate meter effects |

## Dependencies

- `VerbData` resources - Verb definitions
- [[DemonProgressionService]] - Level/stat requirements
- `MissionStateData` - Active mission context

## Verb System

Verbs represent demon abilities used during schemes:
- Each verb has requirements (level, stats)
- Verbs modify mission meters (Leverage, Suspicion, Fatigue)
- Demons equip verbs into loadouts before missions
- Verb effects trigger during mission execution

## Data Location

Verb definitions: `data/planning/verbs/`

## Related

- [[Mission System]] - Verb usage during missions
- [[MissionMeterService]] - Meter modifications
- [[Demon System]] - Verb eligibility
- [[PlanningFacade]] - Loadout management
