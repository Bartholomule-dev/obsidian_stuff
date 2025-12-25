---
type: moc
domain: architecture
layer: state
status: stable
---
# Managers

State owners that provide CRUD operations on game data. Managers own the authoritative state and are accessed through facades.

## Pattern

Managers own state → Services orchestrate → Facades provide access

**Key Principles:**
- Own and persist state (Dictionaries, Resources)
- Provide CRUD operations
- Emit signals through EventBus on state changes
- Initialized in GameStateInitializer Phase 1-2

## All Managers

```dataview
TABLE domain, status, file
FROM "Born Below/Components"
WHERE type = "manager"
SORT domain
```

## By Domain

### Demon Domain
- RosterManager - Demon roster, entity storage
- DemonManager - Demon state, progression, services
- DemonProgressionManager - Level, XP tracking
- DemonSlotManager - Slot assignments
- DemonTrainingManager - Training state
- DemonCooldownManager - Cooldown tracking
- DemonEntityManager - Entity data

### Planning Domain
- PlanningPhaseManager - Weekly plan, content registries
- QuestManager - Quest state, assignments

### Economy Domain
- InventoryManager - Items, inventories
- EquipmentManager - Equipment state
- CraftingManager - Crafting recipes
- ResourceTransactionManager - Resource flow

### World Domain
- MortalCharacterManager - Character data
- StoryStateManager - Story flags
- UnlockableManager - Unlock state
- WorldEventManager - World event rotation
- RealmCoordinator - Realm initialization

### Other
- CultManager - Cult state, meters
- DiscoveryManager - Exploration discoveries
- PersistenceManager - Save/load
