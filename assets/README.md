# Clone Lab Idle — starter art library

Selected original PNG assets are stored locally in this repository so the browser game can load them without third-party hotlinks. All included packs are CC0 1.0 / public-domain equivalent, allowing use, modification and redistribution, including in public and commercial games.

## Included assets

- `warriors/ninja-blue.png`, `warriors/samurai-blue.png`: 4-direction 3/4-view RPG character sheets from Ninja Adventure.
- `lab/interior-floor-tiles.png`, `lab/interior-wall-tiles.png`: interior floor and wall tiles from Ninja Adventure. These are starter interior tiles, not a finished laboratory by themselves.
- `lab/scifi-console.png`: one 64×64 sci-fi structure sprite from Kenney's Sci-Fi RTS pack, suitable as a small room fixture.
- `bosses/components/`: modular body, eyes, arms, legs, horn and mouth layers from Kenney's Monster Builder Pack. These are source components, not a finished animated boss.

## Perspective and rendering

The selected warrior art is 16×16-grid, four-direction, 3/4-view. This establishes a top-down/3/4 room camera for the initial art pipeline. Use nearest-neighbor rendering; do not blur or hue-shift the character sheets.

## Sources and licenses

### Ninja Adventure — Pixel-Boy and AAA
- Product: https://pixel-boy.itch.io/ninja-adventure-asset-pack
- Public source repository: https://github.com/pixel-boy/NinjaAdventure
- License: CC0 1.0 Universal, as stated on the itch.io product page.
- Included: two warrior sheets and two interior tile sheets.

### Sci-Fi RTS — Kenney
- Source: https://kenney.nl/assets/sci-fi-rts
- CC0 mirror metadata: https://github.com/Tiddybub/2d-assets/tree/main/sci-fi/sci-fi-rts
- License: CC0 1.0, recorded in the mirror's SOURCE.md and License.txt.
- Included: one sci-fi console/structure sprite.

### Monster Builder Pack — Kenney
- Source: https://kenney.nl/assets/monster-builder-pack
- CC0 mirror metadata: https://github.com/Tiddybub/2d-assets/tree/main/characters/monster-builder-pack
- License: CC0 1.0, recorded in the mirror's SOURCE.md and License.txt.
- Included: selected modular components for assembling boss appearances.

Credit is not required for these CC0 assets, but links are retained for provenance. The full Ninja Adventure itch.io download contains a much larger roster than the subset currently installed here.


## Next free asset downloads (selected, pending)

The following three archives are the preferred expansion set for the first playable lab/warrior/boss scene. They are not in this repository yet; do not reference them from game code until the user supplies the ZIPs and the contents/frame maps are inspected.

1. **Lab:** [Free Pixel Sci-Fi Tileset (16x16)](https://reodesuxz.itch.io/free-pixel-sci-fi-tileset-16x16) — `Pixel_Sci-Fi_Tileset_v1.0.zip`, 121 KB, 83 top-down 16×16 tiles/props, includes white floors/walls and lab machinery.
2. **Warriors:** [16x16 Characters & Monsters](https://larchrow.itch.io/larchrow-16x16-characters-monsters) — `larchrow-16x16-characters-monsters.zip`, 1.4 MB, 8 four-directional heroes and 10 animated monsters.
3. **Bosses:** [16x16 Boss Monsters](https://larchrow.itch.io/larchrow-16x16-boss-monsters) — `larchrow-16x16-boss-monsters.zip`, 2.4 MB, 14 larger bosses with idle/attack/hurt/death/enraged animations and frame metadata.

These three packs are a stronger perspective match for one another than combining the 3/4-view Ninja Adventure sheets with a top-down room. The existing Ninja Adventure starter assets remain available as a separate 3/4-view prototype set; don't mix both perspectives in one scene without deliberate conversion.

**Next step:** download the three free $0 ZIPs from itch.io and attach them to the chat. After inspection, place selected lab art in `lab/`, character art in `warriors/`, boss art in `bosses/`, and keep required frame maps/metadata in `source-notes/`. Keep original archive names and source notes in the import record.
