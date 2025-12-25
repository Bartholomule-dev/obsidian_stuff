---
type: manager
domain: mission
file: DiscoveryManager.gd
status: stable
---
# DiscoveryManager

Manages the lifecycle of discovered intel, secrets, and vulnerabilities for mission targets.

## Overview

DiscoveryManager tracks intelligence gathered about mortal characters during missions. Discoveries can provide advantages in future corruption attempts.

## Key Responsibilities

- Store discoveries linked to targets
- Track discovery expiration
- Allow consumption of discoveries for bonuses
- Index discoveries for quick lookup

## State

| State | Type | Purpose |
|-------|------|---------|
| `_discoveries` | Target ID → Array[DiscoveryData] | Discoveries per target |
| `_discovery_index` | Discovery ID → DiscoveryData | Quick lookup by ID |

## Key Methods

| Method | Purpose |
|--------|---------|
| `add_discovery()` | Register new discovery for target |
| `get_active_discoveries_for_target()` | Get all valid discoveries |
| `consume_discovery()` | Use discovery for bonus |
| `expire_old_discoveries()` | Clean up stale intel |

## Dependencies

- `DiscoveryData` - Discovery resource type

## Discovery Types

Discoveries can include:
- Character vulnerabilities
- Secret information
- Behavioral patterns
- Relationship intel

## Game Loop Integration

- Discoveries found during [[Mission System|missions]]
- Used during [[Week Flow|Planning Phase]] for mission bonuses
- Expire over time if not used

## Related

- [[Mission System]] - Discovery source
- [[PlanningFacade]] - Access discoveries for planning
- [[StoryStateManager]] - Story-relevant secrets
