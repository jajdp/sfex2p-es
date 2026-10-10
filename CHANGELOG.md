# Changelog

All notable changes to this mod. Dates are `YYYY-MM-DD`.

## [1.0.1] — 2026-10-10

A code-review pass over the three repositories of this project. Nothing about the translation
itself changed: the 979 patches are byte for byte what 1.0.0 shipped.

### Changed

- `LICENSE` now carries the **canonical** PolyForm Noncommercial 1.0.0 text from
  polyformproject.org — the one the `PolyForm-Noncommercial-1.0.0` identifier names. The copy
  shipped before was an abridged variant missing *Distribution License*, *Notices*, *Changes and
  New Works License* and *Patent License*, which are the sections that grant a recipient the right
  to share and build on this.
- The manifest's header now says where the file comes from, that the generator stays in the
  private project, and how to ask for a wording change.
- One shared `.gitignore` across the three repositories, with the strictest protection of the
  three. The two mod repositories were missing `*.BIN` and `SCPH*` — the BIOS — which Windows
  hides because git matches case-insensitively there, but a clone on Linux does not.

## [1.0.0] — 2026-10-08

First public release: 302 strings, 979 guarded patches (938 to the disc, 41 to the
executable). Walked through screen by screen on Windows and on an Xbox Series in Developer
Mode.

### Added

- Spanish for the title and loading screens, the main menu and its submenus, game and sound
  options, the memory card, the database, the ranking, the results screen and the pause menus
  of both a match and training.
- The complete versus screen: **1J** / **2J** pointers and health-bar plates, **ENERGIA** on
  the bar, **00 VIC 00** on the scoreboard and **2J PRESIONE START**.
- Two gold arcade labels redrawn from the game's own letters: **FASE 1** (instead of
  "STAGE 1") and **ELIGE PERS.** (instead of "PLAYER SELECT").
- A launcher toggle (**Mods → Localization → Menú en español**), on by default, with shared
  save compatibility.

### Notes

- Fighter, stage, music and move names stay in English, as does the drawn scoreboard jargon
  and **CP** for the CPU side. See [docs/TRANSLATION.es.md](docs/TRANSLATION.es.md).
- The arcade endings have not been walked through: English text may remain there.

### Documentation, same day

Verified from scratch on a clean machine — game cloned and built from source, disc and BIOS
supplied by the tester, package installed from this repository alone — and the install guide
corrected with what that run exposed:

- where the game project itself comes from, and that it requires a retail SCPH-1001 BIOS;
- what `package does not target this game/image` actually means, and how to fix it;
- that renaming a package folder rejects the whole mod catalogue, not just that package;
- where the package goes when the game is built from source.

Published as a release: `sfex2p.es-1.0.0.zip` carries the package in its own install path, so
extracting it next to the game executable is the whole install, plus a short bilingual guide
and the license.
