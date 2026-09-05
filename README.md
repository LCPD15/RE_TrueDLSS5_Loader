# DLSS5 Neural Rendering Load Tool

🌍 **English** | [简体中文](./README_ZH.md)

A drop-in **DLSS5 / DLSSNR** loader built for **RE Engine** games. Other loaders can't read the engine's native motion-vector data, which is exactly what makes DLSSNR flicker or do nothing — this one can.

## Features

- **Real motion vectors** — taps into the game's own DLSS motion data, so the temporal pass follows the scene instead of flickering.
- **Higher frame rate** — lower the neural-render internal resolution to save GPU time while the image stays sharp.
- **Zero config** — drop the files next to the game's `.exe` and launch; DLSS5 is on by default with recommended settings.
- **In-game menu** — tweak every parameter and view debug info without leaving the game.
- <img width="4096" height="2160" alt="image" src="https://github.com/user-attachments/assets/b922778a-3d6e-4612-961a-fa8e3cfa08d0" />



## Requirements

1. An **NVIDIA RTX** GPU with up-to-date drivers.
2. **[REFramework](https://github.com/praydog/REFramework)** — required for RE Engine games.
3. **[ReShade](https://www.reshade.me/#download)**. — The RE engine game is a must-have. For other games, you only need to install RE_TrueDLSS5_Loader. You can also install them together.

## Install

1. Unzip the release archive and put **all files** next to the game's `.exe` (Steam → game → right-click → Properties → Local Files → Browse).
2. If the game folder already has `nvngx_dlss.dll` / `nvngx_dlssnr.dll`, you can skip overwriting them.
3. Launch the game. A green `DLSS5 Load Mod ready` toast bottom-left means it loaded.

## Usage

- **F8** — toggle DLSS5 on/off.
- **F9** — open the in-game menu (both hotkeys are rebindable).
- If the menu shows `motion: zero`, native motion vectors weren't captured (zero-vector fallback — normal when the game has no DLSS).
- Hover any option for a description.

## Parameters

| Parameter | Range | What it does |
|---|---|---|
| **Inputs** | Native / Zero | Input source — native depth + motion captured from the game's DLSS, or empty buffers as a safe fallback. |
| **Preset** | 0–4 | Neural model weight set; tunes detail recovery vs. temporal stability (0 = quality-leaning default). |
| **Style** | Default / Natural / Cinematic | Overall look of the neural pass. |
| **Intensity** | 0.0–1.0 | Overall strength of the enhancements; 0 = original frame, 1 = full effect. |
| **Local Tone** | 0.0–2.0 | Low-frequency detail: broad lighting and colour response. |
| **Local Structure** | 0.0–2.0 | High-frequency detail: ambient occlusion, contact shadows, reflections, subsurface scattering. |
| **Skin Strength** | 0.0–1.0 | Skin-specific enhancement (natural subsurface scattering). |
| **Auto Mask** | on/off | Semantic AI mask — limits enhancement to the intended targets. |
| **UI Correction** | on/off | Keeps UI / HUD / text crisp by excluding interface regions from the pass. |
| **NR Render Scale** | 0.5–1.0 | Internal compute resolution of the neural pass; lower = cheaper but softer. |
| **Debug view** | Off / Depth / Motion / Encoded / Diff | Overlay a live view of the filter inputs / output. |

## Supported games

Tested on:

- Onimusha: Way of the Sword
- RESIDENT EVIL requiem
- Street Fighter 6
- Monster Hunter Wilds

Other DX12 / DX11 games should work in theory (also tested: Death Stranding 2, Tomb Raider).

## Known issues

1. **Not compatible with frame generation** (FSRFG / DLSSFG) — it crashes the game. Disable FG in-game before installing.
2. **Path tracing** in RESIDENT EVIL requiem (and some others) blocks native motion-vector capture.

## What if the game has no DLSS?

The tool falls back to zero-vector mode automatically — everything still works, but moving content may flicker a little. Enable DLSS in-game for the best result.

## Related

- Onimusha ColorCorrection: https://www.nexusmods.com/onimushawayofthesword/mods/23
- Onimusha RE_TrueDLSS5_Loader: https://www.nexusmods.com/onimushawayofthesword/mods/32
- ColorCorrection_MonsterHunterWilds: https://www.nexusmods.com/monsterhunterwilds/mods/341

---

© LCPD15 · Bilibili: https://space.bilibili.com/885387
