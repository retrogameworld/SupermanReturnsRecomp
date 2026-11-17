# Superman Returns (Xbox 360) - Native PC Static Recompilation

**Superman Returns: The Video Game** (Xbox 360, EA Tiburon, 2006) running natively on Windows through **static recompilation**. It is not an emulator.

The game's original PowerPC code is translated ahead of time into native x64 code, built on the ReXGlue recompilation SDK. The Xbox 360 graphics run on a **Direct3D 12** renderer, so the game runs like a normal PC program. That makes room for things the original never could do: 4K, 120 fps, flying into space, and much more.

> **This repository contains information only.** It holds no source code, no builds and no game files. You need your own legally owned copy of the game. Nothing from the game is included or distributed here.

## Status

- **Playable from start to finish**, with music, sound, controller support and saves.
- Runs at **native 4K, locked at 120 fps** on an RTX 5080 (about 70% GPU load).
- Work in progress: more native D3D12 rendering, to help older PCs. See [STATUS.md](STATUS.md).

## Highlights

- Up to **4K** and **120 fps / uncapped**. The original 30 Hz game logic is smoothly interpolated, so game speed and physics stay correct.
- **Cape fix:** no more flicker or tearing. **Cape smoothing** keeps it fluid at high frame rates.
- **Fly into space:** the sky turns into space as you climb, with a cloud deck and the Earth below.
- **No invisible wall:** the hard fog wall at the edge of the world is replaced by natural haze, with a short white-out when you cross the mountains.
- **Save anywhere**, **cutscene skip**, **PlayStation or Xbox button prompts**, and a full in-game **PC SETTINGS** menu.
- Optional cheats: fast flight up to **50x**, a damage multiplier, fast forward, and the game's own cheats.

The full list is in [FEATURES.md](FEATURES.md). How it works is in [HOW_IT_WORKS.md](HOW_IT_WORKS.md).

## Credits

- **ReXGlue** recompilation SDK; **XenonRecomp**, used as a fallback.
- **Xenia / Xenia Canary**, the reference for correct Xbox 360 behaviour. The GPU layer is derived from it.
- The Xbox 360 homebrew and preservation community.

## Disclaimer

This is a fan preservation project and is not affiliated with or endorsed by Electronic Arts, Warner Bros., DC or Microsoft. *Superman* and all related characters and marks are trademarks of their respective owners. No copyrighted game data is distributed.
