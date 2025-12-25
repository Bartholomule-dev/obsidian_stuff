---
type: service
domain: demon
file: AutonomousBehaviorService.gd
status: stable
---
# AutonomousBehaviorService

Manages independent demon actions driven by personality and emotional state, applying mechanical consequences and generating narrative events to simulate autonomous agency.

## Overview

AutonomousBehaviorService gives demons independent agency. Based on personality, stress, and loyalty, demons may take autonomous actions during the planning phase - demanding assignments, stealing resources, or helping others.

## Key Responsibilities

- Evaluate all demons for autonomous action triggers
- Calculate action probability from personality/mood
- Execute mechanical effects of autonomous actions
- Generate narrative events for player feedback
- Manage action cooldowns

## Key Methods

| Method | Purpose |
|--------|---------|
| `check_all_demons_for_autonomous_actions()` | Evaluate all slotted demons |
| `evaluate_action_probability()` | Calculate trigger odds |
| `_execute_autonomous_action()` | Dispatch to action handlers |
| `_process_template_resolution()` | Apply effects via EventSystem |
| `process_weekly_cooldowns()` | Prevent repetitive behaviors |

## Triggers

Probability influenced by:
- **Personality archetype** - Different archetypes favor different actions
- **Stress level** - High stress increases disruptive acts
- **Loyalty** - Affects helpful vs harmful frequency
- **Context** - Consecutive weeks worked, recent events

## Action Categories

### Prideful/Fanatical
- Demand prestigious assignments
- Crusade demands
- Energy sacrifice for "the cause"

### Cruel/Deceitful
- Torment weaker demons (lower happiness)
- Steal Soul Essence
- Fake mission progress

### Obsessive/Slothful
- Overwork in training (XP boost)
- Perfectionist meltdowns
- Refuse assignments to rest

## Integration

Actions processed through:
1. Probability roll during planning phase
2. Mechanical effects applied
3. Event generated via [[Event System|EventSystem]]
4. UI notification/activity log entry
5. Cooldown applied

## Related

- [[Autonomous Behavior]] - Concept overview
- [[Personality Evolution]] - Personality affects actions
- [[DemonMoodService]] - Stress/loyalty factors
- [[Event System]] - Event generation
