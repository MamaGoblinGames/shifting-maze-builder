# Shifting Maze Builder

A level editor for a maze whose walls shift. It's a single HTML file with no build step, made for a family game jam.

**Try it:** https://mamagoblingames.github.io/shifting-maze-builder/

## What it does

- **Levels:** make as many levels as you want, each with its own size, tile size, walk speed, camera size, and design notes.
- **Layouts (shift states):** each level has one or more layouts, and each layout is one arrangement of walls. When the maze shifts, it moves on to the next layout. Duplicate a layout and change some walls to design a shift.
- **Objects:** place a start, an exit door, pedestals, glyph tablets, journal pages, levers, gears, beetles, and design notes. You can make an object appear only in some layouts.
- **Checks while you build:** see which tiles change between layouts, which floor the player can't reach from the start, the path length from start to exit in each layout, and which tablets match a pedestal and which are decoys.
- **Playtest:** walk the level with the arrow keys or WASD. E picks up or places a tablet or pulls a lever, Space forces a shift, and Esc goes back to editing. You can set what makes the maze shift (a key press, a timer, placing a stone, or pulling a lever), how many stones the player can carry, and what happens when a stone is wrong.

Your work saves automatically in your browser's `localStorage` under the key `maze-builder-v1`. It stays in that browser on that computer, so export your levels to keep a copy or move them somewhere else.

## Exporting levels

Click **Export levels** at the top right. Your browser downloads `maze-levels.json` with every level in it.

If your browser can't download the file, a window opens with the level data instead. Copy all of the text and save it as a `.json` file.

## Importing levels

1. Click **Import**.
2. Click **Choose a file…** and pick an exported `.json` file, or paste the file's text into the box and click **Add these levels**.

Imported levels are added next to the ones you already have. Nothing is replaced.

## File format

The export is JSON:

```json
{
  "format": "maze-builder",
  "version": 1,
  "tileKey": { "0": "floor", "1": "wall" },
  "levels": [
    {
      "name": "Level 1",
      "w": 24,
      "h": 16,
      "layouts": [{ "name": "Layout A", "tiles": [1, 1, 1, "…"] }],
      "objects": [{ "type": "start", "x": 2, "y": 13 }]
    }
  ]
}
```

Each layout's `tiles` is a flat array of `w × h` numbers, read row by row from the top left, where `0` is floor and `1` is wall. A game can read this file directly to load the levels.

## Running it locally

Open `index.html` in a browser. There's nothing to install.
