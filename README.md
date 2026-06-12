# Relationshapez: Cornering Queen

**Cornering Queen** is a single-file HTML activity for exploring the relationship game played by moving a queen toward the lower-left corner of an `N × N` board.

The remote version is intended to be available at:

<https://relationshapez.github.io/cornering_queen/>

## Files

- `index.html` — the complete app in one HTML file.
- `README.md` — this documentation file.

## How to play

The board uses zero-based coordinates with `(0,0)` in the lower-left corner. This is the winning square. On an `N × N` board, the coordinates run from `0` to `N - 1` in each direction.

A queen can move in three directions only:

1. Horizontally left.
2. Vertically down.
3. Diagonally down-left, moving the same number of squares left and down.

Tap or click a valid square to move the queen there. If an invalid square is selected, that square is briefly highlighted and the app displays **Invalid Move**.

When the queen reaches `(0,0)`, the app displays **You Win!**

## Tabs

The app has two tabs. A slider at the top switches between **Game** on the left and **Settings** on the right.

### Game

The Game tab displays the board. The game controls appear beneath the board.

- **Undo** returns to the previous queen position. Repeated presses step backward through the whole move history.
- **Reset** returns the current game to its starting position.

If **Random start** was selected before the game began, Reset returns the queen to that same random starting square. If Random start was not selected, Reset returns the game to an empty board so the first move can place the queen again.

### Settings

The Settings tab controls the game setup.

Press **Start** to begin a game. While a game is running, the settings are locked and the Start button changes to **Stop**. Press **Stop** to end the current game, deactivate the board, and unlock the settings.

## Settings options

### N

Sets the board size. The board is `N × N`.

### Random start

When selected, the queen is placed randomly when the game starts. Random starts avoid positions with `x = y`, since those are trivial diagonal wins.

When not selected, the board starts empty and the first tap/click places the queen.

### Show moves

Highlights the legal moves from the queen's current square.

### Show safe spots

Highlights the safe spots on the board. Since the winning square is `(0,0)`, these are the Wythoff pairs

```text
(floor(nφ), floor(nφ²))
```

and their coordinate reversals, together with the winning square `(0,0)`, where

```text
φ = (1 + sqrt(5)) / 2.
```

Since `floor(nφ²) = floor(nφ) + n`, the safe spots can also be written as

```text
(floor(nφ), floor(nφ) + n)
```

and the reversed pairs.

### Show lines

Overlays two guide lines passing through the lower-left corner of the board:

- one with slope `φ`,
- one with slope `1/φ`.

These lines help visualize why the safe spots follow the golden-ratio pattern.

### Show variables

Displays four lines of calculations that can help identify a winning move.

The first line gives the queen's current coordinates and whether `x < y`, `y < x`, or `x = y`.

The next three lines use the same formulas for every square:

```text
n₁ = |y - x|,              ⌊n₁φ⌋
n₂ = ⌈min(x,y) / φ⌉,      ⌊n₂φ⌋,      ⌊n₂φ²⌋
n₃ = ⌈min(x,y) / φ²⌉,     ⌊n₃φ⌋
```

In the app, each formula is shown together with its computed value. For example, the display has the form

```text
(x, y)   x < y
n₁ = |y−x| = #, ⌊n₁φ⌋ = #
n₂ = ⌈min(x,y)/φ⌉ = #, ⌊n₂φ⌋ = #, ⌊n₂φ²⌋ = #
n₃ = ⌈min(x,y)/φ²⌉ = #, ⌊n₃φ⌋ = #
```

These values correspond to common checks for whether a move can reach a safe spot horizontally, vertically, or diagonally.

## Mobile use

The app is designed to fit on small screens. It uses large tap targets, a square responsive board, and a minimal interface.

## License

Copyright (c) 2026 Alan Miller.

This project is released under the **MIT License**.

See the [`LICENSE`](LICENSE) file for the full license text.
