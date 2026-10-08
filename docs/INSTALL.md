# Installing the Spanish mod

*(Español: [INSTALL.es.md](INSTALL.es.md))*

## Before you start

You need a PSXRecomp project for Street Fighter EX2 Plus that already runs on your machine,
and your own dump of the NTSC-U disc.

If you do not have the game running yet, that part comes from
[strider973/Street-Fighter-EX2-Plus-Recompiled](https://github.com/strider973/Street-Fighter-EX2-Plus-Recompiled),
built on the [PSXRecomp](https://github.com/RetroPortingToolKit/psxrecomp) framework. Two things
it needs that this mod cannot provide:

- **your own disc dump** (`.cue` / `.bin`), and
- **a retail SCPH-1001 BIOS** — that project sets `openbios = false`, so the bundled OpenBIOS
  will not do.

Get the game itself booting first; then come back here. Installing this package is the last
step, not the first.

The package is bound to that dump. Check yours before anything else:

```
SHA-256  f12ab8cb7a7af9599fe805f3c1405a051f22810305d2005b107c042316aa936f
```

```powershell
# Windows
certutil -hashfile "Street Fighter EX2 Plus (USA).bin" SHA256
```

```sh
# Linux / macOS
sha256sum "Street Fighter EX2 Plus (USA).bin"
```

If your digest differs, the mod will refuse to apply. See *If something looks wrong* below.

## 1. Copy the package

Two ways in, and both install the same file:

- **From the release.** Download `sfex2p.es-1.0.0.zip` from
  [the releases page](https://github.com/jajdp/sfex2p-es/releases/latest) and extract it into
  the folder that holds the game executable: the archive carries the `mods/packages/…` path
  inside, so extracting it there puts the package where it belongs. It also drops two loose
  `sfex2p.es-1.0.0-*.txt` files — a short guide and the license — which you can delete.
- **From this repository.** Copy the `mods/` folder out of a clone, or out of *Code → Download
  ZIP*.

Either way, this file has to end up next to the game executable:

```
<game folder>/mods/packages/sfex2p.es/1.0.0/manifest.toml
```

That is all: there is nothing to build and nothing to generate. Do not rename the folders —
the package id and version **are** the path, and a renamed folder makes the runtime reject the
whole catalogue, not just this package (`mods unavailable: package path does not match
manifest id/version`).

**If you build the game from source**, copy the package in **after** the build, into
`build-*/mods/packages/`. The framework stages its own built-in catalogue there and clears that
folder first, so a package copied in beforehand is wiped. (With
[sfex2p-widescreen](https://github.com/jajdp/sfex2p-widescreen) installed you can instead keep
the package in the project's own `mods/packages/`: its installer adds a post-build step that
stages that folder next to the executable, after the catalogue is written.)

## 2. Turn it on

Launch the game. In the launcher, under **Mods**, the group **Localization** now lists **Menú
en español**, enabled by default. Press **PLAY**.

![The launcher's Mods list](images/pc-lanzador-mods.png)

## 3. Check it

The title screen should read **PULSA START** and the main menu **ELIGE MODO**. Then:

| Screen | What you should see |
|---|---|
| Main menu | **ELIGE MODO**, with PRACTICA, OPCIONES and MINIJUEGOS among the entries |
| Mode list | MODO ARCADE, MODO VERSUS, ENTRENAMIENTO, MODO DESAFIO, MODO DIRECTOR |
| Before a fight | **FASE 1** in the gold arcade label, not "STAGE 1" |
| Character select | **ELIGE PERS.** in the gold label, **ELIGE LUCHADOR** as text (two different resources) |
| Versus screen | **1J** / **2J** pointers, **ENERGIA** on the bar, **00 VIC 00** on the scoreboard, **2J PRESIONE START** |
| Pause | SEGUIR JUGANDO, REPETIR, SALIR |
| Memory card | accented Spanish — that font has accents |

![The results screen in Spanish](images/pc-resultados-es.png)

## 4. Turning it off

Uncheck **Menú en español** in the launcher: the game is in English again, immediately, with
no reinstall. Saves are unaffected (`save_compatibility = "shared"`).

To remove it completely, delete the `mods/packages/sfex2p.es/` folder.

## Consoles and other UWP packaging

On a UWP build (for example an Xbox in Developer Mode) the package is not installed
separately: it is staged into the application package next to the executable and travels
inside it, and the runtime copies it to its data folder on each launch. Installing a new
application package version is what updates the translation.

## If something looks wrong

| Symptom | Cause |
|---|---|
| The feature does not appear in the launcher | The package is not next to the executable, or the folders were renamed. The path must be exactly `mods/packages/sfex2p.es/1.0.0/manifest.toml`. |
| `mods unavailable: package path does not match manifest id/version` | A package folder was renamed. This rejects **every** mod, not just the renamed one. Restore the original name. |
| `cannot launch with selected mods: package does not target this game/image: sfex2p.es` | The game is not running **your** image. Either the dump is not the NTSC-U `SLUS-01105` this package targets, or the game is pointed at a different file: pick your disc in the launcher once (it is remembered), or set `disc` in `game.toml` to your `.cue`. Booting with `--no-launcher` resolves mods *before* a `--disc` on the command line, so the path in `game.toml` is what counts there. |
| It appears but cannot be enabled | The disc digest does not match `disc_sha256`: different dump, revision or region. This package is NTSC-U `SLUS-01105` only. |
| Menus are Spanish but one screen is English | Either it is deliberate (proper nouns and drawn artwork stay English) or it is a screen that has not been walked through yet — the arcade endings are known to be unchecked. Reports welcome. |
| Accented characters missing in menus | Deliberate: the menu font has no accents and no `ñ`. The memory-card font does, and uses them. |
