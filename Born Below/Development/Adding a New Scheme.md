---
type: development
domain: content
status: stable
tags:
  - development
  - howto
  - scheme
---
# Adding a New Scheme

Step-by-step guide for creating a new corruption scheme in Born Below.

## Overview

Schemes are missions that deploy demons against mortal targets. Each scheme exploits a character's activities and vulnerabilities.

## Step 1: Create the Resource File

Location: `data/planning/corruption_schemes/`

```
data/planning/corruption_schemes/
├── knight/
│   ├── tournament_training.tres
│   └── your_new_scheme.tres  ← Create here
├── queen/
└── bishop/
```

## Step 2: Define Properties

Create a `.tres` file:

```gdscript
[gd_resource type="Resource" script_class="CorruptionSchemeData" load_steps=2 format=3]

[ext_resource type="Script" path="res://scripts/data/resources/planning/CorruptionSchemeData.gd" id="1"]

[resource]
script = ExtResource("1")

# Identity
id = "knight_your_scheme"
display_name = "Your Scheme Name"
description = "What the demon will do to corrupt the target."

# Target
target_id = "knight"  # knight, queen, bishop
sin_focus = "wrath"   # Primary sin exploited

# Costs
soul_essence_cost = 0
energy_cost = 20

# Beats (narrative decision points)
available_beats = ["leverage_setup", "leverage_milestone", "suspicion_complication"]

# Tags for filtering
tags = ["combat", "honor"]
```

## Step 3: Choose Sin Focus

Match the scheme's narrative to a sin:

| Sin | Scheme Themes |
|-----|---------------|
| Wrath | Violence, anger, revenge, combat |
| Envy | Jealousy, comparison, status |
| Pride | Ego, recognition, validation |
| Greed | Money, power, possessions |
| Lust | Desire, forbidden pleasure |
| Gluttony | Excess, indulgence, escape |
| Sloth | Despair, apathy, doubt |

## Step 4: Design Available Beats

Beats trigger at meter thresholds. Choose which apply:

### Leverage Beats (Progress)
- `leverage_setup` - Low threshold (20)
- `leverage_milestone` - Medium (40)
- `leverage_advantage` - High (60)
- `leverage_critical` - Max (80)

### Suspicion Beats (Risk)
- `suspicion_setup` - Low
- `suspicion_complication` - Medium
- `suspicion_defensive` - High
- `suspicion_critical` - Max

### Moral Fatigue Beats (Breaking Will)
- `fatigue_setup` - Low
- `fatigue_crack` - Medium
- `fatigue_vulnerability` - High
- `fatigue_breaking_point` - Max

## Step 5: Create Activity-Specific Beats (Optional)

For unique narrative at thresholds, create custom beats:

Location: `data/events/packs/activities/`

```json
{
  "events": [
    {
      "event_id": "activity.beat.knight_your_scheme.leverage_high",
      "event_type": "choice",
      "context": "scheme",
      "tags": ["beat", "leverage", "milestone", "activity", "knight"],
      "priority": 110,
      "content": {
        "title": "Your Beat Title",
        "description": "What's happening in the narrative...",
        "prompt": "What should your demon do?"
      },
      "roles": {
        "target": "{{target_id}}",
        "demon": "{{demon_id}}"
      },
      "choices": [
        {
          "choice_id": "bold_option",
          "label": "Bold Choice",
          "description": "High risk, high reward",
          "effects_dsl": [
            "mission.leverage += 15",
            "mission.suspicion += 10"
          ]
        },
        {
          "choice_id": "safe_option",
          "label": "Safe Choice",
          "description": "Lower risk, steady progress",
          "effects_dsl": [
            "mission.leverage += 8",
            "mission.moral_fatigue += 5"
          ]
        }
      ]
    }
  ]
}
```

## Step 6: Configure Unlock Conditions

### Option A: Available from Start

Add to starting unlocks in `UnlockableManager`.

### Option B: Corruption Stage Unlock

Schemes typically unlock as target corruption advances:

```gdscript
# In unlock logic
if target_id == "knight" and corruption_stage >= 2:
    unlock_scheme("knight_your_scheme")
```

### Option C: Story Flag Unlock

```gdscript
if story_facade.has_story_value("knight.discovered_secret"):
    unlock_scheme("knight_your_scheme")
```

## Step 7: Test the Scheme

```gdscript
# tests/unit/data/test_your_scheme.gd
extends GutTest

func test_scheme_loads():
    var scheme = load("res://data/planning/corruption_schemes/knight/your_scheme.tres")
    assert_not_null(scheme)
    assert_eq(scheme.target_id, "knight")

func test_scheme_has_valid_sin():
    var scheme = load("res://data/planning/corruption_schemes/knight/your_scheme.tres")
    var valid_sins = ["wrath", "envy", "pride", "greed", "lust", "gluttony", "sloth"]
    assert_has(valid_sins, scheme.sin_focus)

func test_scheme_has_beats():
    var scheme = load("res://data/planning/corruption_schemes/knight/your_scheme.tres")
    assert_gt(scheme.available_beats.size(), 0)
```

## Checklist

- [ ] Create `.tres` in appropriate target folder
- [ ] Set unique `id` matching folder/target pattern
- [ ] Write compelling `display_name` and `description`
- [ ] Choose appropriate `sin_focus`
- [ ] Set reasonable costs
- [ ] Select relevant `available_beats`
- [ ] (Optional) Create custom beat events
- [ ] Configure unlock conditions
- [ ] Write tests
- [ ] Playtest the mission flow

## Related

- [[Corruption Schemes]] - Existing schemes
- [[Mission Beats]] - Beat definitions
- [[Mission System]] - How schemes execute
- [[Seven Sins]] - Sin mechanics
- [[Event System]] - Beat event format
