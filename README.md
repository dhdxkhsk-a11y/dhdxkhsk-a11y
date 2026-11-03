| [KR 한국어](./docs/locales/ko.md) | [US English](./README.md) | [JP 日本語](./docs/locales/ja.md) | [CN 简体中文](./docs/locales/zh-CN.md) | [ES Español](./docs/locales/es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./docs/locales/fr.md) | [DE Deutsch](./docs/locales/de.md) | [RU Русский](./docs/locales/ru.md) | [BR Português](./docs/locales/pt-BR.md) | [SA العربية](./docs/locales/ar.md) |

---

# Min (@dhdxkhsk)

> Systems Software & Assistive Interface Engineer.  
> Focusing on low-latency OS accessibility abstractions, tactile refreshable braille drivers, and deterministic text rendering engines.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 About Me

I design and build runtime infrastructure where operating systems meet assistive input/output hardware. 

My primary engineering focus centers on closing the latency gap between graphical display servers and assistive technology clients—specifically screen readers, refreshable braille terminals, and head-tracking pointing devices. I believe accessibility should never be treated as an afterthought or a high-level UI patchwork; it belongs in the systems layer, built with deterministic memory management and zero unnecessary IPC hops.

When I am not tracing kernel input events or writing SIMD-accelerated text shape parsers, you will find me soldering custom split ergonomic keyboards, experimenting with analog tape loops, or bikepacking along gravel backroads.

---

## 🛠️ Technical Competency

### Languages & Runtimes

| Category | Primary Technologies | Secondary / Exploring |
| :--- | :--- | :--- |
| **Systems Programming** | Rust, C11, C++20 | Zig, Nim |
| **Userland & Scripting** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Web & Embedded Standards** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### Platform Subsystems & Driver Architectures

| Subsystem | Specialization | Key APIs & Protocols |
| :--- | :--- | :--- |
| **Linux Accessibility** | Direct AT-SPI2 bus IPC, `evdev` event tap | D-Bus, `uinput`, Wayland accessibility protocol extensions |
| **Windows Platform** | Native UI Automation (UIA) provider architecture | IAccessible2, WinEvents, Raw Input API |
| **macOS Accessibility** | Native Accessibility API wrappers | `AXUIElement`, CoreGraphics event taps |
| **Embedded & Peripherals** | Braille display controller communication | USB HID-Telephony / Custom Braille Protocol, UART / BLE |

---

## 🚀 Key Open-Source Projects

### 1. `braille-bridge`
*A memory-safe, zero-allocation userland daemon for refreshable braille displays.*
- **Core Stack**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- Implements translation tables for Unified English Braille (UEB) and Korean 8-dot Computer Braille at sub-millisecond conversion latency.
- Features pluggable transport backends for USB HID, Serial (UART), and Bluetooth LE.

### 2. `subtext-engine`
*Deterministic glyph rasterizer and high-contrast text rendering pipeline.*
- **Core Stack**: C11, FreeType, HarfBuzz, Software Rasterizer.
- Optimized for extreme low-vision rendering: zero halo artifacts, custom subpixel geometric expansion, and user-defined color separation curves.
- Zero GPU dependency required; runs deterministically on constrained embedded x86 and ARM platforms.

### 3. `aria-lint-cli`
*Zero-runtime AST accessibility invariant analyzer for design systems.*
- **Core Stack**: Go, tree-sitter.
- Statically verifies accessibility tree contracts, keyboard trapping invariants, and dynamic announcement live-regions directly inside CI/CD pipelines before bundling.

### 4. `earcon-dsp`
*Spatialized directional audio cue synthesizer for non-visual desktop navigation.*
- **Core Stack**: Rust, `cpal`, HRTF convolution filters.
- Generates 3D acoustic breadcrumbs and boundary feedback without interfering with primary speech synthesizers.

---

## 🔬 Current Research & Exploration

- [ ] Implementing zero-copy memory buffers for Wayland accessibility tree updates under heavy DOM mutations.
- [ ] Benchmarking WebAssembly SIMD vs native SSE4.2 text layout algorithms for headless screen readers.
- [ ] Developing open-spec tactile vector graphic converters for consumer dual-cell refreshable braille pads.

---

## 💻 Workstation & Tooling

```ini
[Hardware]
Machine   = Lenovo ThinkPad P1 Gen 5 (Custom RAM/SSD)
Displays  = 2x 27" 4K IPS (Running locked 200% Integer Scaling)
Keyboard  = Corne Choc Split (Low-Profile 36-key, Miryoku Layout)
Audio     = Beyerdynamic DT 770 Pro (80 Ohm) + Motu M2 Audio Interface

[Software]
Operating System = Void Linux (musl libc variant) / FreeBSD 14.1-RELEASE
Window Manager   = River (Wayland dynamic tiling compositor)
Terminal         = Foot / Alacritty
Editor           = Neovim (Hand-rolled Lua configuration, zero bloated frameworks)
Shell            = Zsh + Tmux
```

---

## 📬 Connect & Verification

- **Email**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk](https://github.com/dhdxkhsk)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **GPG Fingerprint**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*“Software is truly finished only when every single person can operate it without friction.”*
