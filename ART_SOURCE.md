# Clone Lab Idle — Art Source & Visual Direction

> Canonical visual and asset guide. Read this document before creating, replacing, or substantially modifying visual assets, animations, layout styling, or character presentation.

## Art direction summary

Clone Lab Idle is a **2D pixel-art laboratory simulation** with the friendly, compact charm of Kairosoft-style management games.

The room should look like a clean, modern research laboratory rendered in warm, carefully detailed pixel art. The visual contrast is intentional: a bright, orderly white lab containing a growing crowd of tiny, expressive fantasy/RPG warriors fighting oversized bosses.

The game should feel cute, readable, lively, and handcrafted—not sterile corporate software, not gritty science fiction, and not a generic fantasy battle screen.

## Current starter asset sources

The original starter library remains under `assets/` and is retained as an alternate 3/4-view prototype set:

1. **Ninja Adventure — Pixel-Boy and AAA:** two four-direction RPG warrior sheets plus interior floor and wall tiles.
2. **Sci-Fi RTS — Kenney:** a selected sci-fi console/structure sprite.
3. **Monster Builder Pack — Kenney:** modular boss components and a static first-boss composition.

For the main game scene, the preferred camera/art pipeline is now **top-down on a 16×16 grid**, using the verified reodesuxz laboratory tiles and Larchrow character/boss packs. Keep the original Ninja Adventure art separate; do not mix the two perspectives without deliberate conversion. See `assets/README.md` and `assets/source-notes/VERIFIED_IMPORT.md` for exact source, license, and QA records.

The previously discussed LimeZu Modern Interiors and Zerie Tiny RPG Character packs are not part of the installed starter library. They remain optional candidates only; do not substitute them without confirming the exact version and license for public browser-game delivery.

## Environment: the laboratory

### Room identity

- One large, enclosed, modern laboratory room.
- Predominantly white and very light neutral surfaces.
- Pixel-art walls, floor, trim, doors, windows, and architectural details.
- Subtle cool accents (such as pale blue, muted teal, or soft gray) may reinforce the laboratory theme.
- Small props and equipment can make the room feel lived-in, but must not clutter the combat floor.
- The room should read as a coherent space being observed, not as a framed arena floating on a plain page.

### Composition

- The boss occupies the central area and is the primary focal point.
- The cloning machine is in the bottom-right area and must remain visually distinct.
- Warriors need clear floor space to emerge, move, gather, and fight.
- Background props should sit behind the action and must not compete with the boss or machine.
- Preserve enough negative space for the tiny characters to remain legible on an iPhone screen.

The environment may be assembled from tiles or layered room assets, but tile seams, inconsistent perspective, and mismatched scale must be avoided.

## Cloning machine

The machine is a signature object and should be more visually elaborate than ordinary room props.

- Clearly recognizable as a cloning/production device.
- Designed to fit naturally into the modern lab interior.
- Positioned bottom-right in the room composition.
- Has a readable chamber or output area where a new warrior can visibly appear and emerge.
- Its active state should be communicated through restrained lights, screen indicators, chamber glow, or mechanical motion.
- Upgrade interaction should be visually associated with the machine.

The machine animation should communicate a sequence: activation → chamber/process effect → clone appears → output/release → clone steps into the room. Keep the sequence short enough that production feels satisfying during repeated idle play.

## Bosses

- Bosses are substantially larger than the tiny warriors and should dominate the center of the room.
- Use distinct silhouettes, palettes, and visual motifs so progression feels meaningful.
- Keep bosses stylistically compatible with the pixel-art environment and character assets.
- Boss health and combat feedback must remain readable without covering important parts of the boss.
- Defeat animation should clearly communicate the end of the encounter and leave room for the reward/next-boss transition.

## Warriors / clones

- Warriors are tiny 2D pixel-art RPG-style characters.
- Each unlocked clone type should be recognizable at the actual on-screen scale, not only when enlarged.
- Distinguish types through silhouette, weapon, outfit, palette, or other strong visual cues.
- Preserve each asset's original pixel proportions and intended palette.
- Avoid smoothing, blur, fractional scaling, or CSS filters that muddy pixel edges.
- Characters should be visually grounded on the room floor, with consistent scale and orientation.
- If a pack supplies directional or animation frames, use the correct frames rather than stretching or mirroring in ways that break weapon/handedness details.

## Animation language

Animations should be brief, readable, and charming.

Priority animation beats:

1. Cloning machine activation and production.
2. Clone appearing inside the machine/chamber.
3. Clone emerging and entering the room.
4. Warrior walking toward the boss.
5. Warrior attack and hit feedback.
6. Boss taking damage or reacting.
7. Boss defeat/death.
8. Reward and next-boss arrival.

