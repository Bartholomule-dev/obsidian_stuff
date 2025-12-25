---
type: manager
domain: mortal
file: MortalCharacterManager.gd
status: stable
---
# MortalCharacterManager

Provides centralized CRUD operations and state-based filtering for all mortal characters in the simulation.

## Overview

MortalCharacterManager is the state owner for all mortal characters. It provides access to character data and filtering based on corruption state, needs, and other criteria.

## Key Responsibilities

- Store and manage all mortal characters
- Provide CRUD operations for character data
- Filter characters by state (corrupted, critical needs, etc.)
- Support character queries for mission targeting

## State

| State | Type | Purpose |
|-------|------|---------|
| `_characters` | Character ID → MortalCharacterData | All mortal characters |

## Key Methods

| Method | Purpose |
|--------|---------|
| `add_character()` | Register new character |
| `get_character()` | Retrieve character by ID |
| `get_uncorrupted_characters()` | Filter for valid targets |
| `get_characters_with_critical_needs()` | Find vulnerable characters |

## Dependencies

- [[Mortal Character Data]] - Character resource type

## Filtering Queries

Common queries for game logic:
- Uncorrupted characters (valid mission targets)
- Characters with critical needs (vulnerable)
- Characters at specific corruption stages
- Characters in specific locations/groups

## Related

- [[MortalCharacterFacade]] - Public API for character access
- [[MortalCharacterService]] - Character business logic
- [[Corruption System]] - Corruption state changes
