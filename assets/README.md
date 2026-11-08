# Clone Lab Idle — asset library

The repository's original starter assets are retained as a separate 3/4-view prototype set. The preferred art direction for the main game scene is now top-down on a 16×16 grid, using the three user-supplied packs documented below.

## Existing starter assets (alternate 3/4-view set)

- `warriors/ninja-blue.png`, `warriors/samurai-blue.png`: four-direction 3/4-view sheets from Ninja Adventure.
- `lab/interior-floor-tiles.png`, `lab/interior-wall-tiles.png`: interior tiles from Ninja Adventure.
- `lab/scifi-console.png`: Kenney Sci-Fi RTS fixture.
- `bosses/components/` and `bosses/first-boss.svg`: Kenney Monster Builder components and a static composition.

Do not mix these perspective-specific assets into the top-down room without deliberate conversion.

## Verified incoming top-down packs (2026-11-08)

All three supplied ZIP archives were inspected. Every PNG in each archive opened successfully. Full QA results and license notes are in `source-notes/VERIFIED_IMPORT.md`.

1. **Lab — reodesuxz, Free Pixel Sci-Fi Tileset (16x16)**  
   https://reodesuxz.itch.io/free-pixel-sci-fi-tileset-16x16  
   83 described 16×16 tiles/sprites; native PNGs, spritesheet + JSON, sample scene. Commercial use and modification allowed; no attribution required; no standalone redistribution/resale.

2. **Warriors — Larchrow, 16x16 Characters & Monsters**  
   https://larchrow.itch.io/larchrow-16x16-characters-monsters  
   8 heroes/NPCs + 10 monsters; 122 animations / 356 frames. The included QA report passed all checks. Commercial use and modification allowed; attribution optional; no resale/asset-pack redistribution.

3. **Bosses — Larchrow, 16x16 Boss Monsters**  
   https://larchrow.itch.io/larchrow-16x16-boss-monsters  
   14 bosses (32×32 and 48×48); 95 animations / 432 frames, telegraphs and HP UI. The included QA report passed all checks. Commercial use and modification allowed; attribution optional; no resale/asset-pack redistribution.

## Rendering rules

- Use nearest-neighbour / `image-rendering: pixelated`.
- Keep 16×16 source frames at native resolution and preserve the provided animation indexes.
- The two Larchrow packs share a 32-colour palette. Do not apply hue shifts, blur, or blanket filters.
- Use the larger 32×32 / 48×48 boss frames to maintain a clear scale difference over 16×16 warriors.

## Repository status

The supplied ZIPs have been verified, but the PNG binaries are not yet committed to this repository. The curated engine-neutral bundle `Clone-Lab-Idle-verified-assets.zip` was prepared separately for import. No game code or playable page exists yet; do not reference uncommitted assets from game code.

## Sources and licenses

- Ninja Adventure: https://pixel-boy.itch.io/ninja-adventure-asset-pack — CC0 1.0.
- Kenney Sci-Fi RTS: https://kenney.nl/assets/sci-fi-rts — CC0 1.0.
- Kenney Monster Builder Pack: https://kenney.nl/assets/monster-builder-pack — CC0 1.0.
- reodesuxz Pixel Sci-Fi Tileset: https://reodesuxz.itch.io/free-pixel-sci-fi-tileset-16x16 — commercial/personal use and modification allowed; no attribution required; no standalone redistribution.
- Larchrow Characters & Monsters: https://larchrow.itch.io/larchrow-16x16-characters-monsters — royalty-free commercial/non-commercial use and modification; attribution optional; no resale/asset-pack redistribution.
- Larchrow Boss Monsters: https://larchrow.itch.io/larchrow-16x16-boss-monsters — royalty-free commercial/non-commercial use and modification; attribution optional; no resale/asset-pack redistribution.
