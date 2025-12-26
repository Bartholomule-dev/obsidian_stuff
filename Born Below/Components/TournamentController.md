---
type: controller
domain: combat
file: TournamentController.gd
status: stable
---
# TournamentController

Orchestrates tournament gauntlet execution with visual combat and narrative beats.

## Overview

TournamentController manages the runtime experience of a tournament: running consecutive visual battles, tracking HP across rounds, applying between-round healing, and logging narrative events.

**File:** `scripts/core/services/TournamentController.gd`

## Key Responsibilities

- Run consecutive visual combat rounds
- Track demon HP across rounds (damage persists)
- Apply 20% heal between victories
- Scale enemy difficulty per tournament settings
- Log narrative beats to ActivityLog
- Handle early defeat (tournament ends)
- Return completion results to caller

## Usage

Called by [[VisualsCoordinator]] during week execution:

```gdscript
var controller = TournamentController.new()
controller.initialize({
    "combat_facade": combat_facade,
    "tournament_service": tournament_service,
    "game_state": game_state
})
var result = await controller.present_tournament(demon_id, tournament)
```

## Main Method

### `present_tournament(demon_id, tournament) -> Dictionary`

Async method that runs the full gauntlet:

1. **Show intro** - Tournament name, flavor text, round count
2. **Gauntlet loop** (for each round):
   - Get enemy from `enemy_pool[round_index]`
   - Show round intro (matchup announcement)
   - Run visual combat via [[CombatFacade]]
   - If victory: award per-round XP, heal 20%, continue
   - If defeat: show defeat message, break loop
3. **Completion** - Call [[TournamentService]].`complete_tournament()`
4. **Return** result dictionary

## HP Management

```gdscript
# Initial HP from demon stats
var demon_max_hp = _combat_facade.calculate_demon_combat_hp(demon_id)
var demon_current_hp = demon_max_hp

# After each victory (except final round)
var heal_amount = int(demon_max_hp * 0.2)
demon_current_hp = min(demon_max_hp, demon_current_hp + heal_amount)

# HP passed to combat for carry-over
var outcome = await _combat_facade.present_visual_combat(
    demon_id, enemy_data, null, 
    demon_current_hp,           # Carried HP
    tournament.difficulty_scaling  # Enemy stat multiplier
)
```

## Narrative Logging

Uses [[EventSystem]].`log_activity()` for ActivityLog entries:

| Template Key | When | Data |
|--------------|------|------|
| `tournament_enter` | Start | demon_name, tournament_name |
| `tournament_flavor` | Start | flavor_text |
| `tournament_battles_await` | Start | rounds |
| `tournament_round` | Each round | round_number, total_rounds |
| `tournament_round_matchup` | Each round | demon_name, enemy_name |
| `tournament_round_victory` | After win | round_number, soul_reward, xp_reward |
| `tournament_heal` | After win | demon_name, heal_amount |
| `tournament_complete` | All rounds won | - |
| `tournament_victory` | All rounds won | demon_name |
| `tournament_bonus` | All rounds won | soul_reward, xp_reward |
| `tournament_defeat` | Loss | round_number |
| `tournament_defeat_flavor` | Loss | demon_name |

## Dependencies

| Dependency | Purpose |
|------------|---------|
| [[CombatFacade]] | Visual combat presentation |
| [[TournamentService]] | Reward distribution |
| [[GameState]] | Demon data access |
| [[EventSystem]] | ActivityLog entries |

## Return Value

```gdscript
{
    "tournament_id": "pit_fighters_trial",
    "tournament_name": "Pit Fighter's Trial",
    "rounds_won": 3,
    "total_rounds": 3,
    "completed": true,
    "soul_gained": 0,
    "xp_gained": 135,
    "stat_rewards": {"wrath": 2, "pride": 1},
    "items_awarded": []
}
```

## Related

- [[TournamentService]] - Assignment and rewards
- [[Tournament System]] - System overview
- [[CombatFacade]] - Visual combat API
- [[CombatSessionService]] - Combat viewport management
