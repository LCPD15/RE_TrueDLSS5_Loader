# DLSS5 神经渲染加载工具

🌍 [English](./README.md) | **简体中文**

即插即用 DLSS5 / DLSSNR 加载器。支持帧生成、原生矢量的，理论上兼容大部分dx12/dx11游戏
视频：https://www.bilibili.com/video/BV1FDtz6SEXF
https://www.bilibili.com/video/BV1AubL6WEKe

## 特性

- **真运动矢量** — 直接读取游戏 DLSS 自带的运动数据，时间降噪跟着画面走，不再闪烁。
- **帧数更高** — 可调低神经渲染的内部分辨率省性能，画面依然清晰。
- **零配置** — 把文件解压到游戏 `.exe` 旁即可，进游戏默认开启 DLSS5，参数已调成推荐值。
- **游戏内菜单** — 不用退出游戏就能调所有参数、查看 debug 信息。
- <img width="4096" height="2160" alt="image" src="https://github.com/user-attachments/assets/b922778a-3d6e-4612-961a-fa8e3cfa08d0" />
- <img width="2677" height="1506" alt="image" src="https://github.com/user-attachments/assets/459a24ee-18bd-4652-a0af-f277ebe79c58" />

## 前置要求

1. **NVIDIA RTX** 显卡 + 最新驱动。
2. **[REFramework](https://github.com/praydog/REFramework-nightly)** — RE 引擎游戏必装。
3. **[ReShade](https://www.reshade.me/#download)**。— RE 引擎游戏必装，其他游戏只装RE_TrueDLSS5_Loader也行。

## 安装

1. 解压 release 压缩包，把**所有文件**放到游戏 `.exe` 旁（Steam → 游戏 → 右键 → 属性 → 本地文件 → 浏览）。
2. 若游戏目录已有 `nvngx_dlss.dll` / `nvngx_dlssnr.dll`，可不覆盖。
3. 启动游戏。左下角弹绿色 `DLSS5 Load Mod ready` 即加载成功。

## 使用

- **F8** — 开关 DLSS5 效果。
- **F9** — 呼出游戏内菜单（两个快捷键都可重绑）。
- 菜单里 `motion: zero` 表示没拿到原生矢量，走了零矢量兜底路径（游戏没有 DLSS 时属正常）。
- 鼠标悬停任一选项有具体说明。

## 参数说明

| 参数 | 范围 | 作用 |
|---|---|---|
| **Inputs（输入源）** | Native / Zero | 输入源 — Native 用游戏 DLSS 的真深度+运动矢量；Zero 用空缓冲做安全兜底。 |
| **Preset（档位）** | 0–4 | 神经网络模型档位，调整细节重建与时间稳定的平衡（0 = 偏质量默认档）。 |
| **Style（风格）** | Default / Natural / Cinematic | 神经渲染的整体观感。 |
| **Intensity（强度）** | 0.0–1.0 | 神经增强整体强度；0 = 原画面，1 = 完整效果。 |
| **Local Tone（色调）** | 0.0–2.0 | 低频细节：大范围光照与色彩响应。 |
| **Local Structure（结构）** | 0.0–2.0 | 高频细节：环境光遮蔽、接触阴影、反射、次表面散射。 |
| **Skin Strength（皮肤强度）** | 0.0–1.0 | 皮肤专属增强（自然次表面散射）。 |
| **Auto Mask（自动遮罩）** | 开/关 | 语义 AI 遮罩，让增强只作用于预设目标区域。 |
| **UI Correction（UI 修正）** | 开/关 | 排除界面区域，保持 UI/HUD/文字清晰。 |
| **NR Render Scale（内部分辨率）** | 0.5–1.0 | 神经渲染内部计算分辨率；降低省性能但更柔和。 |
| **Debug view（调试视图）** | Off / Depth / Motion / Encoded / Diff | 叠加显示滤镜输入/输出的可视化。 |

## 支持游戏

已测试：

- 鬼武者（Onimusha: Way of the Sword）
- 生化危机9（RESIDENT EVIL requiem）
- 街霸6（Street Fighter 6）
- 怪物猎人荒野（Monster Hunter Wilds）

其它 DX12 / DX11 游戏理论上也能用（另测过：死亡搁浅2、古墓丽影）。

## 已知问题

1. **无法和游戏内帧生成同时使用**（FSRFG / DLSSFG 都不行）：已经修复
2. **路径追踪**：生化危机9 及部分游戏开路径追踪后拿不到原生矢量。： 已经修复


## 游戏没有 DLSS 怎么办？

工具会自动走零矢量兜底：功能照常，但动态画面可能轻微闪烁。想要最好效果就在游戏里打开 DLSS。

## 相关

- 鬼武者色彩修复 mod：https://www.nexusmods.com/onimushawayofthesword/mods/23
- 怪猎荒野色彩修复 mod：https://www.nexusmods.com/monsterhunterwilds/mods/341

---

© LCPD15 · Bilibili：https://space.bilibili.com/885387
