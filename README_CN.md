# DLSS5 Neural Rendering Load Tool v0.15

MOD简介： 
针对 RE 引擎制作的 DLSS5 加载器，解决其他加载器无法获取 RE 引擎原生运动矢量数据导致的 DLSSNR 闪烁或者不生效的问题。
- **画面更稳定**：能用上游戏 DLSS 里的真矢量（画面运动方向信息），增强效果会跟着画面走，不容易闪烁。
- **帧数更高**：可以调低神经渲染的内部分辨率来省性能，画面依然清晰。
已经测试鬼武者、生化危机9、街霸6（街霸无DLSS所以无法获取矢量）、怪猎荒野等RE引擎游戏，理论上其他DX12 DX11游戏也能用，我只测试过死亡搁浅2和古墓丽影(DX11）

**********暂时未修复BUG****************
1.无法和帧生成同时开启（FSRFG/DLSSFG都不行），会导致游戏崩溃，如果开了请先在游戏里关掉再装mod
2.生化危机9和我其他游戏开启路径追踪后会无法获取原生矢量

前置要求：
1.显卡是 NVIDIA RTX，驱动更新到最新。
2.安装reframework：https://github.com/praydog/REFramework
3.安装reshade：https://www.reshade.me/#download

安装方法： 
1.把下载的.zip 压缩包内的文件解压，找到游戏安装目录，把文件都放到游戏的.exe 启动文件旁。可以通过 steam > 游戏 > 右键 > 浏览本地目录 找到游戏安装目录
2.如果游戏目录已经存在nvngx_dlss.dll\nvngx_dlssnr.dll，可以不覆盖。
3.启动游戏即可。

使用方法：
进游戏后左下角会弹绿色提示 `DLSS5 Load Mod ready`表示mod加载成功。
1.进入游戏默认开启DLSS5，默认参数是我推荐的参数。
2.默认按F8开关效果，按F9呼出游戏内菜单，可以修改快捷键。可以调整dlss5参数和查看debug信息。
3.如果游戏内菜单motion显示zero，则表示没能没能获取到原生矢量，走的是零矢量路径。
4.NR Scale参数可以调整DLSSNR的分辨率，只影响DLSSNR的性能和添加的细节程度，不影响画面清晰度。降低可以显著降低性能消耗
5.鼠标悬停会有具体的参数说明

鬼武者可以试试我的色彩修复mod一起用：https://www.nexusmods.com/onimushawayofthesword/mods/23


会不会和别的工具冲突：
- 万一别的 mod 也用了 `version.dll`：把本工具的 `version.dll` 改个名（比如 `winmm.dll`），另外两个文件别改名、放同一目录即可。
- 万一别的工具/mod 用了 `version.dll` 以外的其它导入槽（`dxgi.dll`/`dinput8.dll` 等），本工具会自动跳过已被占用的名字——`RE_DLSS5_Core_settings.json` 是唯一配置名，不会去读写别的工具的 `settings.json`。

游戏没有 DLSS 怎么办：
游戏不支持 DLSS、或游戏里没开 DLSS 时，工具会自动用"零矢量"兜底：功能照常，但因为少了运动信息，动态画面可能有点闪烁，属于正常现象，不会崩溃。想要最好效果就在游戏设置里打开 DLSS。

## 一个小提醒
开着设置面板时，**切换窗口（Alt-Tab）或别的画质 mod 弹出界面**，画面偶尔会闪一下——这只是叠加层的偶发小问题，不影响 DLSS5 本身。按 **F9** 把面板关掉再打开一次就恢复。

---
© LCPD15 / LCPD拉灯
@bilibili：https://space.bilibili.com/885387