Use small anticipation and follow-through where the source sprites support it. Avoid excessive screen shake, large flashes, particles, or effects that obscure the pixel characters. Animation timing should not block the idle simulation or make rapid production feel unresponsive.

## Pixel-art rendering rules

- Use crisp pixel rendering (for example, `image-rendering: pixelated` where appropriate).
- Scale sprites by integer multiples where practical.
- Avoid fractional transforms and resampling that soften pixel edges.
- Do not apply hue shifts, blanket recoloring, or CSS filters to character sprites as a shortcut for creating new clone types. Prefer distinct source sprites or carefully authored palette variants that preserve important details.
- Keep outlines, shadow direction, lighting, and pixel density consistent across assets.
- Do not mix high-resolution smooth illustrations with pixel-art assets in the same scene.

## UI visual direction

The UI should feel like part of a friendly laboratory management game.

- Compact, readable pixel-inspired panels and buttons.
- Light surfaces and restrained outlines that fit the white lab.
- Clear hierarchy for currency, boss health, production stats, and upgrade costs.
- Machine upgrades should be easy to scan and tap on a phone.
- Keep UI decoration subordinate to the room and combat.
- Avoid modern SaaS/dashboard styling, oversized gradients, glassmorphism, or heavy card stacks.
- Use pixel fonts only where they remain legible at iPhone sizes; prioritize readability over novelty.

## Asset handling and attribution

For every external asset pack, maintain a record containing:

- Asset/pack name.
- Creator or studio.
- Exact itch.io product URL.
- Downloaded version or date obtained.
- License name and relevant terms.
- Whether commercial use is allowed (even if the game is initially a personal project).
- Required attribution wording and where it must appear.
- Any edits made to the original files.

Keep source assets organized and avoid overwriting originals. Store edited/exported game-ready assets separately where practical. Include credits in the repository (for example, `ASSET_CREDITS.md`) once the exact packs and terms have been verified.

Do not commit assets whose license is unclear or incompatible with public GitHub hosting and the intended distribution.

## Visual quality checklist

Before approving a visual change, verify:

- [ ] The scene still reads as a bright, modern pixel-art laboratory.
- [ ] The boss remains the central focal point and fills most of the white containment platform.
- [ ] The cloning machine remains in the bottom-right and easy to identify.
- [ ] Warriors are small but readable at iPhone portrait scale.
- [ ] Sprite edges remain crisp with no blur or unwanted recoloring.
- [ ] Props do not obstruct the combat path or important controls.
- [ ] Machine and combat animations are understandable and do not obscure gameplay.
- [ ] UI remains legible and does not overwhelm the room.
- [ ] All external assets have verified source and license information.

## Change control

Read this document before visual or animation work. Update it whenever the approved art direction, asset sources, rendering rules, or attribution requirements change. Product behavior and gameplay rules belong in `SOURCE_OF_TRUTH.md`.


## Installed starter asset library

### Ninja Adventure — Pixel-Boy and AAA

- **Product page:** https://pixel-boy.itch.io/ninja-adventure-asset-pack
- **Public source repository:** https://github.com/pixel-boy/NinjaAdventure
- **License:** CC0 1.0 Universal, stated on the product page.
- **Included local files:** `assets/warriors/ninja-blue.png`, `assets/warriors/samurai-blue.png`, `assets/lab/interior-floor-tiles.png`, and `assets/lab/interior-wall-tiles.png`.
- **Perspective:** Four-direction, 3/4-view, 16×16-grid character art. Keep directions and frame order intact.
- **Status:** Selected files copied into the project and committed. This is a small starter subset, not the full 89 MB itch.io archive.

### Sci-Fi RTS — Kenney

- **Source:** https://kenney.nl/assets/sci-fi-rts
- **License:** CC0 1.0, verified in the source mirror's metadata.
- **Included local file:** `assets/lab/scifi-console.png`.
- **Status:** One 64×64 structure/console sprite installed as a lab fixture reference. Build the room itself from coherent interior floor/wall pieces and original room detailing; do not stretch this object into a floor tile.

### Monster Builder Pack — Kenney

- **Source:** https://kenney.nl/assets/monster-builder-pack
- **License:** CC0 1.0, verified in the source mirror's metadata.
- **Included local components:** `assets/bosses/components/` (body, eyes, arms, legs, horn, mouth).
- **First composition:** `assets/bosses/first-boss.svg` layers the local components into a static first-boss base image.
- **Status:** Component art installed. The assembled base is not a complete animated boss; add in-game idle/hit/defeat motion and dedicated boss variations as the game develops.

