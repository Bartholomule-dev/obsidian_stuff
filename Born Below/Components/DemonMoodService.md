---
type: service
domain: demon
file: DemonMoodService.gd
status: stable
---
# DemonMoodService

Orchestrates short-term emotional and physical state of demons, including happiness, energy, stress, and burnout.

## Purpose

Manages the immediate wellbeing of demons that affects their weekly performance.

## Key Responsibilities

- Tracks happiness and stress levels with performance modifiers
- Manages energy costs for activities and recovery during rest
- Calculates burnout risk from accumulated stress and overwork
- Processes end-of-week updates including natural stress decay

## Key Methods

| Method | Purpose |
|--------|---------|
| `update_happiness(demon_id, event_type, context)` | Modify happiness |
| `update_stress(demon_id, event_type, context)` | Modify stress |
| `spend_energy(demon_id, activity_type)` | Deduct activity energy |
| `get_stress_performance_modifier(demon_id)` | Performance impact |
| `process_weekly_mood_updates(demon_id)` | End-of-week processing |
| `apply_overwork_penalty(demon_id)` | Burnout check |

## Stress Levels

| Level | Stress | Performance |
|-------|--------|-------------|
| Peak | 0-25 | 100% |
| Fatigued | 26-50 | 90% |
| Exhausted | 51-75 | 75% |
| Burnout | 76-100 | Cannot work |

## Energy System

- Activities cost energy
- Rest recovers energy
- Low energy increases stress
- Zero energy forces rest

## Related

- [[Demon System]] - System overview
- [[DemonManager]] - Parent coordinator
- [[Autonomous Behavior]] - Mood affects demands
