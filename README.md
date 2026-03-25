# dRandomSpawn

Get random spawns, unique for every player. Lava excluded.

## Features

*   New players start at a safe random location instead of piling up at world spawn.
*   Bedless respawns can reuse the same saved spawn or roll a fresh one each time.
*   Beds, respawn anchors, and `/spawnpoint` can be respected or ignored.
*   You can block unwanted biomes and dangerous blocks from random spawns.
*   Included commands let you view, reroll, or set saved spawns.

## Commands

*   `/drandomspawn get_spawn [player]`: Shows a saved spawn point. Specifying a player requires OP.
*   `/drandomspawn random_teleport [player]`: Sends you or another player to a new random spawn. Requires OP.
*   `/drandomspawn set_spawn [player] [x] [y] [z]`: Sets a player's saved spawn manually. Requires OP.

## Configuration

Notable config options in `dRandomSpawn.toml`:

*   `useSpectatorLock`: Briefly locks the player and hides loading while a random spawn is being found.
*   `ignoreRespawnPoint`: Ignores beds, respawn anchors, and `/spawnpoint`, so the mod handles every respawn.
*   `alwaysRandomSpawn`: Gives a fresh random spawn on each mod-handled respawn instead of reusing the saved one.
*   `biomeBlacklist`: Lists biomes that should never be used for random spawns.
*   `blockBlacklist`: Lists blocks that players should never spawn on.

Respawn behavior combinations:

*   `ignoreRespawnPoint = false`, `alwaysRandomSpawn = false`: Beds and anchors work normally. Otherwise, players return to their saved random spawn.
*   `ignoreRespawnPoint = false`, `alwaysRandomSpawn = true`: Beds and anchors work normally. Otherwise, players get a fresh random spawn each time.
*   `ignoreRespawnPoint = true`, `alwaysRandomSpawn = false`: Beds and anchors are ignored. Players return to their saved random spawn.
*   `ignoreRespawnPoint = true`, `alwaysRandomSpawn = true`: Beds and anchors are ignored. Players get a fresh random spawn on every respawn.

## Credits

This project is a heavily revamped fork of the original [RandomSpawn](https://github.com/rinko1231/RandomSpawn) project by rinko1231, released under MIT; the original license is available under `LICENSE.original.md`.
