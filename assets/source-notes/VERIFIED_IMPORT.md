# Verified asset import audit

**Inspection date:** 2026-11-08  
**Project:** Clone Lab Idle  
**Status:** ZIP contents verified; repository binary import remains pending.

## Archive integrity

| Supplied archive | Entries | PNG files | PNG verification |
|---|---:|---:|---|
| `Pixel_Sci-Fi_Tileset_v1.0.zip` | 191 | 169 | All opened successfully |
| `larchrow-16x16-characters-monsters.zip` | 267 | 186 | All opened successfully |
| `larchrow-16x16-boss-monsters.zip` | 351 | 315 | All opened successfully |

## Character pack QA report

The included report records all checks as passed:
- 18 characters: 8 heroes/NPCs and 10 monsters.
- 122 animations and 356 frames.
- Shared 32-colour palette; no foreign colours or semi-transparent pixels.
- 16×16 grid, closed 1px outlines, no empty/static frames.
- Strips, per-character sheets, combined sheet, and CSV/JSON index agree.
- Godot 4.3 SpriteFrames and demo scene load successfully.

## Boss pack QA report

The included report records all checks as passed:
- 14 bosses: 7 at 32×32 and 7 at 48×48.
- 95 animations and 432 frames; 84 boss animations.
- 466 indexed tiles including boss frames, telegraphs, HP bar, icons and panels.
- Shared Larchrow 32-colour palette; no semi-transparent pixels.
- Frame sizes, outlines, animation indexes, nine-slice textures and Godot/Tiled exports validate.

## Lab pack inspection

- The pack README describes 83 top-down 16×16 tiles/sprites.
- Includes 20 floor tiles, 16 wall pieces, 7 doors/stairs, 18 props, 5 traps, 7 items, 8 enemy frames and 2 player sprites.
- Native PNGs, 4× PNGs, a 160×144 spritesheet + JSON, and sample scene are included.
- License permits personal and commercial projects and modification; no attribution required. Standalone resale/redistribution is prohibited.

## Main-scene asset choice

Use the top-down sci-fi tiles and Larchrow characters/bosses together. The two Larchrow packs explicitly share a 32-colour palette and 16px grid. Keep the previously committed Ninja Adventure 3/4-view assets as a separate prototype set.

## Import bundle

A curated engine-neutral bundle was prepared with native lab PNGs, character animation strips/sheets/indexes, boss strips/sheets/tiles/UI/indexes, palettes, and original license/readme files. It omits redundant engine exports and enlarged duplicate sheets. The bundle is a convenience import artifact, not a substitute for committing the source assets to the repository.

**Important:** This audit does not claim that the binary assets have been committed or that a playable game exists. The repository still needs its actual browser-game implementation.
