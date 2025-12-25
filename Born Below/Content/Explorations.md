---
type: content
domain: exploration
status: stable
---
# Explorations

Procedural node-based dungeon exploration. Each domain provides intel and discoveries about corruption targets.

## Target Domains

### Royal Court (Queen)
The palace halls, secret passages, and political chambers.

| Tier | Requirement | Nodes | Turns |
|------|-------------|-------|-------|
| Scout | Innocent | 6-10 | 4 |
| Recon | Tempted | 10-14 | 6 |
| Expedition | Falling | 16-22 | 10 |

**Discoveries**: Affairs, political schemes, poisoners, illegitimate heirs

### Martial Quarter (Knight)
Barracks, taverns, training grounds, and tournament arenas.

| Tier | Requirement | Nodes | Turns |
|------|-------------|-------|-------|
| Scout | Innocent | 6-10 | 4 |
| Recon | Tempted | 10-14 | 6 |
| Expedition | Falling | 16-22 | 10 |

**Discoveries**: Gambling debts, secret lovers, dishonorable past

### Sacred District (Bishop)
Cathedrals, crypts, catacombs, and secret archives.

| Tier | Requirement | Nodes | Turns |
|------|-------------|-------|-------|
| Scout | Innocent | 6-10 | 4 |
| Recon | Tempted | 10-14 | 6 |
| Expedition | Falling | 16-22 | 10 |

**Discoveries**: Hidden wealth, crises of faith, forbidden knowledge

---

## Resource Domains

### The Outskirts
Frontier wilderness for reliable soul essence yields.
- No intel value
- General resource gathering

### Hell's Periphery
Infernal borderlands with demonic aesthetics.
- Node flavors: Sulfur Vents, Charred Woods, Demon Burrows
- Demonic encounters

---

## Node Types

| Node | Effect |
|------|--------|
| **Battle** | Combat encounter |
| **Campfire** | Recovery point |
| **Soul Harvest** | Resource collection |
| **Item Find** | Equipment discovery |
| **Hazard Trap** | Risk/reward challenge |
| **Mystery** | Random buff/discovery |
| **Boss** | Major encounter |

## Exploration Flow

1. Assign demon during [[Week Flow|Planning Phase]]
2. Pay Soul Essence + Energy cost
3. Traverse procedural node map
4. Process encounters at each node
5. Collect discoveries and resources
6. Finalize at week end

## Related

- [[ExplorationService]] - Core logic
- [[ExplorationCoordinator]] - Coordination
- [[Exploration System]] - System overview
- [[Corruption Schemes]] - Uses discoveries
- [[DiscoveryManager]] - Discovery storage
