---
type: content
domain: events
status: stable
tags:
  - content
  - events
  - catalog
---
# Event Packs

Complete catalog of event packs in Born Below. Events drive narrative progression and player choices.

## Overview

Events are stored in `data/events/packs/` as JSON files organized by domain.

| Pack | Events | Purpose |
|------|--------|---------|
| activities | 22 | Character-specific mission beats |
| cult | 14 | Cult action outcomes and situations |
| mission | 5 | Generic mission meter beats |
| infernal | 27 | Demon personality and corruption events |
| divine | 9 | Divine intervention events |
| intervention | 8 | Suspicion/judgment escalation |
| demo | 1 | Demo-specific events |
| interrupt | 1 | High-priority interrupts |

**Total: 87 events**

---

## Activities Pack

**Path:** `data/events/packs/activities/`
**Context:** `scheme`
**Events:** 22

Character-specific narrative beats during missions.

### Knight Activities
- `bishop_crisis_of_faith` - Faith doubt moments
- `knight_drowning_sorrows` - Tavern despair
- `knight_guarding_queen` - Forbidden devotion
- `knight_investigating_threats` - Paranoia spirals
- `knight_leading_men` - Command guilt
- `knight_proving_himself` - Glory seeking
- `knight_tournament_training` - Combat rivalry

### Queen Activities
- `queen_court_intrigue` - Political maneuvering
- `queen_meeting_suitors` - Marriage politics
- `queen_royal_celebration` - Revelry exploitation
- `queen_secret_correspondence` - Treasonous letters
- `queen_securing_alliances` - Power deals
- `queen_tightening_grip` - Control obsession

### Bishop Activities
- `bishop_fasting_penance` - Divine visions
- `bishop_hearing_confessions` - Secret harvesting
- `bishop_leading_holy_rites` - Faith spectacle
- `bishop_private_devotions` - Doubt seeds
- `bishop_rooting_out_heresy` - Persecution zeal

### Sample Event Structure

```json
{
  "event_id": "activity.beat.knight_tournament_training.leverage_high",
  "event_type": "choice",
  "context": "scheme",
  "tags": ["beat", "leverage", "milestone", "activity", "knight"],
  "priority": 110,
  "content": {
    "title": "Rival's Edge",
    "description": "The knight's rival has discovered a weakness...",
    "prompt": "How should your demon exploit this?"
  },
  "choices": [
    {
      "choice_id": "stoke_rivalry",
      "label": "Stoke Rivalry",
      "effects_dsl": ["mission.leverage += 12", "mission.suspicion += 5"]
    }
  ]
}
```

---

## Cult Pack

**Path:** `data/events/packs/cult/`
**Context:** `weekly` / `end_of_week`
**Events:** 14

Cult action outcomes and situation events.

### Action Outcomes
- `cultist_fervor` - Preach success
- `merchant_prosperity` - Fundraise success
- `shadow_network` - Cover up success
- `underground_success` - Recruit success
- `unified_faithful` - Punish success
- `zealot_fervor` - High fervor outcomes

### Situation Events
Triggered based on cult identity:

| Event | Identity | Trigger |
|-------|----------|---------|
| `situation_zealot` | Zealot | Fervor dominant |
| `situation_shadow` | Shadow | Secrecy dominant |
| `situation_merchant` | Merchant | Size dominant |
| `situation_strife` | Any | High dissent |
| `situation_pressure` | Any | High heat |
| `situation_opportunity` | Any | Balanced meters |

---

## Mission Pack

**Path:** `data/events/packs/mission/`
**Context:** `scheme`
**Events:** 5

Generic meter-based beats (not character-specific).

| Event | Meter | Purpose |
|-------|-------|---------|
| `beat_leverage` | Leverage | Progress milestones |
| `beat_suspicion` | Suspicion | Risk management |
| `beat_moral_fatigue` | Moral Fatigue | Will erosion |
| `mission_completion` | Leverage 80+ | Finisher options |

---

## Infernal Pack

**Path:** `data/events/packs/infernal/`
**Context:** Various
**Events:** 27 (across subfolders)

Demon and corruption narrative events.

### Subfolders

**corruption/** (2 events)
- `desperate_actions` - Mortal desperation narratives
- `signature_ripples` - Corruption cascade effects

**demon/** (2 events)
- `burnout_recovery` - Stress recovery narratives
- `scheme_reactions` - Demon feedback on missions

**personality_mutations/** (12 events)
Archetype evolution events:
- `aggressive → tyrannical`
- `analytical → obsessive`
- `arrogant → narcissistic`
- `cunning → manipulative`
- `zealous → fanatical`
- And further mutations...

**rest_drift/** (8 events)
Personality drift during rest:
- `cruelty_score_early/notable`
- `ego_inflation_early/notable`
- `obsession_level_early/notable`
- `pride_accumulation_early/notable`

---

## Divine Pack

**Path:** `data/events/packs/divine/`
**Context:** `weekly` / `divine_phase`
**Events:** 9

Divine intervention and blessing events.

| Event | Type | Effect |
|-------|------|--------|
| `angel_guardian_host` | Intervention | Target protection |
| `blessing_divine_protection` | Blessing | Resistance buff |
| `blessing_righteous_uprising` | Blessing | Cult opposition |
| `divine_wrath_judgment` | Judgment | Progress reset |
| `exorcism_demon_banishment` | Exorcism | Demon disabled |
| `exorcism_scheme_disruption` | Exorcism | Mission abort |
| `miracle_purifying_light` | Miracle | Corruption cleanse |
| `miracle_restoration` | Miracle | Need recovery |

---

## Intervention Pack

**Path:** `data/events/packs/intervention/`
**Context:** `mission` / `weekly`
**Events:** 8

Suspicion escalation and judgment events.

| Event | Trigger | Effect |
|-------|---------|--------|
| `escalate_to_inquisition` | Suspicion critical | Major investigation |
| `escalate_to_suspicion` | Suspicion high | Increased scrutiny |
| `escalate_to_watched` | Suspicion medium | Target awareness |
| `judgment_imminent` | Risk critical | Cleanse warning |
| `penance_quest_events` | Post-cleanse | Recovery path |
| `scheme_disrupted` | Intervention | Mission failure |
| `severity_decreased` | Low profile | Risk reduction |

---

## Adding New Events

See [[Event System]] for JSON format details.

### Quick Template

```json
{
  "events": [
    {
      "event_id": "your.event.id",
      "event_type": "choice",
      "context": "weekly",
      "tags": ["tag1", "tag2"],
      "priority": 100,
      "conditions": {
        "story_flag": "some.flag"
      },
      "content": {
        "title": "Event Title",
        "description": "What happened..."
      },
      "choices": [...],
      "effects": [...]
    }
  ]
}
```

## Related

- [[Event System]] - Event architecture
- [[Mission Beats]] - Beat mechanics
- [[Cult System]] - Cult events
- [[Intervention Risk]] - Divine events
