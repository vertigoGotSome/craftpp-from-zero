# Game assets

Place original textures and assets licensed for redistribution under `assets/`. Record third-party sources and license terms in [Third-party notices](../THIRD_PARTY_NOTICES.md).

Start with 16 × 16 PNG tiles and lowercase snake_case filenames. Save source tiles separately so a future renderer can decide how to pack or upload them.

| Block | Texture files in `textures/blocks/` |
| --- | --- |
| Grass block | `grass_top.png`, `grass_side.png`, `dirt.png` |
| Rough stone | `rough_stone.png` |
| Wood planks | `wood_planks.png` |

Use an original grass silhouette, stone pattern and plank layout. The grass block uses a separate texture for its top, sides and bottom. Rough stone and planks can use one tile per block for the first scene.

Keep editable drafts and local reference material under the ignored `work/assets/` directory. The game asset directory is for runtime-ready files.
