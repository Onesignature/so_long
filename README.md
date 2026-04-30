# so_long

A 42 graphical project: a small 2D game built with the **MiniLibX** library where the player navigates a maze, collects items, and reaches the exit.

![screenshot](screenshot.png)

## Features

- Loads and parses a maze from a `.ber` map file
- Keyboard-controlled character movement
- Collectible items + exit unlocking
- Tile-based rendering via MiniLibX
- Map validation, including a DFS path-checking algorithm to confirm the map is solvable

## Build

```bash
make
```

Requires **MiniLibX** — see the [MiniLibX docs](https://harm-smits.github.io/42docs/libs/minilibx/) for installation.

## Run

```bash
./so_long maps/valid/map.ber
```

## Map format

A valid `.ber` file uses the following tiles:

| Char | Meaning |
|---|---|
| `1` | Wall |
| `0` | Empty space |
| `C` | Collectible item |
| `E` | Exit |
| `P` | Player start |

The map must be rectangular, fully enclosed by walls, and contain exactly one `P`, at least one `C`, and at least one `E`.

## Layout

- `so_long.c`, `so_long.h` — entry point and headers
- `parser.c`, `parser2.c` — map file parsing and validation
- `dfs.c` — depth-first path check (confirms `P` can reach every `C` and the `E`)
- `keyhooks.c` — keyboard input handling
- `utils/` — helper functions
- `img/` — sprite assets
- `maps/` — sample valid and invalid maps
- `mlx/` — MiniLibX
