---
type: development
domain: content
status: stable
tags:
  - development
  - howto
  - demon
---
# Adding a New Demon

Step-by-step guide for creating a new demon in Born Below.

## Overview

Demons are defined as `.tres` resource files with stats, personality, and identity information.

## Step 1: Create the Resource File

Location: `data/demons/`

```
data/demons/
├── blood_drainer.tres
├── night_terror.tres
├── your_new_demon.tres  ← Create here
└── ...
```

## Step 2: Define Properties

Create a new `.tres` file with:

```gdscript
[gd_resource type="Resource" script_class="DemonData" load_steps=2 format=3]

[ext_resource type="Script" path="res://scripts/data/resources/DemonData.gd" id="1"]

[resource]
script = ExtResource("1")

# Identity
id = "your_demon_id"
display_name = "Your Demon Name"
demon_rank = 0  # 0=Lesser, 1=Greater, 2=Archdemon

# Personality
personality_archetype = "cunning"  # aggressive, analytical, arrogant, cunning, sadistic, zealous

# Stats (Seven Sins) - typically 1-100
wrath = 15
envy = 30
pride = 25
greed = 45
lust = 20
gluttony = 35
sloth = 10

# Starting state
happiness = 70
energy = 100
stress = 0
loyalty = 0
level = 1
xp = 0
```

## Step 3: Choose Stats Strategically

Match demon specialty to target vulnerabilities:

| Target | Vulnerable Sins | Recommended High Stats |
|--------|-----------------|----------------------|
| Knight | Pride, Wrath, Lust | Wrath, Pride |
| Queen | Pride, Envy, Lust | Envy, Lust |
| Bishop | Greed, Pride, Gluttony | Greed, Gluttony |

### Stat Guidelines

- **Primary stat**: 60-80 (demon's specialty)
- **Secondary stat**: 30-50 (backup option)
- **Other stats**: 10-25 (minimal)
- **Total**: Keep balanced with existing demons

## Step 4: Choose Personality

Archetypes affect autonomous behavior:

| Archetype | Behavior | Good For |
|-----------|----------|----------|
| Aggressive | Push hard, high damage | Fast corruption |
| Analytical | Calculated, consistent | Safe progress |
| Arrogant | Ego-driven, pride-focused | Pride targets |
| Cunning | Subtle, deceptive | Low suspicion |
| Sadistic | Enjoys suffering | Moral fatigue |
| Zealous | Devoted, extreme | All-or-nothing |

## Step 5: Register for Unlocking

Add unlock conditions in the unlockable system:

### Option A: Available from Start

In `UnlockableManager` initialization:
```gdscript
_unlocked_demons["your_demon_id"] = true
```

### Option B: Story Unlock

Add to story progression triggers:
```gdscript
# In event effects or story milestones
GameState.get_unlock_facade().unlock_demon("your_demon_id")
```

### Option C: Corruption Stage Unlock

Connect to character corruption:
```gdscript
# In UnlockableManager._on_character_corrupted
if character_id == "knight" and stage >= 2:
    unlock_demon("your_demon_id")
```

## Step 6: Test the Demon

Create a test file:

```gdscript
# tests/unit/data/test_your_demon.gd
extends GutTest

func test_demon_loads_correctly():
    var demon = load("res://data/demons/your_demon.tres")
    assert_not_null(demon)
    assert_eq(demon.id, "your_demon_id")
    assert_gt(demon.wrath + demon.envy + demon.pride, 0)

func test_demon_has_valid_archetype():
    var demon = load("res://data/demons/your_demon.tres")
    var valid = ["aggressive", "analytical", "arrogant", "cunning", "sadistic", "zealous"]
    assert_has(valid, demon.personality_archetype)
```

## Checklist

- [ ] Create `.tres` file in `data/demons/`
- [ ] Set unique `id` and `display_name`
- [ ] Choose appropriate `demon_rank`
- [ ] Set stats with clear specialty
- [ ] Choose fitting `personality_archetype`
- [ ] Configure unlock condition
- [ ] Write basic test
- [ ] Test in-game recruitment

## Related

- [[DemonData]] - Data structure details
- [[Demon System]] - How demons work
- [[Personality Evolution]] - Archetype effects
- [[Seven Sins]] - Stat meanings
- [[Starting Demons]] - Existing demon roster