### Rendering and integration notes

- Use `image-rendering: pixelated` / nearest-neighbor sampling for raster assets.
- Do not apply smoothing, fractional scaling, hue shifts, or blanket filters to warrior sprite sheets.
- Slice Ninja Adventure character sheets using their original directional/frame layout; do not render the whole sheet as one character.
- Treat the Monster Builder components as aligned full-canvas layers. Keep their source dimensions and layer order when composing a boss.
- The first room should remain bright and predominantly white; use the sci-fi object as a small fixture, not as the entire art direction.
- All local assets are documented in `assets/README.md`. Credit is not required under the recorded CC0 licenses, but preserve the source links.

### Deferred candidates

- LimeZu Modern Interiors: https://limezu.itch.io/moderninteriors
- Zerie Tiny RPG Character Asset Pack 01 V2.0: https://zerie.itch.io/tiny-rpg-character-asset-pack

These were user-identified candidate packs earlier in planning, but were not downloaded or integrated for this free starter set. Revisit only after confirming the precise archive and the license terms for public GitHub Pages asset delivery.


## Verified free expansion packs — archives received and inspected (2026-11-08)

The user supplied all three ZIP archives. Their contents, source documentation, and licenses were inspected. All PNG files in the three archives opened successfully; the Larchrow QA reports were also checked.

### Laboratory — Free Pixel Sci-Fi Tileset (16x16), reodesuxz
- Product: https://reodesuxz.itch.io/free-pixel-sci-fi-tileset-16x16
- Supplied archive: `Pixel_Sci-Fi_Tileset_v1.0.zip`
- 191 archive entries, including 169 valid PNGs. The pack README describes 83 top-down 16×16 tiles/sprites, with native PNGs, 4× PNGs, a 160×144 spritesheet + JSON, and a sample scene.
- License inspected: personal and commercial use permitted; modification permitted; attribution not required (credit appreciated); no standalone redistribution/resale.
- The pack includes white, steel, blue, green, and other floor/wall options plus lab props such as terminals, cryo pod, medbed, reactor core, pipes, and lamps.

### Clone roster — 16x16 Characters & Monsters, Larchrow
- Product: https://larchrow.itch.io/larchrow-16x16-characters-monsters
- Supplied archive: `larchrow-16x16-characters-monsters.zip`
- 267 archive entries, including 186 valid PNGs. Contains 8 heroes/NPCs and 10 monsters, 122 animations and 356 frames, with 16×16 strips, per-character sheets, combined sheet, and CSV/JSON animation indexes.
- The included QA report states all checks passed: 32-colour palette, binary alpha, closed outlines, non-empty/non-static frames, consistent strips/sheets/indexes, and Godot 4.3 validation.
- License inspected: royalty-free for commercial and non-commercial games/apps/videos; modification permitted; attribution appreciated but not required; no resale or redistribution as an asset pack.

### Boss roster — 16x16 Boss Monsters, Larchrow
- Product: https://larchrow.itch.io/larchrow-16x16-boss-monsters
- Supplied archive: `larchrow-16x16-boss-monsters.zip`
- 351 archive entries, including 315 valid PNGs. Contains 14 bosses (7 at 32×32 and 7 at 48×48), 95 animations and 432 frames, telegraphs, HP-bar art, nine-slice UI, and CSV/JSON indexes.
- The included QA report states all checks passed: 32-colour palette, binary alpha, 16px-grid sizing, 466 indexed tiles, animation completeness, and Godot/Tiled validation.
- License inspected: royalty-free for commercial and non-commercial games/apps/videos; modification permitted; attribution appreciated but not required; no resale or redistribution as an asset pack.

### Chosen integration direction
- Use the top-down 16×16 sci-fi lab and Larchrow packs together; the Larchrow character and boss art share the same 32-colour palette.
- Keep the older Ninja Adventure 3/4-view assets as an alternate set, not mixed into the top-down scene.
- Preserve native pixel dimensions, frame order, original palette, and nearest-neighbour rendering.
- A curated, engine-neutral import bundle was prepared as `Clone-Lab-Idle-verified-assets.zip` for the selected asset folders and their frame metadata. It contains no game code.
- **Repository status (updated 2026-11-08):** the selected PNG assets and animation indexes are committed in the repository, and `index.html` contains the playable browser implementation. The imported source assets remain preserved separately from game code.



## Effects — Free Effect and Bullet 16x16

