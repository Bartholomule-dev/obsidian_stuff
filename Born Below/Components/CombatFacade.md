---
type: facade
domain: combat
file: CombatFacade.gd
status: stable
---
# CombatFacade

Unified interface for combat operations.

## Purpose

Provides API for instant battles, visual combat, stat calculation, and outcome application.

## Dependencies

- [[EncounterResolutionService]] - Instant stat-based battles
- [[CombatResolutionService]] - Multi-turn simulation
- [[RewardDistributionService]] - Rewards and penalties
- [[CombatSessionService]] - Visual combat lifecycle
- [[RosterManager]] - Demon data

## Key Responsibilities

### Instant Battle
- `calculate_battle_success_rate(demon_id, difficulty, stat)` - Success chance

### Visual Combat
- `resolve_visual_combat(demon_id, enemy_data)` - Backend calculation
- `present_visual_combat(demon_id, enemy_data)` - Full visual sequence

### Combat Stats
- `get_effective_combat_stats(demon_id)` - Base + bonuses
- `calculate_demon_combat_hp(demon_id)` - Max HP (60-150)

### Outcome Application
- `apply_combat_outcome(outcome)` - Process rewards/penalties
- `apply_failure_penalties(demon_id, stress, energy)` - Defeat penalties

## Combat Modes

| Mode | Use Case | Visual |
|------|----------|--------|
| Instant | Quick encounters | No |
| Visual | Interactive battles | Yes |

## Visual Combat Flow

1. `present_visual_combat()` called
2. CombatSessionService manages viewport
3. Turn-by-turn resolution with animation
4. `CombatOutcomeEvent` returned
5. Rewards/penalties applied

## Related

- [[Combat System]] - System overview
- [[CombatResolutionService]] - Multi-turn logic
- [[TournamentService]] - Tournament integration
