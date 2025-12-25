---
type: service
domain: demon
file: DemonFeedbackService.gd
status: stable
---
# DemonFeedbackService

Orchestrates the "Demon Feedback Loop" by applying player choices to events and recording resulting memories.

## Overview

DemonFeedbackService bridges player decisions (praise, scold, respond to demands) with demon memory and mood systems. It ensures demons remember how they were treated.

## Key Responsibilities

- Apply player choices from feedback events
- Record feedback as demon memories
- Connect to EventSystem for event handling

## Key Methods

| Method | Purpose |
|--------|---------|
| `apply_choice()` | Process player's feedback choice |
| `initialize()` | Set up event connections |
| `_record_feedback_memory()` | Store feedback in demon memory |

## Dependencies

- [[DemonMemoryService]] - Memory storage
- [[Event System|EventSystem]] - Event handling

## Feedback Types

| Type | Effect |
|------|--------|
| Praise | Positive memory, mood boost |
| Scold | Negative memory, mood decrease |
| Grant Demand | Positive memory, loyalty increase |
| Deny Demand | Negative memory, loyalty decrease |

## Feedback Loop

1. Demon event triggers (demand, milestone, action)
2. Player presented with choices
3. Player selects response
4. DemonFeedbackService applies choice
5. Memory recorded for demon
6. Mood/loyalty updated

## Related

- [[Demon System]] - Parent system
- [[Memory System]] - Memory storage
- [[DemonMoodService]] - Mood effects
- [[Autonomous Behavior]] - Triggers feedback events
