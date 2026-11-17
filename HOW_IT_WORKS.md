# How it works

## Static recompilation
The Xbox 360 executable is PowerPC code. A static recompiler (ReXGlue) turns every function of the game into C++ ahead of time, and that C++ is compiled to native x64. The result is a normal Windows program, not an emulator interpreting instructions at run time.

The recompiled game still expects an Xbox 360 around it. A runtime supplies the kernel calls, memory, threads, audio (XMA decoding) and input. The GPU work goes to a Direct3D 12 backend derived from Xenia's.

## Why fixes and new features are possible
Every game function is native code that can be replaced or wrapped. New features hook into the game's own logic:
- The settings menu.
- Save anywhere.
- The space sky.
- The fast-flight levels.

Graphics features (the cape fix, the haze, space, HD textures) recognise the game's own draws and change or add passes around them.

## Some interesting problems solved
- **Cape:** the cape flickered because of how its quads were split into triangles and how its depth was handled. A specific triangle split plus a two-pass depth bias fixed it, and smoothing interpolates its shape at 120 fps.
- **120 fps with 30 Hz logic:** the game simulation stays at its original 30 Hz. Rendering interpolates between ticks, so speed and physics stay exactly as designed.
- **Flying into space:** the original world ends at a fixed height. A "virtual altitude" keeps Superman's real position where floating-point numbers are precise, and adds the extra height for the sky and the Earth. That removes the shaking at extreme heights.
- **The edge of the world:** the original hard fog wall became a soft haze. Crossing the mountain ring uses a short white-out and a teleport, so the hollow back side of the map is never seen up close.
- **Music volume:** a bug where the music slider was saved as 0 came from how the game stores its volume. The volume is read straight from the mixer bus, so the setting has to be preserved at that level.
