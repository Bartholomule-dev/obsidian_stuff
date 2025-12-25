---
type: moc
domain: architecture
layer: logic
status: stable
---
# Services

Domain logic that orchestrates operations across managers. Services contain the "how" of game mechanics.

## Pattern

Managers own state → **Services orchestrate** → Facades provide access

**Key Principles:**
- Stateless or minimal state
- Coordinate across multiple managers
- Implement complex game logic
- Initialized in GameStateInitializer Phase 1-2

## All Services

```dataview
TABLE domain, status, file
FROM "Born Below/Components"
WHERE type = "service"
SORT domain
```

## By Domain

### Demon Services
- DemonLifecycleService - Recruitment, retirement
- DemonLifecycleCoordinator - Lifecycle orchestration
- DemonMoodService - Mood, energy, stress
- DemonMemoryService - Memory formation, recall
- DemonProgressionService - XP, leveling logic
- DemonTrainingService - Training execution
- DemonQuestService - Quest logic
- DemonHistoryService - Timeline, accomplishments
- DemonDialogueService - Dialogue generation
- DemonFeedbackService - Feedback events
- DemonInteractionService - Demon interactions
- DemonSlotService - Slot logic
- DemonStrikeService - Strike mechanics

### Mission Services
- MissionExecutorService - Daily meter updates
- MissionMeterService - Leverage/suspicion/fatigue
- MissionBeatService - Threshold narrative beats
- MissionRewardService - Mission rewards
- MissionActivityLogger - Activity logging

### Corruption Services
- CorruptionStageService - Stage progression
- CorruptionRippleService - Cascading effects
- CharacterDefenseService - Character defenses
- DesperateActionService - Desperate behaviors
- CascadeService - Corruption cascades

### Combat Services
- CombatResolutionService - Multi-turn combat
- CombatSessionService - Visual combat lifecycle
- EncounterResolutionService - Instant battles
- RewardDistributionService - Combat rewards
- TournamentService - Tournament logic
- TournamentController - Tournament flow

### Exploration Services
- ExplorationService - Procedural maps
- ExplorationCoordinator - Exploration orchestration

### Planning Services
- PlanningWorkflowService - Training/mission workflows
- ActivitySelectionService - Activity selection
- OpportunityGenerationService - Card generation
- OpportunityCooldownService - Card cooldowns

### Other Services
- SimulationPhaseCoordinator - Phase orchestration
- AutonomousBehaviorService - Demon AI
- PersonalityEvolutionService - Personality changes
- InterventionService - Divine intervention
- HeatCalculationService - Heat mechanics
- CultExecutionService - Cult action execution
- VerbService - Demon verbs
- IdleActivityService - Idle activities
- HellEconomyService - Economy logic
- NarratorGuideService - Narrator hints
- DivineCleanseService - Cleansing logic
- WeekPerformanceTracker - Performance tracking
- BeatResponseProcessor - Beat responses
- VisualsCoordinator - Visual orchestration
