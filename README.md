# Kukoo Modpack — Config Tuning

Tuned configuration files for the **Kukoo** CurseForge modpack
(Forge `36.2.34`, Minecraft `1.16.5`). Goal of the pack: exploration with
**frequent enemy-filled dungeons**, fewer boring decorative structures, and
controlled mob spawning.

## Install (for a friend — easiest)

Copy **everything inside the `config/` folder of this repo** into your instance's
`config/` folder, overwriting when asked:

```
<CurseForge>/Instances/Kukoo/config/
```

The `config/` folder mirrors the game's exact layout (root files + the
`castle_dungeons/` and `idas/` subfolders), so it works right away — no manual
placement needed. Then fully restart CurseForge + Minecraft. Note: structure
changes only show up in **newly generated chunks**, so explore fresh terrain.

> Requires the same pack: Forge `36.2.34`, Minecraft `1.16.5`, with these mods
> installed. It only changes config values, not which mods you have.

## Repo layout

- **`config/`** — ready-to-deploy mirror of the instance `config/` directory (use this).
- **Per-mod folders** (`when-dungeons-arise/`, `idas/`, …) — the same files grouped
  by mod for easy browsing/review. Reference only; don't copy these directly.

Each per-mod folder contains the config file(s) we changed under their **original
filenames**; the table below shows where each maps inside `config/`.

## Files & where they belong

| Folder | File | Goes to (`<instance>/config/…`) |
|---|---|---|
| `when-dungeons-arise/` | `when-dungeons-arise-common.toml` | `when-dungeons-arise-common.toml` |
| `dungeons-enhanced/` | `dungeons_enhanced-common.toml` | `dungeons_enhanced-common.toml` |
| `dungeons-mod/` | `dungeonsmod-common.toml` | `dungeonsmod-common.toml` |
| `rl-structures/` | `rlstructures-common.toml` | `rlstructures-common.toml` |
| `awesome-dungeon-nether/` | `awesomedungeonnether_1.properties` | `awesomedungeonnether_1.properties` |
| `castle-dungeons/` | `config.cfg` | `castle_dungeons/config.cfg` |
| `idas/` | `idas.toml` | `idas/idas.toml` |
| `battle-towers/` | `ba-battletowers-config.toml` | `ba-battletowers-config.toml` |
| `lycanites-mobs/` | `lycanitesmobs-common.toml` | `lycanitesmobs-common.toml` |
| `greek-fantasy/` | `greekfantasy-common.toml` | `greekfantasy-common.toml` |

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
