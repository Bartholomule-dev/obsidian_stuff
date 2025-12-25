---
type: development
domain: patterns
status: stable
tags:
  - development
  - patterns
  - code
---
# Common Patterns

Code patterns and idioms used throughout Born Below.

## Architecture Patterns

### Facade Pattern

Facades provide focused API access with read-bypass optimization:

```gdscript
# In your class
var _demon_facade: DemonManagementFacade

func _ready():
    _demon_facade = GameState.get_demon_facade()

func do_something():
    var demon = _demon_facade.get_demon(demon_id)
```

### Dependency Injection

Services receive dependencies through `initialize()`:

```gdscript
class_name MyService extends RefCounted

var _roster_manager: RosterManager
var _planning_manager: PlanningManager

func initialize(dependencies: Dictionary) -> void:
    _roster_manager = dependencies.roster_manager
    _planning_manager = dependencies.planning_manager
```

### Event Bus Pattern

All signals go through EventBus:

```gdscript
# State changes (with history)
EventBus.publish_demon_retired(demon_id, career_summary)

# UI events (fire-and-forget)
EventBus.toast_requested.emit("Mission complete!", "success")
```

## GDScript Type Safety

### The Untyped Storage / Typed Returns Pattern

Storage uses untyped containers (loader compatible), returns are typed:

```gdscript
# Storage - UNTYPED
var _items: Dictionary = {}

# Returns - TYPED
func get_items() -> Dictionary[String, ItemData]:
    var typed: Dictionary[String, ItemData] = {}
    for key in _items:
        typed[key] = _items[key]
    return typed
```

Or use TypingUtils:

```gdscript
func get_demons() -> Dictionary[String, DemonData]:
    var typed: Dictionary[String, DemonData] = {}
    return TypingUtils.to_typed_dict(_demons, typed)
```

### Resource Property Access

Always use direct property access on resources:

```gdscript
# Correct
var name = demon.display_name
var wrath = demon.wrath

# Wrong - don't use dictionary access on resources
var name = demon.get("display_name", "")  # Don't do this
```

### Typed RefCounted Classes

Don't call `.get()` or `.has()` on typed RefCounted:

```gdscript
# Correct
var damage = combat_outcome.damage_dealt

# Wrong - causes runtime errors
var damage = combat_outcome.get("damage_dealt", 0)
```

## Signal Patterns

### State Change Signals

Use past-tense verbs, publish through EventBus:

```gdscript
# In your service
EventBus.publish_corruption_change(character_id, old_stage, new_stage)

# Listener
func _ready():
    EventBus.corruption_changed.connect(_on_corruption_changed)
```

### UI Command Signals

Use `*_requested` or `*_selected` suffixes:

```gdscript
# Emit directly
EventBus.scheme_ui_selected.emit(scheme_id)
EventBus.modal_close_requested.emit()
```

## Resource Loading

### Preload at Top Level

```gdscript
const DemonData = preload("res://scripts/data/resources/DemonData.gd")
const MissionStateData = preload("res://scripts/data/resources/planning/MissionStateData.gd")
```

### Load at Runtime

```gdscript
func _load_demon(demon_id: String) -> DemonData:
    var path = "res://data/demons/%s.tres" % demon_id
    return load(path) as DemonData
```

## Error Handling

### Null Checks

```gdscript
func get_demon_name(demon_id: String) -> String:
    var demon = _roster_manager.get_demon(demon_id)
    if not demon:
        push_warning("Demon not found: %s" % demon_id)
        return "Unknown"
    return demon.display_name
```

### Guard Clauses

```gdscript
func process_mission(mission_id: String) -> void:
    var state = _get_mission_state(mission_id)
    if not state:
        return
    
    if state.is_completed:
        return
    
    # Main logic here
```

## Collection Patterns

### Safe Dictionary Access

```gdscript
# With default
var value = dict.get("key", default_value)

# Check first
if dict.has("key"):
    process(dict["key"])
```

### Array Filtering

```gdscript
func get_available_demons() -> Array[DemonData]:
    var result: Array[DemonData] = []
    for demon in _all_demons:
        if demon.is_available and not demon.is_on_mission:
            result.append(demon)
    return result
```

## Testing Patterns

### Arrange-Act-Assert

```gdscript
func test_demon_gains_xp():
    # Arrange
    var demon = TestDataBuilder.demon("test", true)
    TestHelpers.inject_demon_into_roster(_roster, demon)
    
    # Act
    _progression_service.award_xp("test", 100, "mission", "wrath")
    
    # Assert
    var updated = _roster.get_demon("test")
    assert_eq(updated.xp, 100)
```

### Test Isolation

```gdscript
func before_each():
    _service = MyService.new()
    _mock_manager = MockManager.new()
    _service.initialize({"manager": _mock_manager})

func after_each():
    _service = null
    _mock_manager = null
```

## Related

- [[Facades]] - Facade pattern details
- [[Architecture/Services]] - Service patterns
- [[Testing Guide]] - Test patterns
- [[Data Resources]] - Resource handling
