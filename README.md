# Kukoo Modpack — Config Tuning

Tuned configuration files for the **Kukoo** CurseForge modpack
(Forge `36.2.34`, Minecraft `1.16.5`). Goal of the pack: exploration with
**frequent enemy-filled dungeons**, fewer boring decorative structures, and
controlled mob spawning.

## Install — read this carefully

There is **only one folder to copy: `config/`**. Do **not** copy anything else
(not the `reference/` folder, not `README.md`).

1. Download/clone this repo.
2. Open the repo's **`config/`** folder and select everything **inside** it
   (the `.toml` / `.properties` files **and** the `castle_dungeons/` and `idas/`
   subfolders).
3. Paste it into your modpack's config folder, overwriting when asked:
   `<CurseForge>/Instances/Kukoo/config/`
4. **Stop here.** Do not also copy the per-mod folders — that's the mistake that
   breaks it (it creates ignored junk folders like `config/when-dungeons-arise/`).
5. Fully close and restart CurseForge + Minecraft.

> Structure changes only appear in **newly generated chunks** — explore fresh
> terrain (or a new world) to see them. Already-explored areas won't change.
>
> Requires the same pack: Forge `36.2.34`, Minecraft `1.16.5`, with these mods
> installed. It only changes config values, not which mods you have.

### If you already pasted the wrong folders (cleanup)

Inside your `Kukoo/config/` folder, delete any of these mod-named folders if they
appear there (they don't belong in `config/` and do nothing):
`when-dungeons-arise/`, `dungeons-enhanced/`, `dungeons-mod/`, `rl-structures/`,
`awesome-dungeon-nether/`, `castle-dungeons/`, `battle-towers/`, `lycanites-mobs/`,
`greek-fantasy/`, plus any stray `README.md`. **Keep** `castle_dungeons/` (with an
underscore) and `idas/` — those are real.

## Repo layout

- **`config/`** — the only thing you copy. Mirrors the game's exact config layout.
- **`reference/`** — the same files grouped by mod, for browsing/review only.
  **Never copy this.**

The table below shows where each changed file lives inside `config/`.

## Files & where they belong

| File | Path inside `config/` |
|---|---|
| `when-dungeons-arise-common.toml` | `when-dungeons-arise-common.toml` |
| `dungeons_enhanced-common.toml` | `dungeons_enhanced-common.toml` |
| `dungeonsmod-common.toml` | `dungeonsmod-common.toml` |
| `rlstructures-common.toml` | `rlstructures-common.toml` |
| `awesomedungeonnether_1.properties` | `awesomedungeonnether_1.properties` |
| `config.cfg` (Castle Dungeons) | `castle_dungeons/config.cfg` |
| `idas.toml` | `idas/idas.toml` |
| `ba-battletowers-config.toml` | `ba-battletowers-config.toml` |
| `lycanitesmobs-common.toml` | `lycanitesmobs-common.toml` |
| `greekfantasy-common.toml` | `greekfantasy-common.toml` |

## Summary of changes

- **Dungeons (combat/explore) boosted** — When Dungeons Arise, Dungeons Enhanced,
  IDAS, Castle Dungeons, Battle Towers, Awesome Dungeon Nether: spacing reduced so
  enemy dungeons (castles, forts, towers, temples, mazes, mines, asylums) generate
  more often. For each, only the combat structures were boosted; decorative filler
  was left at vanilla.
- **Dungeons Mod** — its structures (the_castle, the_catacombs, the_lab, etc.)
  boosted to ~3–4× vanilla so its bosses (King, Princess, Malevolent Observer,
  Iron Slime) are findable, then eased back from an over-dense first pass.
- **Decorative clutter reduced** — RL Structures' `wild_*` rock/decor pieces made
  far sparser (its actual dungeons kept); IDAS desert houses/markets/camps/statues
  made sparser; Dungeons Enhanced tower-types (Watch/Witch/Undead Tower, Tall Witch
  Hut) pushed below default after they spammed.
- **Greek Fantasy structures** reduced below the mod's (dense) defaults — biggest
  cut on `arachne_pit` (82→16), shrines/camps/dens/caves roughly halved.
- **Lycanites Mobs spawning cut** via `lycanitesmobs-common.toml`:
  `spawnWeightScale = 0.1`, `typeSpawnLimit = 3`.

## Note on Lycanites spawner JSONs

Per-spawner files (`config/lycanitesmobs/spawners/*.json`) are **not** tracked here:
Lycanites regenerates them from its internal defaults on each world load, so edits
to them do not persist. Effective Lycanites spawn control is done through
`lycanitesmobs-common.toml` (the global `spawnWeightScale` / `typeSpawnLimit`),
which is included.

## Config rule of thumb

- Structure mods use **spacing** / **separation** (in chunks): **lower = more
  frequent**. `separation` must stay below `spacing`. Some mods (Dungeons Enhanced)
  also have an `offset` that must stay below `spacing`.
- IDAS uses `…AverageChunkDistance`: lower = more frequent.
- Greek Fantasy `features` use `chance` (0–1000): higher = more frequent.
