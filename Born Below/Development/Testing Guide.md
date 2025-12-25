---
type: development
domain: testing
status: stable
tags:
  - development
  - testing
  - guide
---
# Testing Guide

Practical guide for running and writing tests in Born Below.

## Test Framework

**Primary:** GUT 9.4.0 (GdUnit4 available for scene tests)

## Running Tests

### Python Test Runner (Required)

Always use the Python runner for correct environment setup:

```bash
# All tests, condensed output
python3 run_tests.py

# Verbose output
python3 run_tests.py -v

# Unit tests only
python3 run_tests.py --dirs res://tests/unit

# Integration tests only
python3 run_tests.py --dirs res://tests/integration

# Specific subdirectory
python3 run_tests.py --dirs res://tests/unit/core/services
```

### Critical Rules

| Do | Don't |
|----|-------|
| Use `res://` paths | Use filesystem paths |
| Pass directories only | Pass file paths |
| Use valid flags only | Use `--test-script=`, `-gsuffix=` |

### Valid Arguments

- `-v`, `--verbose` - Detailed output
- `--dirs` - Test directory (res:// path)
- `--godot-bin` - Godot executable path
- `--log-level` - Logging verbosity
- `--keep-colors` - Preserve ANSI colors

## Test Organization

```
tests/
├── unit/           # Single class tests (~253 scripts)
│   ├── core/
│   │   ├── services/
│   │   ├── managers/
│   │   └── facades/
│   └── data/
├── integration/    # Cross-system tests (~73 scripts)
├── smoke/          # Critical path validation
└── helpers/        # Test utilities
```

## Writing Tests

### Basic Structure

```gdscript
extends GutTest  # Required - NOT BaseTest

const ServiceUnderTest = preload("res://scripts/core/services/MyService.gd")

var _service: ServiceUnderTest

func before_each():
    _service = ServiceUnderTest.new()

func after_each():
    _service = null

func test_something_should_do_expected_behavior():
    # Arrange
    var input = "test_value"
    
    # Act
    var result = _service.process(input)
    
    # Assert
    assert_eq(result, "expected")
```

### Using Test Helpers

#### TestDataBuilder

Create valid game resources with sensible defaults:

```gdscript
const TestDataBuilder = preload("res://tests/helpers/TestDataBuilder.gd")

func test_demon_operations():
    var demon = TestDataBuilder.demon("test_demon", true, "lesser")
    # demon has wrath:10, envy:5, all other sins populated
    
    var character = TestDataBuilder.character("test_char", true)
    # character has all 7 needs at 50
    
    var near_breaking = TestDataBuilder.mortal_character_near_breaking("pride")
    # character with 4 desperate behaviors, pride at 35
```

#### MemoryTestHelper

Test demon memory and loyalty systems:

```gdscript
const MemoryTestHelper = preload("res://tests/helpers/MemoryTestHelper.gd")

func test_memory_effects():
    var demon_id = MemoryTestHelper._create_basic_test_demon(_roster_manager)
    
    # Create demon with specific memory history
    var memories = [
        {"type": "praised", "week": 1, "intensity": 1.5},
        {"type": "punished", "week": 2, "intensity": 1.0}
    ]
    var demon = MemoryTestHelper.create_demon_with_memories(demon_id, memories)
    
    # Assert memory exists
    MemoryTestHelper.assert_memory_exists(self, demon.memories, "praised")
    
    # Check loyalty change
    var loyalty_delta = MemoryTestHelper.get_total_loyalty_change(demon.memories)
```

#### TestHelpers

Inject test data into managers:

```gdscript
const TestHelpers = preload("res://tests/helpers/TestHelpers.gd")

func test_roster_operations():
    var demon = TestDataBuilder.demon("test_demon", true)
    TestHelpers.inject_demon_into_roster(_roster_manager, demon)
    
    # Demon is now in roster with progression state initialized
    var retrieved = _roster_manager.get_demon("test_demon")
    assert_not_null(retrieved)
```

### Mock Objects

#### MockGameState

Lightweight GameState replacement:

```gdscript
var _mock_state = MockGameState.new()

func before_each():
    # Configure mock with test data
    _mock_state.add_character(TestDataBuilder.character("knight"))
    _service.initialize({"game_state": _mock_state})
```

#### MockCultFacade

Test cult-dependent logic:

```gdscript
var _mock_cult = MockCultFacade.new()

func before_each():
    _mock_cult.set_meter("size", 50)
    _mock_cult.set_meter("fervor", 70)
```

#### TestResourceTransactionManager

Functional validation mock for purchases:

```gdscript
var _transaction_manager = TestResourceTransactionManager.new()
_transaction_manager.initialize(_corruption_facade)

# Performs real soul essence checks
# Executes callbacks on success
# Handles refunds on failure
```

## Test Patterns

### GDScript Type Safety

Always initialize all demon stats:

```gdscript
# Services expect complete stat dictionaries
var demon = TestDataBuilder.demon("test")  # All 7 sins populated
```

### Private Access Pattern

Tests may access private fields for setup (not for production):

```gdscript
# Acceptable in tests for injection
_roster_manager._demon_entity_manager.add(demon)
```

### End-to-End Simulation

Skip early stages to test late-game logic:

```gdscript
var character = TestDataBuilder.mortal_character_near_breaking("greed")
# Now test breaking point logic directly
```

## Related

- [[Testing Patterns]] - Detailed patterns (agent-context)
- [[Demon System]] - What to test
- [[Mission System]] - Integration test targets
