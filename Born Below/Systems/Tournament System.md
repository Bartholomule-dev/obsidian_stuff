---
type: system
domain: combat
status: stable
---
# Tournament System

Multi-round combat gauntlets where demons fight through increasingly difficult opponents.

## Overview

**Service:** `TournamentService`, `TournamentController`
**Data:** `data/planning/tournaments/`

## Key Features

- **Multi-Round Gauntlets:** 3-5 sequential battles
- **HP Carry-Over:** Damage persists between rounds
- **Difficulty Scaling:** Each round tougher than the last
- **Entry Costs:** Some tournaments require soul essence
- **Progressive Rewards:** Rewards per round + victory bonus

## Tournament Structure

```gdscript
{
    "id": "arena_of_fury",
    "name": "Arena of Fury",
    "rounds": [
        {"enemy_id": "gladiator_imp", "difficulty": 1},
        {"enemy_id": "champion_fury", "difficulty": 3},
        {"enemy_id": "arena_master", "difficulty": 5}
    ],
    "entry_cost": {"soul_essence": 50},
    "rewards": {
        "victory": {"xp": 200, "stat_boost": {"wrath": 3}},
        "per_round": {"soul_essence": 25}
    }
}
```

## Flow

```
Entry → Round 1 → Round 2 → ... → Final Round → Rewards
  ↓        ↓          ↓              ↓            ↓
Pay fee  Fight    HP carries     Boss fight   XP + Items
```

## Weekly Activity

Tournament counts as demon's weekly activity:
- Mutually exclusive with scheme/quest/training/exploration
- Validated during assignment

## Signals

```gdscript
tournament_assigned.emit({demon_id, tournament_id})
tournament_completed.emit({demon_id, tournament_id, rounds_won, rewards})
```

## Related

- [[Combat System]] - Battle resolution
- [[Demon System]] - Tournament participants
- [[Economy System]] - Entry costs and rewards
