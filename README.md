# Mordhau-BotSpawner
An automated bot spawner for Mordhau
# INI Settings
The following are the default settings, that can be modified by adding this section to `Engine.ini`. To keep the default settings, you do not need this entry in `Engine.ini`.

```ini
[/Game/Mordhau/Maps/BotSpawner/BP_BotSpawner.BP_BotSpawner_C]
botSpawnerInitialDelaySeconds=5.0
botSpawnerMinimumPlayers=1
botSpawnerTargetBotsPerTeam=30
botSpawnerBotBatchSize=1
botSpawnerSpawnDelaySeconds=1.0
```
The settings can be interpreted in this fashion:
Once a match has started, and there are at least **botSpawnerMinimumPlayers** players present, wait **botSpawnerInitialDelaySeconds** and then start adding **botSpawnerBotBatchSize** bots every **botSpawnerSpawnDelaySeconds** until there are **botSpawnerTargetBotsPerTeam** bots per team.
