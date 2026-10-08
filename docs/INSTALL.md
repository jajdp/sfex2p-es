# Installing the Spanish mod

*(Español: [INSTALL.es.md](INSTALL.es.md))*

## Before you start

You need a PSXRecomp project for Street Fighter EX2 Plus that already runs on your machine,
and your own dump of the NTSC-U disc.

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

Copy the folder so that this file ends up next to the game executable:

```
<game folder>/mods/packages/sfex2p.es/1.0.0/manifest.toml
```

That is all: there is nothing to build and nothing to generate. Do not rename the folders —
the package id and version are the path.

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
| It appears but cannot be enabled, or the game refuses to launch | The disc digest does not match `disc_sha256`. Different dump, different revision or a different region: this package is NTSC-U `SLUS-01105` only. |
| Menus are Spanish but one screen is English | Either it is deliberate (proper nouns and drawn artwork stay English) or it is a screen that has not been walked through yet — the arcade endings are known to be unchecked. Reports welcome. |
| Accented characters missing in menus | Deliberate: the menu font has no accents and no `ñ`. The memory-card font does, and uses them. |
