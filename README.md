# ItemFrameController

A Paper, Spigot, and Bukkit plugin for Minecraft 1.16 - 26.3 that controls item frame interactions in selected worlds. It blocks rotation, item placement, breaking by players, breaking by entities, and frame placement for non-creative players.

[![License](https://img.shields.io/badge/license-GPL--3.0-blue)](LICENSE)
[![Version](https://img.shields.io/badge/version-1.0.0-green)]()
[![Platform](https://img.shields.io/badge/platform-Paper%20%7C%20Spigot%20%7C%20Bukkit-lightgrey)]()
[![Minecraft](https://img.shields.io/badge/Minecraft-1.16--26.3-green)]()

## What is it

ItemFrameController gives server administrators fine-grained control over item frames in specific worlds. It is useful for protecting museum builds, adventure maps, custom hubs, or any area where item frames must stay in a fixed state.

The plugin works only in worlds listed in `restricted-worlds`. In those worlds, non-creative players cannot rotate item frames, place items into them, break them, or place new frames. Entities also cannot damage item frames. Creative players bypass all restrictions, so builders can still work normally.

There are no commands and no permission nodes. After installation, the plugin listens to item frame events and applies the configured rules automatically. Every blocked action can send a configurable message to the player.

## Features

- Blocks item frame rotation when a non-creative player sneaks and right-clicks a frame in a restricted world.
- Blocks placing items into item frames when a non-creative player right-clicks without sneaking.
- Blocks non-creative players from breaking item frames. The message is configurable through `messages.knocking-by-player`.
- Blocks entities from damaging item frames. If a player causes the damage, they receive `messages.knocking-by-entity`.
- Blocks placing new item frames in restricted worlds for non-creative players. The message is set in `messages.placing-frames`.
- Applies all rules only to worlds listed in `restricted-worlds`. Other worlds remain unaffected.
- Sends configurable messages for each blocked action. Messages are sent as plain text, so use `§` for color codes.
- Has no external dependencies.

## Installation

1. Download the ItemFrameController `1.0.0` JAR.
2. Place the JAR in your server's `plugins` folder.
3. Restart the server or load the plugin with a plugin manager.
4. Edit `plugins/ItemFrameControllerPlugin/config.yml` to match your server.

No additional setup is required. The plugin does not define commands or permissions, so it works immediately after the server loads it.

## Usage

The plugin has no commands. After installation, it enforces the configured rules automatically.

Non-creative players in restricted worlds cannot rotate item frames, place items into them, break them, or place new frames. Entities cannot damage item frames. Creative players bypass all restrictions. To change which worlds are protected, edit `restricted-worlds` in `config.yml`.

## Configuration

The plugin generates `plugins/ItemFrameControllerPlugin/config.yml`. The default file contains:

```yaml
restricted-worlds:
  - world
  - custom_world

prevent-rotation: true
prevent-placing-items: true
prevent-knocking-by-player: true
prevent-knocking-by-entity: true
prevent-placing-frames: true

messages:
  rotation: "§cYou cannot rotate item frames in this world!"
  placing-items: "§cYou cannot place items into item frames here!"
  knocking-by-player: "§cYou cannot break item frames here!"
  knocking-by-entity: "§cEntities cannot destroy item frames here!"
  placing-frames: "§cYou cannot place item frames in this world!"
```

`restricted-worlds` lists world names where the plugin applies restrictions. World names are case-sensitive and must match the server's world folder names. `prevent-rotation` blocks sneaking players from rotating item frames. `prevent-placing-items` blocks placing items into item frames. `prevent-knocking-by-player` blocks players from breaking item frames. `prevent-knocking-by-entity` blocks entities from damaging item frames. `prevent-placing-frames` blocks placing new item frames.

The `messages` section defines the text sent when an action is blocked. Messages are sent as-is, so use `§` followed by a color code for formatting. Set any message to an empty string to send nothing, though the action is still cancelled.

## Compatibility

- Minecraft: 1.16 - 26.3
- Platform: Paper, Spigot, Bukkit
- Java: any version supported by the server platform; no specific Java version is required

No known incompatibilities with other plugins or libraries.

## Technologies

- Language: Java
- Platform API: Bukkit, Spigot, Paper
- Build: standard plugin JAR
- Key dependencies: none

## License

This project is distributed under the [GNU General Public License v3.0](LICENSE).