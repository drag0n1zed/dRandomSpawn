# dRandomSpawn

A simple mod that teleports new players to a random location and sets it as their spawn, asynchronously.

## Features

*   **Asynchronous Random Spawn:** New players are teleported to a unique, safe random location without blocking the server thread.
*   **Flexible Bedless Respawns:** By default, bedless respawns return players to their saved random spawn. Enable `alwaysRandomSpawn` to roll a fresh random location for any respawn the mod handles.
*   **Optional Respawn-Point Override:** Enable `ignoreRespawnPoint` to bypass beds, respawn anchors, and `/spawnpoint`, making the mod handle every respawn instead of only bedless ones.
*   **Spectator Lock (Configurable):** Optionally places players in spectator mode and gives darkness during any random spawn search so world loading stays hidden.
*   **Intelligent Respawn Handling:** By default, player-set beds, respawn anchors, and `/spawnpoint` commands are respected until `ignoreRespawnPoint` is enabled.
*   **Customizable Spawn Conditions:**
    *   **Search Radius:** Define the maximum distance for random teleportation.
    *   **Biome Blacklist:** Exclude specific biomes from potential spawn locations.
    *   **Block Blacklist:** Prevent spawning on undesirable or hazardous blocks.
*   **Commands:**
    *   `/drandomspawn get_spawn [player]`: Allows players to view their saved spawn points. Requires OP to specify player.
    *   `/drandomspawn random_teleport [player]`: Initiates random teleport and saves the new location. Requires OP.
    *   `/drandomspawn set_spawn [player] [x] [y] [z]`: Sets player spawn position manually. Requires OP.

## Configuration

Edit `dRandomSpawn.toml` located under `/config`:

*   `maxDistance`: The maximum radius, in blocks, from the world spawn for random teleportation.
*   `minDistance`: The minimum radius, in blocks, from the world spawn for random teleportation.
*   `maxTries`: How many times the mod will try to find a safe location within the maxDistance. If all attempts fail, the player will spawn at the default world spawn.
*   `useSpectatorLock`: If true, puts a player into spectator mode while any random spawn search is running. This prevents movement and hides world loading for a smoother experience.
*   `ignoreRespawnPoint`: If true, beds, respawn anchors, and `/spawnpoint` are ignored, so the mod handles every respawn. If false, the mod only handles respawns when no respawn point is set.
*   `alwaysRandomSpawn`: If true, every respawn handled by the mod finds a fresh random spawn. If false, handled respawns reuse the player's saved random spawn point.
*   `biomeBlacklist`: A list of biomes where new players are not allowed to spawn. Entries must be valid biome resource locations, e.g., 'minecraft:ocean' or 'biomesoplenty:wasteland'.
*   `blockBlacklist`: A list of blocks that players cannot spawn directly on top of. This is useful for preventing spawns on dangerous blocks. Entries must be valid block resource locations, e.g., 'minecraft:lava'.

Respawn behavior combinations:

*   `ignoreRespawnPoint = false`, `alwaysRandomSpawn = false`: Respect player respawn points; otherwise reuse the saved random spawn.
*   `ignoreRespawnPoint = false`, `alwaysRandomSpawn = true`: Respect player respawn points; otherwise choose a fresh random spawn each time.
*   `ignoreRespawnPoint = true`, `alwaysRandomSpawn = false`: Ignore player respawn points and always return to the saved random spawn.
*   `ignoreRespawnPoint = true`, `alwaysRandomSpawn = true`: Ignore player respawn points and choose a fresh random spawn on every respawn.

## Credits

This project is a heavily revamped fork of the original [RandomSpawn](https://github.com/rinko1231/RandomSpawn) project by rinko1231, released under MIT; the original license is available under `LICENSE.original.md`.
