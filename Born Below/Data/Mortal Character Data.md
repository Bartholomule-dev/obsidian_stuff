---
type: data
domain: mortal
status: stable
---
# Mortal Character Data

Resource class defining mortal corruption targets.

## Resource Class

`MortalCharacterData` extends `Resource`

**Location:** `data/mortal_characters/` (23 .tres files)

## Core Properties

### Identity

| Property | Type | Description |
|----------|------|-------------|
| `id` | String | Unique identifier |
| `display_name` | String | Shown in UI |
| `character_type` | String | knight, bishop, queen, etc. |
| `portrait` | Texture | Character image |

### Seven Needs (0-100)

| Property | Sin Mapping | Recovery Rate |
|----------|-------------|---------------|
| `security` | Wrath | Fast (+7) |
| `standing` | Envy | Medium (+5) |
| `esteem` | Pride | Medium (+5) |
| `wealth` | Greed | Slow (+3) |
| `desire` | Lust | Slow (+3) |
| `comfort` | Gluttony | Medium (+5) |
| `purpose` | Sloth | Fast (+7) |

### Corruption State

| Property | Type | Description |
|----------|------|-------------|
| `corruption_stage` | int | 0-4 (innocent to corrupted) |
| `is_corrupted` | bool | Stage 4 reached |
| `corruption_flavor` | String | Outcome type |
| `desperate_behavior_count` | int | Breaking point progress |

### Awareness & Defense

| Property | Type | Description |
|----------|------|-------------|
| `awareness` | int | 0-100 suspicion level |
| `holiness` | float | Divine protection modifier |
| `active_defenses` | Array | Current active defenses |
| `sin_vulnerabilities` | Dictionary | Vulnerable sins |

### Weekly State

| Property | Type | Description |
|----------|------|-------------|
| `received_pressure_this_week` | bool | Recovery eligibility |
| `scheme_sin_history` | Dictionary | For Change Routine |

## Demo Characters

| Character | Type | Key Vulnerability |
|-----------|------|-------------------|
| Knight | knight | Honor-bound |
| Bishop | bishop | Faith-driven |
| Queen | queen | Power-focused |

## Related

- [[Corruption System]] - How data is used
- [[MortalCharacterFacade]] - Data access API
- [[Seven Sins]] - Need/sin mapping
