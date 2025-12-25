---
type: system
domain: ui
status: stable
---
# Modals

Full-screen or overlay interfaces that capture focus for specific interactions.

## Modal Manager

`ModalManager` handles modal lifecycle:
- Opening/closing with transitions
- Modal stacking
- Focus management
- Input blocking

## Core Modals

### Planning Modals

| Modal | Purpose |
|-------|---------|
| **UnifiedAssignmentModal** | Assign demons to any activity type |
| **DemonSelectionModal** | Select demon from filtered roster |

### Event Modals

| Modal | Purpose |
|-------|---------|
| **ChoiceEventModal** | Generic player choices (demands, events) |
| **NotificationModal** | Milestones, unlocks, warnings |
| **DialogueBox** | Narrative progression, story events |
| **BeatDecisionModal** | Mid-mission decisions |

### Information Modals

| Modal | Purpose |
|-------|---------|
| **CodexModal** | Game reference, lore, history |
| **MortalCharacterDetailModal** | Character deep-dive |
| **CultManagementModal** | Cult status and actions |

### Summary Modals

| Modal | Purpose |
|-------|---------|
| **EndOfWeekSummaryModal** | Week results compilation |

## Modal Patterns

### Opening

```gdscript
ModalManager.open_modal("choice_event", {
    event_data = event,
    choices = choices
})
```

### Closing with Result

```gdscript
# In modal
ModalManager.close_modal(result_data)

# Caller receives via signal
ModalManager.modal_closed.connect(_on_modal_closed)
```

## Modal Categories

| Category | Blocks Input | Has Backdrop |
|----------|-------------|--------------|
| Critical | Yes | Dark |
| Standard | Yes | Semi |
| Toast | No | None |

## Related

- [[UI System]] - Parent system
- [[Week Flow]] - When modals appear
- [[Event System]] - Event modal triggers
