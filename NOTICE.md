# Notice

*(Español: [NOTICE.es.md](NOTICE.es.md))*

## Not affiliated

This is an unofficial, noncommercial fan project. It is **not affiliated with, endorsed by or
connected to Capcom or Arika**, or any of their subsidiaries, nor to the authors of the
[PSXRecomp](https://github.com/RetroPortingToolKit/psxrecomp) framework or of the
[game project](https://github.com/strider973/Street-Fighter-EX2-Plus-Recompiled) this mod runs
on. *Street Fighter*, *Street Fighter EX2 Plus* and all related names, characters and marks are
the property of their respective owners, and are used here only to identify the game this mod
is compatible with.

Nothing here is for sale, and nothing here is monetized.

## What this repository does not distribute

No ROM. No disc image. No BIOS. No built executable. No patched disc image. No art, audio,
music or font data from the game. Playing requires **your own legally obtained copy** of the
game and a working build of the game project, neither of which this repository provides or can
provide. On its own, nothing here produces a playable game.

## What it does contain of the original work

A declarative patch package, and nothing else. Each of its 979 patches states the **bytes it
expects to find** at an offset before it writes anything — that guard is what makes the package
refuse to apply to the wrong dump instead of corrupting it. Those quoted bytes come to
**23,330 bytes in total**, and they are interface strings: `MODE SELECT`, `PRACTICE`,
`VITALITY` and the like. No executable code, no art, no audio.

The package also records the disc's **SHA-256**, which is a fingerprint rather than content,
and is what binds each patch to the correct edition of the game.

The screenshots under `docs/images/` are here to document **what the mod changes**: every one of
them shows translated interface, which is the work itself, and the game's art is the background
it unavoidably sits on. The rule applied is that a screenshot earns its place by showing the
work — so the title screen, which is mostly Capcom's logo and trademark and shows nothing this
mod did, is not here. What remains is still the property of its respective owners.

## Takedown and contact

If you hold rights in this material and want something here removed or changed, write to
**jajdpmail@gmail.com**, saying what you object to and in what capacity you are writing.

Requests from rights holders are honoured: the disputed part is removed, or the repository is
taken down, without argument, and you will get a reply confirming it. No notice or legal
process beyond that email is needed to reach the person who maintains this.
