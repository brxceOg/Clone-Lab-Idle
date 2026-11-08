# Larchrow 16x16 Characters & Monsters (18 characters, 122 animations, 356 frames)

Animated top-down RPG sprites: 8 heroes/NPCs and 10 monsters. Every frame is 16x16 with a 1px dark outline
(#120e1a), hard pixels (alpha is only 0 or 255) and uses only the 32-colour Larchrow palette, the same one as our
*Pixel Dungeon & Overworld Tileset*, *Village & Cave Expansion* and *RPG Item Icons*.

## Characters
| Group | Characters | Animations |
|---|---|---|
| Heroes & NPCs (8) | knight, mage, archer, rogue, villager, merchant, guard, elder | idle_down/left/right/up (2 frames), walk_down/left/right/up (4 frames) |
| Monsters, 4 directions (2) | skeleton, goblin | idle_<dir> (2), walk_<dir> (4), hit (1), death (4) |
| Monsters, left/right (3) | ghost, rat, wolf | idle_left/right (2), move_left/right (4), hit (1), death (4) |
| Monsters, no direction (5) | slime, bat, spider, mushroom, golem | idle (2), move (4), hit (1), death (4) |

`hit` is a one-frame white flash; `death` = flash, squash, two puff-of-smoke frames (play once).
Suggested speeds (also in the index and the Godot files): idle 3 fps, walk/move 8 fps, hit 10 fps, death 8 fps.
Right-facing frames are exact mirrors of the left-facing ones.

## Contents
```
PNG/<group>/<name>/<name>_<animation>.png             one horizontal strip per animation (16px high, 16px per frame)
Spritesheet/per_character/<name>_16x16.png            one sheet per character: 1 row per animation, 4 columns (64px wide)
Spritesheet/per_character/<name>_48x48_3x.png         same, scaled 3x (nearest neighbour)
Spritesheet/larchrow_chars_combined_16x16.png         all characters in one sheet (640x288), heroes on top
Spritesheet/larchrow_chars_combined_48x48_3x.png      same, 3x
animation_index.csv / animation_index.json            every animation: frames, fps, loop, sheet row, pixel rects
Godot4/larchrow_chars/                                sheets + one SpriteFrames .tres per character + demo scene
Palette/                                              the 32 colours as .png, .gpl (GIMP/Aseprite) and .hex (Lospec)
Previews/                                             labelled overview (3x), animated GIFs (one per character + showcase)
screenshots/, cover_*.png                             store images (the example maps are from our tileset packs, not included)
qa-report.json                                        automatic checks (see below)
```
Empty cells in a sheet (e.g. columns 3-4 of a 2-frame idle row) are fully transparent.

## Godot 4 (tested with Godot 4.3)
1. Copy `Godot4/larchrow_chars/` into your project so it ends up at `res://larchrow_chars/` (the .tres files use that path).
2. For crisp pixels set *Project Settings > Rendering > Textures > Canvas Textures > Default Texture Filter* to **Nearest**.
3. Add an `AnimatedSprite2D`, set *Sprite Frames* to `res://larchrow_chars/spriteframes/<name>.tres`, pick an animation.
4. `demo.tscn` shows all 18 characters; the knight uses `demo_walk.gd` (arrow keys, plays idle_/walk_ + direction).

## Other engines
Use the per-character sheets with a 16x16 grid (no spacing, no margin) and `animation_index.csv` for the rows,
or the PNG strips. Unity: Sprite Mode Multiple, Grid By Cell Size 16x16, Filter Point, Compression None.
GameMaker / Phaser / LOVE / Pygame: 16x16 frames. Scale only by whole numbers with nearest-neighbour filtering.

## Quality checks (qa-report.json)
Palette identical to our other pixel packs; only palette colours; no semi-transparent pixels; every frame has a closed
1px outline and is not empty; frame counts consistent; no static animations; right = mirrored left; strips, sheets,
combined sheet, 3x copies, index and Godot files match; all SpriteFrames and the demo scene load in Godot 4.3.

## Origin
Every sprite is drawn by Larchrow's own Python code (numpy + Pillow): small hand-written pixel templates, a body
"doll" with walk phases, and shape rules, then reviewed by eye frame by frame. No generative AI, no third-party assets,
nothing traced or copied from existing games; the characters are generic fantasy types, not based on any known
game character.

## License
See LICENSE.txt: royalty-free for commercial and non-commercial use; do not resell or redistribute the sprites as-is.
