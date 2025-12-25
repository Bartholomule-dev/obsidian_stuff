---
type: concept
domain: mortal
status: stable
---
# Character Defenses

Mortal characters actively resist corruption through AI-driven defenses that activate based on awareness and need state.

## Defense Types

| Defense | Trigger | Effect | Duration |
|---------|---------|--------|----------|
| **Seek Allies** | Awareness ≥ 51 (Alert) | "Protected" status blocks some schemes | Until awareness drops |
| **Fortify Weakness** | Lowest need < 40 | +10/week recovery to that need | Until need > 50 |
| **Change Routine** | 3+ schemes of same sin | Blocks that sin type | 2 weeks |
| **Divine Prayer** | Awareness ≥ 76 (Vigilant) | +3 intervention risk | Permanent accumulation |

## Character-Specific Modifiers

| Character | Defense Modifier |
|-----------|-----------------|
| Knight | Protected blocks Lust/Desire schemes |
| Queen | Protected blocks solo-target schemes |
| Bishop | Prayer effect doubled (+6 risk) |

## Defense Data

Stored in `MortalCharacterData`:
- `active_defenses: Array[String]` - Currently active
- `blocked_sin_types: Dictionary` - Sins blocked by Change Routine
- `blocked_sin_durations: Dictionary` - Weeks remaining per block
- `scheme_sin_history: Dictionary` - Tracks patterns for Change Routine

## Processing

`CharacterDefenseService` processes defenses weekly:

```gdscript
# Check if character can be targeted
if not CharacterDefenseService.can_target_character(char_id, sin_type):
    return false  # Blocked by defense

# Weekly processing
CharacterDefenseService.process_weekly_defenses()
```

## Strategy Implications

- **Vary sin types:** Avoid triggering Change Routine
- **Work slowly:** High awareness activates multiple defenses
- **Target weakness:** Low needs may have Fortify, making them harder
- **Watch Bishop:** Prayer accumulation is permanent

## Related

- [[Corruption System]] - Parent system
- [[Awareness System]] - Triggers defenses
- [[Intervention Risk]] - Prayer affects risk
