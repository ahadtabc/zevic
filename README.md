# ZEVIC — Ambient Screen Edge Glow (Windhawk Mod)

[![GitHub](https://img.shields.io/badge/GitHub-Repository-181717?style=flat-square&logo=github)](https://github.com/ahadtabc/zevic)
[![Windhawk Mod](https://img.shields.io/badge/Windhawk-Mod%20v1.1.0-00D2FF?style=flat-square&logo=cplusplus)](https://github.com/ahadtabc/zevic/blob/main/Windhawk/Zevic.wh.cpp)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg?style=flat-square)](https://github.com/ahadtabc/zevic/blob/main/LICENSE)
[![Creator](https://img.shields.io/badge/Creator-Abdul%20Ahad-0A66C2?style=flat-square&logo=linkedin)](https://www.linkedin.com/in/abdul-ahadit)

**File**: [`Zevic.wh.cpp`](Zevic.wh.cpp)  
**Target Process**: `explorer.exe`  
**License**: MIT  
**Author**: Abdul Ahad  
**Repository**: [https://github.com/ahadtabc/zevic](https://github.com/ahadtabc/zevic)  

---

## 📖 Introduction

`Zevic.wh.cpp` is a native, hardware-synchronized Windows shell mod built for the [Windhawk](https://windhawk.net/) customization engine. Inspired by Sony Bravia cinema displays and AMOLED perimeter edge lighting, ZEVIC renders smooth, luminous orbiting light streaks along the screen edges of all connected displays.

Because it runs directly inside `explorer.exe` using a dedicated background thread and 32-bit pre-multiplied alpha (`PixelFormat32bppPARGB`) DIBSections submitted to the Windows Desktop Window Manager (`UpdateLayeredWindow`), it delivers **silky-smooth 60 FPS animation with zero lag, zero process clutter, and zero window management overhead**.

---

## ⚡ Quick Start

| Action | Shortcut / Default |
| :--- | :--- |
| **Toggle On / Off** | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>Z</kbd> |
| **Default Theme** | Sony Bravia Cyan (`#00D2FF` Electric Blue) |
| **Default Speed** | 8.0 seconds per loop |
| **Master Edge Inset** | `-3 px` (pre-calibrated for a seamless bezel-flush fit) |
| **Default Direction** | Clockwise |

---

## ✨ Features

- **11 Curated Color Presets**:
  - `sony_bravia_cyan`: Sony Bravia Cyan (Default `#00D2FF`)
  - `pure_white`: Pure White (`#FFFFFF`)
  - `rgb`: RGB Rainbow dynamic flow
  - `cyberpunk`: Cyberpunk Neon (`#E040FB`)
  - `amoled_gold`: AMOLED Gold (`#FFB800`)
  - `plasma_violet`: Plasma Violet (`#8A2BE2`)
  - `emerald_neon`: Emerald Neon (`#00FFA3`)
  - `ice_blue`: Ice Blue (`#A0E7FF`)
  - `warm_white`: Warm White (`#FFECCD`)
  - `rose_gold`: Rose Gold (`#FFB6C1`)
  - `amber`: Subtle Amber (`#FFA040`)
  - `custom`: 24-bit Custom RGB channels
- **360° Chromatic Continuous Hue Glide**: Continuous automated color flow around the entire HSV color wheel with customizable speed (seconds per full rotation).
- **Multi-Beam Orbit Dynamics**: Run 1 (Single), 2 (Dual opposite), 3 (Triangle), or 4 (Cross) simultaneous beams.
- **Clockwise & Anti-Clockwise**: Instantly change orbit direction.
- **Dual-Pass Halo & Taper**: Core streak head with soft atmospheric halo blur and smooth optical tail decay.
- **Sharp & Rounded Corner Styles**: Switch between crisp 90° rectangular AMOLED corners and rounded curves with custom pixel radius.
- **Bezel & Taskbar Calibration**: Master edge inset (`-3 px` default) plus 4 independent edge offsets (Top, Bottom, Left, Right).
- **Subtle Ambient Base Line**: Persistent faint perimeter boundary line (customizable opacity & thickness).
- **Automatic Multi-Monitor Support**: Spawns overlays across all monitors and handles dynamic screen topology changes (`WM_DISPLAYCHANGE`).
- **Fullscreen 3D Game / App Auto-Pause**: Automatically hides and stops rendering when a fullscreen 3D game or app is running.
- **Power Intelligence / Battery Saver**: Dynamically throttles to 30 FPS on laptop battery, keeping 60 FPS on AC / desktop power.
- **Zero Distraction & Click-Through**: Passes all mouse events through (`WS_EX_TRANSPARENT`), never takes keyboard focus (`WS_EX_NOACTIVATE`), and stays locked above the taskbar.

---

## 🛠️ How to Compile & Install in Windhawk

1. Open **Windhawk**.
2. Navigate to **Developer Channel** or click **Create New Mod**.
3. Set the Mod details:
   - **Mod ID**: `zevic-ambient-edge-illumination`
   - **Name**: `ZEVIC — Ambient Screen Edge Glow`
   - **Target**: `explorer.exe`
4. Copy the entire content of [`Zevic.wh.cpp`](Zevic.wh.cpp) and paste it into the Windhawk code editor.
5. In the mod's **Settings / Advanced** or compiler configuration, verify the linker flags:
   ```text
   -lgdi32 -ldwmapi -luser32 -lgdiplus -lshlwapi -lole32 -lshell32
   ```
6. Click **Compile Mod** -> **Install Mod**.
7. Once installed, ZEVIC will immediately start glowing along your screen edges!

---

## ⚙️ Settings Reference

| Option | Key | Type | Default | Details |
| :--- | :--- | :---: | :---: | :--- |
| **Enable Glow** | `enabled` | Bool | `true` | Master on/off switch (<kbd>Ctrl+Shift+Z</kbd>). |
| **Color Preset** | `colorPreset` | String | `sony_bravia_cyan` | Choice of 11 curated themes or `custom`. |
| **Continuous Hue Glide** | `colorCycle` | Bool | `false` | Smooth 360° chromatic color flow. |
| **Hue Cycle Speed** | `colorCycleSpeedSec` | Int | `10` | Seconds for a complete 360° color wheel rotation. |
| **Beams** | `illuminationBeams` | String | `single` | `single` (1), `dual` (2), `triple` (3), or `quad` (4). |
| **Direction** | `direction` | String | `clockwise` | `clockwise` or `anticlockwise`. |
| **Rotation Speed** | `speedSec` | Int | `8` | Seconds for one full perimeter loop. |
| **Master Edge Inset** | `edgeInset` | Int/Float| `-3` | Inset in pixels (`-3` gives zero bezel gap). |
| **Beam Length** | `sparkLength` | Int | `80` | Length of glowing head streak in pixels. |
| **Beam Thickness** | `sparkThickness` | Int | `3` | Stroke width in pixels (1–10). |
| **Glow Halo Spread** | `sparkGlowBlur` | Int | `15` | Atmospheric halo glow spread. |
| **Tail Multiplier** | `tailMultiplier` | Int | `25` | Tail length ratio relative to head (25 = 2.5×). |
| **Tail End Fade** | `tailFadeEnd` | Int | `0` | Opacity % at tail tip (0 = fully faded). |
| **Brightness** | `sparkBrightness` | Int | `100` | Brightness percentage (1–100). |
| **Corner Style** | `cornerStyle` | String | `sharp` | `sharp` (90° joints) or `rounded`. |
| **Corner Radius** | `cornerRadius` | Int | `0` | Radius in pixels when `rounded`. |
| **Edge Offsets** | `edgeOffsetTop/Bottom/Left/Right` | Int | `0` | Independent border alignment in pixels. |
| **Show Base Line** | `showBaseLine` | Bool | `true` | Static ambient screen border line. |
| **Base Line Opacity** | `baseLineOpacity` | Int | `8` | Opacity percentage (default 8%). |
| **Base Line Thickness** | `baseLineThickness`| Int | `2` | Stroke thickness in pixels (default 2px). |
| **Pause in Fullscreen** | `hideInFullscreen` | Bool | `false` | Auto-pauses in fullscreen 3D games and apps. |
| **Battery Saver** | `batterySaverAware` | Bool | `true` | 30 FPS on laptop battery, 60 FPS on AC. |
| **Custom RGB** | `color.red`, `green`, `blue` | Int | `0, 210, 255` | Custom RGB color channels (0–255). |

---

## 🔗 Links

- **GitHub Repository**: [https://github.com/ahadtabc/zevic](https://github.com/ahadtabc/zevic)
- **Author**: **Abdul Ahad** ([LinkedIn Profile](https://www.linkedin.com/in/abdul-ahadit))