- **Creator:** BDragon1727.
- **Source:** https://bdragon1727.itch.io/free-effect-and-bullet-16x16
- **License:** Free for non-commercial games; modifications are allowed. The creator requests a contribution of any value for commercial game use. Do not resell or redistribute the pack as a standalone asset.
- **Imported source:** Four 576×208 PNG atlases (Fire, Green, Purple, Water), each arranged on a 16×16 grid.
- **Repository location:** `assets/effects/effect-and-bullet-16x16/`.
- **Credit:** BDragon1727 — Free Effect and Bullet 16x16.
- **Status:** Imported and wired into the browser game. The game loads the four palette atlases and draws selected 16×16 source cells with nearest-neighbour rendering. Current uses: Knight melee impact, Mage spell projectile, Archer projectile, boss attack impact, and cloning-machine production/replacement burst. Preserve source palettes; the authored frame map is `assets/effects/effect-and-bullet-16x16/animation-map.json`.
- **Clone emergence (2026-11-08):** Every newly produced clone and every clone restored from a saved roster receives an individual water-palette emergence burst at the machine output point. Multi-clone bursts are staggered by 85 ms; the effect is displayed at 52 px for 620 ms with a brief scale pulse, while the separate larger machine-production burst remains intact. The seven-frame water sequence is recorded as `cloneSpawn` in `animation-map.json` and rendered with nearest-neighbour sampling.
- **Formation correction (2026-11-08):** Clones retain their assigned concentric orbit slots around the boss. Crowd separation influences their travel path but is limited near the destination; temporary boss knockback is corrected back toward the assigned slot. Each clone travels from the machine output point instead of being snapped directly into formation. Boss clearance and room bounds remain enforced.
- **Import record:** `docs/asset-import/effect-and-bullet-16x16/IMPORT_MANIFEST.md`.


## UI — Complete UI Essential Pack (Free / Flat Theme), Crusenho

- **Product:** https://crusenho.itch.io/complete-ui-essential-pack
- **Imported archive:** `Complete_UI_Essential_Pack_Free.7z`
- **Theme used:** Flat Theme.
- **License:** Creative Commons Attribution 4.0 International (CC BY 4.0). Commercial use and modifications are permitted with attribution; include a link to the license and indicate changes.
- **Repository location:** `assets/ui/complete-ui-essential-pack-free/Complete_UI_Essential_Pack_Free/01_Flat_Theme/`.
- **Import record:** `docs/asset-import/complete-ui-essential-pack-free/IMPORT_MANIFEST.md`.
- **Attribution:** Crusenho — Complete UI Essential Pack. Modified/imported for Clone Lab Idle. https://creativecommons.org/licenses/by/4.0/
- **Pixel-integrity correction (2026-11-08):** UI frame, slot, and button sprites use nine-slice rendering so their original pixel corners and borders retain their native proportions instead of being stretched across controls. Canvas health bars use nine-slice drawing. Decorative banner plates behind standalone text (room label, toast, helper note, and activity log) are removed so labels sit cleanly on the interface. Do not stretch small UI sprites with `background-size: 100% 100%` or direct non-uniform canvas scaling.\n- **Integration (2026-11-08):** Flat-theme sprites now skin the complete visible interface: top HUD, currency display frame, specimen/clone status panels, room viewport frame, room label, helper note, cloning-machine upgrade sheet, upgrade slots, purchase and close buttons, activity log/input panel, toast notifications, boss name banner, boss health bar/fill, and low-health clone bars. Fourteen UI sprites are preloaded from the preserved Flat Theme source folder. The UI stylesheet was rebuilt rather than layered over the former generic styling; legacy rounded-card borders, shadows, system-font declarations, and inline UI styling were removed. The game-room art and character sprites remain their existing approved assets. The room simulation, clone formation, and combat logic are not changed by this UI pass.


## Font — Pixels, Ayden Snider

- **Font:** Pixels by Ayden Snider (DaFont bitmap / 16 px category).
- **Source:** https://www.dafont.com/pixels.font
- **License:** Free for personal use only, as stated on the DaFont listing. Do not use in a commercial release without obtaining the creator's commercial permission/license.
- **Repository location:** `assets/fonts/Pixels.ttf` (extracted from the user-supplied `pixels.zip`).
- **Integration:** Loaded locally with `@font-face` and used for HTML interface text and canvas-rendered labels. No external font service is required.

- **Upgrade access update (2026-11-08):** upgrade controls are opened with a dedicated UPGRADES button anchored at the bottom-left of the laboratory viewport. The button uses the existing Flat Theme nine-slice button sprite and pressed-state sprite. Tapping the cloning machine itself no longer opens the upgrade panel.
