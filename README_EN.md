# DLSS5 Neural Rendering Load Tool v0.15

A DLSS5 loader built for RE Engine games. It solves the problem other loaders have — they can't get the engine's native motion-vector data, which is what makes DLSSNR flicker or simply not work.

- **More stable image**: it uses the real motion vectors from the game's DLSS (the per-pixel motion information), so the effect follows the picture and flickers less.
- **Higher frame rate**: you can lower the neural-rendering internal resolution to save performance while the image stays sharp.

Tested on RE Engine games: *Onimusha: Way of the Sword Demo*, *RESIDENT EVIL requiem*, *Street Fighter 6* (SF6 has no DLSS, so it can't get motion vectors) and *Monster Hunter Wilds*. In theory other DX12 / DX11 games should work too — besides those I've only tested *Death Stranding 2* and *Tomb Raider* (DX11).

## Known issues (not yet fixed)
1. Can't run together with frame generation (neither FSRFG nor DLSSFG) — it crashes the game. If you have frame generation on, turn it off in-game before installing this mod.
2. Turning on path tracing in RESIDENT EVIL requiem (and some of my other games) prevents native motion vectors from being captured.

## Prerequisites
1. An NVIDIA RTX GPU with up-to-date drivers.
2. Install REFramework: https://github.com/praydog/REFramework
3. Install ReShade: https://www.reshade.me/#download

## Install
1. Unzip the downloaded `.zip` and put all the files next to the game's `.exe`. To find the game folder: Steam → the game → right-click → Properties → Local Files → Browse.
2. If the game folder already has `nvngx_dlss.dll` / `nvngx_dlssnr.dll`, you can skip overwriting them.
3. Launch the game.

## Usage
After you're in-game, a green toast appears bottom-left: `DLSS5 Load Mod ready` — that means the mod loaded successfully.
1. DLSS5 is on by default, with the parameters I recommend.
2. **F8** toggles the effect on/off, **F9** opens the in-game menu (rebindable). From there you can tweak DLSS5 parameters and view debug info.
3. If the in-game menu shows `motion: zero`, it means native motion vectors couldn't be captured — the tool fell back to the zero-vector path.
4. The **NR Scale** parameter changes the DLSSNR resolution. It only affects DLSSNR's performance and how much detail it adds — it does not affect image sharpness. Lowering it noticeably reduces performance cost.
5. Hover over any option for a specific description.

For Onimusha, try my ColorCorrection mod: https://www.nexusmods.com/onimushawayofthesword/mods/23

## Conflicts with other tools?
- If another mod also uses `version.dll`: rename this tool's `version.dll` (e.g. to `winmm.dll`); keep the other two files with the same names in the same folder.
- If another tool/mod uses an import slot other than `version.dll` (`dxgi.dll` / `dinput8.dll`, etc.), this tool automatically skips the names that are already taken — `RE_DLSS5_Core_settings.json` is the only config file name this tool uses, and it never reads or writes another tool's `settings.json`.

## What if the game has no DLSS?
If the game doesn't support DLSS, or DLSS is off in-game, the tool automatically falls back to "zero-vector" mode: everything still works, but moving content may flicker a little because there's no motion information. That's expected, and it will never crash. Enable DLSS in-game for the best result.

## A small note
While the settings panel is open, **Alt-Tabbing or another graphics mod popping up its UI** may cause an occasional flicker — a harmless overlay quirk that doesn't affect DLSS5 itself. Press **F9** to close and reopen the panel once and it goes away.

---
© LCPD15 / LCPD拉灯
Bilibili: https://space.bilibili.com/885387
