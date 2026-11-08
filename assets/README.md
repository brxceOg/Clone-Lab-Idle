# Clone Lab Idle — asset library

The repository contains the verified source artwork for the browser game. The supplied art is committed under `assets/`; use these exact files rather than substitutes.

## Main-scene art pipeline

The approved main game scene is top-down on a 16×16 grid:

1. **Laboratory:** reodesuxz Pixel Sci-Fi Tileset (16×16), in `lab/pixel-sci-fi-tileset/`.
2. **Warriors:** Larchrow 16×16 Characters & Monsters, in `warriors/larchrow-16x16-characters-monsters/`.
3. **Bosses:** Larchrow 16×16 Boss Monsters, in `bosses/larchrow-16x16-boss-monsters/`.

The Larchrow character and boss packs share a 32-colour palette and 16px grid. Keep the original Ninja Adventure 3/4-view prototype art separate; do not mix its perspective into the top-down room.

## Imported asset status

The verified bulk import completed successfully on 2026-11-08. The repository contains 403 PNG assets across the supplied packs, plus source spritesheets, animation indexes, CSV/JSON metadata, palettes, previews, and original license/readme files. The temporary ZIP was removed after extraction.

The authoritative source and QA notes are in `source-notes/VERIFIED_IMPORT.md`. The import workflow is `.github/workflows/import-verified-assets.yml`.

## Rendering rules

- Use nearest-neighbour rendering (`image-rendering: pixelated` / canvas smoothing disabled).
- Preserve original source frame dimensions and proportions.
- Read the supplied animation metadata; do not guess sprite-sheet frame layouts.
- Do not apply hue shifts, blur, blanket filters, or resampling that softens pixel edges.
- Use the 32×32 / 48×48 boss frames to maintain a clear scale difference over 16×16 warriors.
- Keep the legacy Ninja Adventure art separate from the top-down game scene.

## Sources and licenses

- Ninja Adventure: https://pixel-boy.itch.io/ninja-adventure-asset-pack — CC0 1.0.
- Kenney Sci-Fi RTS: https://kenney.nl/assets/sci-fi-rts — CC0 1.0.
- Kenney Monster Builder Pack: https://kenney.nl/assets/monster-builder-pack — CC0 1.0.
- reodesuxz Pixel Sci-Fi Tileset: https://reodesuxz.itch.io/free-pixel-sci-fi-tileset-16x16 — commercial/personal use and modification allowed; no attribution required; no standalone redistribution.
- Larchrow Characters & Monsters: https://larchrow.itch.io/larchrow-16x16-characters-monsters — royalty-free commercial/non-commercial use and modification; attribution optional; no resale/asset-pack redistribution.
- Larchrow Boss Monsters: https://larchrow.itch.io/larchrow-16x16-boss-monsters — royalty-free commercial/non-commercial use and modification; attribution optional; no resale/asset-pack redistribution.


## Effects

- **Free Effect and Bullet 16x16 — BDragon1727:** Four palette atlases (Fire, Green, Purple, Water) in `effects/effect-and-bullet-16x16/`.
- Each atlas is 576×208 and uses 16×16 cells (36 columns × 13 rows). Use source rectangles with nearest-neighbour rendering; do not stretch or recolor the atlas.
- License is for non-commercial game use; commercial use requires a contribution to the creator. Do not redistribute the pack as a standalone asset. See `docs/asset-import/effect-and-bullet-16x16/IMPORT_MANIFEST.md`.
- Integrated into in-game sequences for Knight melee, Mage and Archer projectiles, boss attacks, machine production, and clone emergence. Original atlases and authored frame map remain preserved.


## Font — Pixels, Ayden Snider

- **Font:** Pixels by Ayden Snider (DaFont bitmap / 16 px category).
- **Source:** https://www.dafont.com/pixels.font
- **License:** Free for personal use only, as stated on the DaFont listing. Do not use in a commercial release without obtaining the creator's commercial permission/license.
- **Repository location:** `assets/fonts/Pixels.ttf` (extracted from the user-supplied `pixels.zip`).
- **Integration:** Loaded locally with `@font-face` and used for HTML interface text and canvas-rendered labels. No external font service is required.


## PVFX Foundry 1.0 — Pixel VFX Studio

- **Source:** https://pixel-vfx-studio.itch.io/pvfx-foundry
- **Release:** PVFX Foundry 1.0.
- **License:** CC0 1.0 Universal for the rendered sprite sheets and bundled manifests/documentation. The license does not cover Pixel VFX Studio software or source code, which are not included. Attribution is appreciated but not required; suggested credit: “VFX from PVFX Foundry by Pixel VFX Studio.”
- **Repository location:** `assets/effects/pvfx-foundry/`.
- **Import:** 101 Lit-tier fixed-grid sprite sheets and their matching per-effect JSON manifests. Original frame pixels and timings are preserved. The original user-supplied ZIP remains at the repository root.
- **Rendering:** Canvas draws exact manifest frame rectangles and per-frame durations with smoothing disabled, preserving transparent alpha and authored pivots. Only a curated subset is preloaded by the game; all 101 imported effects remain available for future gameplay additions.
- **Current integration:** Knight sword-combo and impact sparks; Mage magic-missile travel and impact; Archer arrow-impact travel and sparks; boss ground-slam, shockwave, clone-hit bursts, and defeat explosion; machine portal activation and clone teleport-in; upgrade level-up feedback; boss-reward coin pickup.
- **Import record:** `assets/effects/pvfx-foundry/IMPORT_MANIFEST.md`.
