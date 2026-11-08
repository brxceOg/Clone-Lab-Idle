# Effect and Bullet 16x16 — import manifest

- **Creator:** BDragon1727
- **Source:** https://bdragon1727.itch.io/free-effect-and-bullet-16x16
- **Source archive:** `Effect and Bullet 16x16.rar`
- **Imported folder:** `assets/effects/effect-and-bullet-16x16/`
- **License:** Free for non-commercial games; modification is allowed. For commercial game use, the creator asks users to contribute any value. Do not resell or redistribute the asset pack as a standalone asset.
- **Credit:** BDragon1727 — Free Effect and Bullet 16x16

The archive contains four palette variants. Each source PNG is a 576×208 atlas arranged on a 16×16 grid (36 columns × 13 rows). The source pixels are preserved; no resizing, recoloring, or resampling was performed during import.

| Variant | File | Dimensions | Grid |
|---|---|---:|---:|
| Fire | `Effect and Bullet 16x16/Fire Effect and Bullet 16x16.png` | 576×208 | 36×13 |
| Green | `Effect and Bullet 16x16/Green Effect and Bullet 16x16.png` | 576×208 | 36×13 |
| Purple | `Effect and Bullet 16x16/Purple Effect and Bullet 16x16.png` | 576×208 | 36×13 |
| Water | `Effect and Bullet 16x16/Water Effect and Bullet 16x16.png` | 576×208 | 36×13 |

**Integration status:** The four atlases are loaded by `index.html`. The game currently uses palette-specific effects for Knight melee impacts (Fire), Mage spell shots (Purple), Archer shots (Water), boss attack impacts (Green), and cloning-machine production/replacement (Water). Source rectangles remain 16×16 and are scaled with canvas smoothing disabled. The source pack did not include animation metadata; the project's authored coordinate selections and timings are recorded in `assets/effects/effect-and-bullet-16x16/animation-map.json`.
