# Mordhau-BotSpawner
An automated bot spawner for Mordhau. This has been tested on dedicated servers only.

This will spawn bots according to the settings below when there are players present. The bots will be removed at the end of a match or if there are no players left. Bots do not take up player slots, and their numbers may exceed the match maximum. However be aware that configuring a large number of bots may use up all of your server capacity.

# Installation

Place the PAK file under `Mordhau/Content/Paks`. Then in `Game.ini`, add the following under the `[/Script/Mordhau.MordhauGameMode]` section, and restart the server:

```ini
SpawnServerActorsOnMapLoad=/Game/Mordhau/Maps/BotSpawner/BP_BotSpawner.BP_BotSpawner_C
```

# Configuration
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

Once a match has started, and there are at least **botSpawnerMinimumPlayers** players present, wait **botSpawnerInitialDelaySeconds** and then start adding **botSpawnerBotBatchSize** bots every **botSpawnerSpawnDelaySeconds** until there are **botSpawnerTargetBotsPerTeam** bots per team, minus any players present on that team.

Note that for Deathmatch, Horde and Battle Royale maps, there will be a total of **botSpawnerTargetBotsPerTeam** in the match since there is only one "team"

**Optional Settings**

It is possible to modify the individual number of bots for each team with the following optional settings. Team0 is Red and Team1 is Blue.

```ini
botSpawnerTargetBotsForTeam0=10
botSpawnerTargetBotsForTeam1=30
```

In this example, there would be 10 bots spawned for Team0 and 30 bots for Team1, minus any players present in those teams.

# Coop Mode

The following optional setting will switch the server to Coop mode.
```ini
botSpawnerCoopTeam=1
```

This will force all players to the selected team, regardless of their team selection. `botSpawnerCoopTeam=0` will put all players in Team 0 (Red), and `botSpawnerCoopTeam=1` will put all players in Team 1 (Blue).

In combination with `botSpawnerTargetBotsForTeam0` and `botSpawnerTargetBotsForTeam1` you can therefore create different coop scenarios of varying difficulty.

