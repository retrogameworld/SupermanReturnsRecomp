# Status & Roadmap

_Last updated: 2026-11-17_

## Working
- Full game, start to finish, with music, sound, cutscenes, saves and controller support.
- 4K at a locked 120 fps on a high-end PC, with lower resolutions and presets for weaker PCs.
- All the features in [FEATURES.md](FEATURES.md).

## Known issues
- In rare heavy city views (about 3,000+ draws per frame) the frame rate can dip below 120 fps at 4K. The CPU side of the graphics layer is the limit there.
- Seen from out at sea, the distant mountain silhouettes can show faint double edges.

## In progress: native Direct3D 12 for older PCs
The game already renders through Direct3D 12 on the GPU. What is still emulated is the work around it: the Xbox 360 GPU command stream, its on-chip render-target memory (EDRAM), and the per-frame copies between surfaces. That overhead hurts older PCs most.

Planned and prepared steps, each behind a switch and checked to be pixel-identical before it is enabled:
1. **Native image output:** frames are presented straight from the render target, without an extra copy.
2. **Exact-size render targets:** much less video memory, which matters for 3-4 GB cards.
3. **Smoother frame delivery** on a separate present thread, with an optional even 120 fps on 240 Hz screens.
4. **Less CPU work per draw**, the main limit on 4-core CPUs.

Research done for later:
- Ahead-of-time compilation of all 237 game shaders to native D3D12 shaders.
- Turning about half of the 30 render-target copies per frame into free views.
- True fractional render scales, such as real 1080p.
- A direct hook of the game's own D3D calls: its draws go through four library functions, so they can be intercepted cleanly.
