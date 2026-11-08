# Clone Lab Idle — Art Source & Visual Direction

> Canonical visual and asset guide. Read this document before creating, replacing, or substantially modifying visual assets, animations, layout styling, or character presentation.

## Art direction summary

Clone Lab Idle is a **2D pixel-art laboratory simulation** with the friendly, compact charm of Kairosoft-style management games.

The room should look like a clean, modern research laboratory rendered in warm, carefully detailed pixel art. The visual contrast is intentional: a bright, orderly white lab containing a growing crowd of tiny, expressive fantasy/RPG warriors fighting oversized bosses.

The game should feel cute, readable, lively, and handcrafted—not sterile corporate software, not gritty science fiction, and not a generic fantasy battle screen.

## Intended asset sources

The planned visual foundation is:

1. **Modern Interiors** — the intended itch.io pixel-art environment/interior asset pack for the laboratory room, furnishings, and lab details.
2. **Tiny RPG Character** — the intended itch.io pixel-art character asset pack for the small warrior characters and related character animation material.

The exact itch.io product pages, creators, included files, and license terms must be verified and recorded before assets are committed. Do not guess URLs, creators, or license permissions. Confirm whether each pack permits the intended use in a publicly hosted browser game, whether attribution is required, and whether redistribution of source files is restricted.

If either intended pack cannot provide a required element, choose a visually compatible asset or create original pixel art. Do not silently substitute a different visual style.

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
- [ ] The boss remains the central focal point.
- [ ] The cloning machine remains in the bottom-right and easy to identify.
- [ ] Warriors are small but readable at iPhone portrait scale.
- [ ] Sprite edges remain crisp with no blur or unwanted recoloring.
- [ ] Props do not obstruct the combat path or important controls.
- [ ] Machine and combat animations are understandable and do not obscure gameplay.
- [ ] UI remains legible and does not overwhelm the room.
- [ ] All external assets have verified source and license information.

## Change control

Read this document before visual or animation work. Update it whenever the approved art direction, asset sources, rendering rules, or attribution requirements change. Product behavior and gameplay rules belong in `SOURCE_OF_TRUTH.md`.


## Identified itch.io packs (not yet installed)

The following exact product pages have been identified for the intended art sources:

### Modern Interior - RPG Pack [32x32] — MarzoDev

- **Product page:** https://marzodev.itch.io/interior-modern-asset-pack
- **Format / scale:** Transparent PNG props, 32px.
- **Free tier:** 12 props.
- **Paid tier:** Full pack; the product page lists an additional 15-assets ZIP at a $1 minimum payment.
- **License distinction:** The free pack is stated to be for personal use, with editing and game-development use allowed. The paid full pack is stated to allow personal or commercial use, with editing and game-development use allowed. Both prohibit redistribution/resale of the assets.
- **Integration status:** Identified only; not downloaded or installed. Confirm the purchased/downloaded archive contents before integration.

### Tiny RPG Character Asset Pack 01 V2.0 — Zerie

- **Product page:** https://zerie.itch.io/tiny-rpg-character-asset-pack
- **Contents:** 22 animated characters, 100×100 pixel tiles, idle, walk, attack, hurt, death, shield-block animations where applicable, selected summoning animations, projectile sprites, and an Aseprite source file.
- **Full pack:** The page lists the full 22-character v2.0 ZIP at a $2.50 minimum payment.
- **Free sample:** The free ZIP is limited to Soldier and Orc; it is not the full roster.
- **License:** Personal and commercial video game use and modification are allowed. Redistribution, resale, or re-upload of the assets (modified or unmodified) is prohibited. Credit is appreciated but not required.
- **Integration status:** Identified only; not downloaded or installed. Confirm the downloaded archive is the full v2.0 pack, not the free sample or an older version.

### Acquisition and integration checklist

- [ ] Obtain the full intended version of each pack.
- [ ] Verify archive contents and version after download.
- [ ] Preserve original source files; create separate game-ready exports.
- [ ] Inspect sprite sheets, animation frame order, transparency, and scale.
- [ ] Integrate only the assets needed for the room and initial clone roster.
- [ ] Keep asset credits/license notes consistent with the exact downloaded versions.

