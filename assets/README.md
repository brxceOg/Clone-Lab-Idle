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
