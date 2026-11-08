LARCHROW - 16x16 BOSS MONSTERS
14 pixel-art bosses for top-down RPG, action and dungeon games, built on the 16 px grid: 7 bosses at 32x32 (2x2 tiles) and
7 at 48x48 (3x3 tiles). Every boss has idle, attack, hurt and death animations plus an enraged phase 2 (idle + attack,
recoloured, with flames and faster timings). On top: a boss HP bar (3-slice frame + 5 fills), name plate, phase pips, a boss
panel nine-slice and 10 animated telegraph / warning markers. Same 32-colour palette as the other Larchrow 16x16 packs
(Characters & Monsters, NPCs & Villagers, Dungeon, Overworld, HUD & UI Icons, Effects...). Hard pixels only (alpha fully on
or off), 1px dark outline on every boss.

FILES
Tilesheets/larchrow_bosses_small_32x32.png    bosses 32x32: 192x1344 (6 columns; 6 rows per boss = idle, attack, hurt,
                                           death, idle_enraged, attack_enraged; unused cells transparent)
Tilesheets/larchrow_bosses_large_48x48.png    bosses 48x48: 288x2016, same layout
Tilesheets/larchrow_bosses_markers_32x32.png  ground telegraphs 32x32: 128x160 (4 columns, one row per marker)
Tilesheets/larchrow_bosses_ui_16x16.png       16x16 UI: 192x80 (HP bar slices, plate, panel, pips, skull, 16x16 markers)
Tilesheets/*_2x.png / *_3x.png             every sheet scaled 2x / 3x nearest-neighbour
Sprites/bosses/<boss>/                     <boss>_sheet_<S>x<S>.png (6 animations x 6 columns) and one strip per animation
                                           (<boss>_<anim>_strip_<N>f.png), each also as _3x
Sprites/markers/                           strips of all 10 telegraphs and the enrage icon (+ _3x)
Sprites/sprites.json                       every strip: frames, frame size, ms per frame, loop, tile names, sheet rects
Tiles/                                     every 16x16 UI piece and marker frame as its own PNG
NineSlice/                                 8 textures: HP bar frame + 5 fills (three-slice, 48x16), name plate (48x16),
                                           boss panel (nine-slice 48x48), 1x and 3x + nine_slice.json (margins in px)
                                           + examples/ (bars at 192 px wide, full / 60 % / enraged 35 %, panel 208x64)
Godot4/larchrow_bosses/                       SpriteFrames .tres per boss (6 animations each), markers.tres, ui_markers.tres,
                                           boss_demo.gd and demo_boss_fight.tscn
Tiled/                                     one .tsx per sheet with names, groups and all 95 animations + boss_lineup.tmx
Palette/                                   larchrow32 palette as .png, .gpl (GIMP/Aseprite) and .hex
Previews/                                  bosses in a dungeon, at sea, in a forest and on lava, animated GIFs, sheet previews
tile_index.csv / tile_index.json           sheet, id, name, column, row, x, y, w, h, category, group, animation, frame
animation_index.csv / animation_index.json every animation: boss, action, phase, frames, ms, loop, sheet rects, strip;
                                           the JSON also lists the bosses with size, description and phase-2 look
qa-report.json                             automatic quality check results

CONTENTS
- 14 bosses:
  slime king       32x32  giant crowned slime that hops and slams; phase 2: turns red-hot
  lich             32x32  floating skeletal sorcerer with a soul-orb staff; phase 2: robes burn crimson
  dragon whelp     32x32  young fire dragon with flapping wings and fire breath; phase 2: scales darken, fire runs hotter
  stone golem      48x48  towering stone golem with mossy shoulders and glowing eyes; phase 2: cracks glow with lava
  kraken           48x48  sea kraken rising from the water with four curling tentacles; phase 2: turns blood-red
  kraken tentacle  32x32  single kraken tentacle that bursts out of the water (use several around the kraken); phase 2: turns blood-red
  demon lord       48x48  horned demon lord with bat wings and a fire orb; phase 2: skin turns violet, wings ignite
  tree guardian    48x48  ancient walking tree guardian with root legs and branch arms; phase 2: leaves turn to autumn fire
  minotaur         48x48  bull-headed brute with a double-bladed axe; phase 2: fur flushes red, eyes burn
  spider queen     48x48  giant crowned spider queen that rears up and spits web; phase 2: turns crimson
  phantom knight   32x32  ghostly armoured knight that floats and slashes; phase 2: spectral flame turns violet
  frost yeti       48x48  huge frost yeti with ice horns that throws ice shards; phase 2: fur frosts blue, eyes glow red
  goblin warlord   32x32  goblin warlord in horned helmet with a spiked club and war cape; phase 2: skin flushes with war rage
  watcher eye      32x32  floating giant eye with tendrils that fires a beam; phase 2: iris and tendrils burn red
- Per boss 6 animations: idle 4f (180 ms, loop), attack 6f (110 ms), hurt 2f (120 ms), death 6f (130 ms),
  idle_enraged 4f (140 ms, loop), attack_enraged 6f (90 ms) = 84 animations, 392 frames
- Death: flash, squash, smoke and a small remnant (crown, skull, rocks, gem, log, horn, ice, helmet...) on the last frame,
  so you can leave it on the floor as loot spot
- 32x32 ground telegraphs: aoe_circle (4f), aoe_shrink (4f), target_lock (4f), ground_crack (4f), enrage_burst (4f)
- 16x16 markers: warn_exclaim (3f), target_reticle (4f), drop_arrow (4f), danger_stripes (4f), countdown (3f), enrage_icon (2f)
- Boss HP bar: three-slice frame with skull badge + fills in red, purple (phase 2), white (damage flash), gold (shield) and
  green (ally / heal); name plate; phase pips (full / empty / rage); skull icon; boss panel nine-slice
- 95 animations, 432 frames, 466 tiles in total

HOW TO USE
Bosses: use the strips, or a sheet + animation_index.json (rects in px). Each boss stands on the bottom of its cell with
a 1 px transparent margin; place a 32x32 boss on 2x2 tiles, a 48x48 boss on 3x3 tiles. Play attack / hurt / death once,
loop the idle animations. Switch to idle_enraged / attack_enraged when the boss drops below half HP (phase 2).
Telegraphs: draw the 32x32 marker on the ground where the attack will land for ~1 s before the attack frame hits.
HP bar: draw boss_hp_frame as a three-slice (16 px fixed left/right caps, middle repeats) at any width; draw a fill with
the same width on top and clip it at x = 14 + (width - 20) * hp. The name plate (4 px caps) goes under the bar.

GODOT 4 (tested with Godot 4.3)
Copy the folder Godot4/larchrow_bosses into your project root so the path is res://larchrow_bosses/. Open demo_boss_fight.tscn: the demon lord
idles, a telegraph and a warning appear, it attacks, gets hurt and the HP bar drains; below 50 % it switches to its
enraged animations, the bar turns purple and the rage icon shows; at 0 HP it dies and the fight resets (boss_demo.gd).
AnimatedSprite2D: Sprite Frames = spriteframes/<boss>.tres, animations idle, attack, hurt, death, idle_enraged,
attack_enraged. Markers: spriteframes/markers.tres (32x32) and ui_markers.tres (16x16).
Tip: Project Settings -> Rendering -> Textures -> Default Texture Filter = Nearest.

OTHER ENGINES
Plain grids: Unity (Sprite Mode Multiple, Grid by Cell Size 32 or 48, Filter Point, Compression None; bar borders from
nine_slice.json), GameMaker, Defold, LÖVE, Construct, Tiled (Tiled/*.tsx). Sheets come in 1x, 2x and 3x.

ORIGIN
Every pixel was generated by Larchrow's own Python code (numpy + Pillow) from a hand-picked 32-colour palette: shape and
shading rules for the bodies, hand-placed details, and shared rules for hurt, death and the enraged look. Drawn by code,
no AI: no generative AI, no third-party assets, no traced or copied sprites from existing games. Generic fantasy creatures
only. The preview backgrounds and heroes are from our own Larchrow packs and are not part of this download.

LICENSE: see LICENSE.txt
