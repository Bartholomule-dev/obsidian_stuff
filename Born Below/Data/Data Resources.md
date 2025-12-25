---
type: moc
domain: data
status: stable
---
# Data Resources

Game content is defined in `.tres` resource files with corresponding GDScript classes.

## Resource Categories

### Demons
**Location:** `data/demons/`

| Class | Purpose |
|-------|---------|
| **DemonData** | Demon attributes, rank, personality, stats, soul cost |

### Mortal Characters
**Location:** `data/mortal_characters/`

| Class | Purpose |
|-------|---------|
| **MortalCharacterData** | Character needs, awareness, corruption state, vulnerabilities |
| **CorruptionBenefitData** | Rewards for corrupting specific characters |

### Activities
**Location:** `data/activities/`, `data/planning/`

| Class | Purpose |
|-------|---------|
| **TrainingActivityData** | Multi-week stat improvement activities |
| **WeeklyActivityData** | Single-week maintenance (rest, recreation) |
| **DemonQuestData** | Personal demon quests with rewards |

### Planning
**Location:** `data/planning/`

| Class | Purpose |
|-------|---------|
| **OpportunityCardData** | Mission opportunity templates |
| **MissionStateData** | Runtime mission state (meters, progress) |

### Items
**Location:** `data/items/`, `data/infernal_items/`

| Class | Purpose |
|-------|---------|
| **ItemData** | Mortal realm items |
| **InfernalItemData** | Demonic equipment, materials |

### Combat
**Location:** `data/enemies/`

| Class | Purpose |
|-------|---------|
| **EnemyData** | Enemy stats, visuals, rewards |

### Events
**Location:** `data/events/packs/`

| Class | Purpose |
|-------|---------|
| **GameEvent** | Event structure (choices, effects, conditions) |
| **EventChoice** | Individual choice within event |

### Configuration
**Location:** `data/config/`

| Class | Purpose |
|-------|---------|
| **GameConfig** | Global balance, timing, limits |

## Resource Pattern

```gdscript
# Resource class definition
class_name DemonData extends Resource

@export var demon_rank: String = "lesser"
@export var personality_archetype: String = "aggressive"
@export var soul_cost: int = 100
```

## Content Creation

1. Create `.tres` file in appropriate directory
2. Set resource type to matching class
3. Fill exported properties
4. Resource auto-loads via managers

## Related

- [[Event System]] - Event JSON packs
- [[DemonManagementFacade]] - Demon data access
- [[InventoryFacade]] - Item data access
