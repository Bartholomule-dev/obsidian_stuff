---
type: moc
domain: architecture
layer: api
status: stable
---
# Facades

The public API layer for game systems. Facades provide focused, cached access to game state and coordinate writes through managers.

## Pattern

```
UI Components & Services
         ↓ GameState.get_*_facade()
      FACADES (focused API, cached reads)
         ↓ coordinate writes
      MANAGERS (state owners, CRUD)
```

**Key Principles:**
- Cache manager references for read-bypass (fast path)
- Delegate writes to managers (slow path)
- Provide domain-specific API groupings
- Initialize via dependency injection

## All Facades

```dataview
TABLE domain, status, file
FROM "Born Below/Components"
WHERE type = "facade"
SORT domain
```

## Manual Index

| Facade | Domain | Purpose |
|--------|--------|---------|
| [[DemonManagementFacade]] | demon | Demon operations, progression, training, quests |
| [[CorruptionFacade]] | corruption | Soul essence, mission launching and tracking |
| [[CultFacade]] | cult | Cult meters, actions, weekly operations |
| [[PlanningFacade]] | planning | Weekly planning, opportunities, activities |
| [[CombatFacade]] | combat | Battle resolution, visual combat, stats |
| [[InventoryFacade]] | inventory | Items, crafting, equipment |
| [[MortalCharacterFacade]] | mortal | Character state, pressure, corruption |
| [[RealmFacade]] | realm | Realm access, entity stats, effects |
| [[StoryFacade]] | story | Story flags, narrative state |
| [[UnlockFacade]] | unlock | Unlock checks for demons, schemes, items |

## Usage

```gdscript
# Cache in _ready()
var _demon_facade = GameState.get_demon_facade()

# Use throughout class
func do_something():
    var demon = _demon_facade.get_demon(demon_id)
```
