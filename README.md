# Street Fighter EX2 Plus — Spanish menus

A Spanish localization of *Street Fighter EX2 Plus* (PlayStation, 1999, `SLUS-01105`) for the
[PSXRecomp](https://github.com/RetroPortingToolKit/psxrecomp) static recompilation, shipped as a **declarative mod
package**: 302 strings, 979 guarded patches, no modified disc image and no patched executable.
It switches on and off in the launcher.

*(Español — la versión completa: [README.es.md](README.es.md))*

![The main menu in Spanish](docs/images/pc-menu-es.png)

## What is translated

- Title and loading screens, the main menu and its submenus, game and sound options, the
  memory card, the database, the ranking, the results screen and the pause menus of both a
  match and training.
- **The versus screen**, in full: the grid pointers and the health-bar plates read **1J** and
  **2J**, the bar reads **ENERGIA**, the scoreboard **00 VIC 00** and the second-player prompt
  **2J PRESIONE START**.
- The two gold arcade labels, **redrawn from the game's own letters** so they match the
  original artwork: **FASE 1** instead of "STAGE 1" before each fight, and **ELIGE PERS.**
  instead of "PLAYER SELECT".

![The versus screen in Spanish](docs/images/pc-versus-es.png)

What stays in English: fighter, stage and move names (proper nouns, most of them drawn as
artwork), the scoreboard jargon (HIT, DAMAGE, TOTAL…), and **CP** for the CPU side — it reads
just as well in Spanish.

The menu font has no accents and no `ñ`: accents are folded (`PRACTICA`), and words needing
`ñ` were rephrased rather than mangled. The memory-card font does have them, and uses them.
See [docs/TRANSLATION.es.md](docs/TRANSLATION.es.md) (Spanish).

## How it works

A `format_version = 5` declarative package. Each patch states the original bytes it expects
and is bound to the disc's SHA-256:

- **938 patches to the disc** (`target = "disc_user"`), because this game keeps its UI strings
  as plain ASCII inside the per-screen modules it loads from disc, and reloads them on every
  screen. The stock image is **not** rewritten: the runtime resolves these into a sparse
  overlay at load time.
- **41 patches to the executable** (`target = "main_exe"`), applied in RAM before the entry
  point, for the boot and button-config messages.

If the disc is not the one the package was built for, nothing is applied — it fails safe
rather than corrupting anything.

## What this repository is not

It contains **no game code, no disc image, no BIOS and no built executable**. You need your
own legally dumped copy of the game and a working PSXRecomp project for it. What is here is a
patch: the bytes to change and the bytes each change expects to find.

## Install

Download the **[latest release](https://github.com/jajdp/sfex2p-es/releases/latest)** and
extract it into your game project, next to the executable. The archive already carries the
folder structure, so that is the whole install:

```
mods/packages/sfex2p.es/1.0.0/manifest.toml
```

Copying that same folder straight out of this repository works just as well — it is the same
file. Then launch the game and enable **Menú en español** under **Mods → Localization**. Step
by step, including consoles, in **[docs/INSTALL.md](docs/INSTALL.md)**.

![The launcher's Mods list](docs/images/pc-lanzador-mods.png)

## Related

- [sfex2p-widescreen](https://github.com/jajdp/sfex2p-widescreen) — real 16:9 for the same
  game, with the stage backdrop actually drawn out to the edges. Independent of this mod; they
  work together.

## Status

Played through on Windows and on an Xbox Series in Developer Mode, screen by screen.

Also verified from scratch on 2026-10-08, using nothing but this repository and the game's own:
the game built from source, this package dropped in, and the title screen reading **PULSA
START** on first boot.

Known gaps: the arcade endings have not been walked through yet, so English text may remain
there.

## Credits and license

Translation and tooling by **Recompilaciones**. Released under the
[PolyForm Noncommercial License 1.0.0](LICENSE), matching the license of the PSXRecomp
framework it runs on.

*Street Fighter EX2 Plus* is © Capcom / Arika. This project is not affiliated with them, with
Sony, or with the PSXRecomp author, and it distributes nothing that belongs to them.
