# Clone Lab Idle — verified asset import bundle

Prepared 2026-11-08 from the three user-supplied ZIP archives.

## Included source packs
- `assets/lab/pixel-sci-fi-tileset/` — reodesuxz Pixel Sci-Fi Tileset (16x16): native 16px PNGs, spritesheet + JSON, sample scene, README and license.
- `assets/warriors/larchrow-16x16-characters-monsters/` — Larchrow 18-character pack: original animation strips, per-character/combined sheets, animation CSV/JSON, palette, README and license.
- `assets/bosses/larchrow-16x16-boss-monsters/` — Larchrow 14-boss pack: original 1x animation strips/sheets, markers, UI tiles, nine-slice textures, animation/tile indexes, palette, README and license.

## QA performed
- All PNGs in all three original ZIP archives opened and passed Pillow image verification: no unreadable PNG files.
- Characters pack QA report: all checks passed; 18 characters, 122 animations, 356 frames; 32-colour palette, binary alpha, valid 16x16 frames and strips.
- Boss pack QA report: all checks passed; 14 bosses, 95 animations, 432 frames, 466 indexed tiles; palette/grid/outline/animation/index checks passed.
- Lab pack README and license inspected; 16x16 top-down tileset with 83 tiles/sprites and no attribution requirement.
- Original licenses and README files are retained alongside the imported art.

## Integration notes
- These selected packs share a top-down 16px visual grid; the two Larchrow packs share the same 32-colour palette.
- The pre-existing Ninja Adventure starter assets are 3/4-view and should not be mixed into the same scene without deliberate conversion. Keep them as an alternate prototype set.
- Use nearest-neighbour rendering and preserve original pixel dimensions/animation frame order.
- This bundle contains engine-neutral source art and metadata. It does not contain game code or imply that the game is playable.
