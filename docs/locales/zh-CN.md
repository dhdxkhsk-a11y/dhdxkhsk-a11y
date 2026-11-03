| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> 资深系统软件与辅助技术（Assistive Interface）工程师。  
> 专注于低延迟操作系统无障碍抽象层、触觉盲文点字终端驱动以及确定性文本渲染引擎。

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 关于我 (About Me)

我致力于设计与实现操作系统内核输入管线与辅助输入/输出硬件交汇处的底层运行时基础设施。

我的核心工程目标是消除图形显示服务与辅助技术客户端（特别是屏幕朗读器、可刷新盲文终端和眼动/头部追踪指针设备）之间的延迟壁垒。我认为无障碍不应作为事后补救的高层 UI 补丁，它必须作为系统的基础层，基于确定性内存管理并剔除不必要的 IPC 往返开销进行架构。

在不追踪内核输入事件或编写 SIMD 加速的文本字形整形解析器时，你会发现我在焊接定制分体人体工学机械键盘、调试模拟磁带循环效果，或是骑着全地形公路车穿行于山间碎石路。

---

## 🛠️ 技术储备 (Technical Competency)

### 编程语言与运行时

| 分类 | 核心技术栈 | 探索与辅助工具 |
| :--- | :--- | :--- |
| **系统级编程** | Rust, C11, C++20 | Zig, Nim |
| **用户态与脚本** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Web 与嵌入式规范** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### 平台子系统与驱动架构

| 子系统 | 专业领域 | 关键 API 与协议 |
| :--- | :--- | :--- |
| **Linux 无障碍** | 直连 AT-SPI2 bus IPC, `evdev` 事件捕获 | D-Bus, `uinput`, Wayland accessibility 协议扩展 |
| **Windows 平台** | 原生 Windows 无障碍 (UIA/IA2) Provider 架构 | IAccessible2, WinEvents, Raw Input API |
| **macOS 无障碍** | 原生 Accessibility API 封装层 | `AXUIElement`, CoreGraphics event taps |
| **嵌入式与外设** | 盲文显示控制器直通通信 | USB HID-Telephony / 定制盲文协议, UART / BLE |

---

## 🚀 核心开源项目

### 1. `braille-bridge`
*面向可刷新盲文终端的安全无内存分配（Zero-allocation）用户态守护进程。*
- **核心栈**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- 支持通用英语盲文（UEB）与韩文计算机 8 点盲文转换表，保持亚毫秒级的微秒响应。
- 具备针对 USB HID、串口（UART）与低功耗蓝牙（BLE）的可插拔传输后端。

### 2. `subtext-engine`
*确定性字形光栅化器与超高对比度文本渲染管线。*
- **核心栈**: C11, FreeType, HarfBuzz, 纯软件光栅化器。
- 专为低视力人群深度优化：消除光晕伪影（Halo artifacts），采用次像素几何膨胀算法与用户自定义色彩分离曲线。
- 完全脱离对 GPU 的依赖，在受限的嵌入式 x86 及 ARM 硬件上保持确定性一致渲染。

### 3. `aria-lint-cli`
*针对设计系统的零运行时 AST 无障碍不变量静态分析器。*
- **核心栈**: Go, tree-sitter.
- 在组件打包前的 CI/CD 流程中，静态验证无障碍树契约、键盘捕获陷阱规避以及动态播报活跃区域（Live Regions）。

### 4. `earcon-dsp`
*用于非视觉桌面导航的空间化定向音频提示音合成器。*
- **核心栈**: Rust, `cpal`, HRTF 卷积滤波。
- 在不干扰主语音朗读（TTS）的前提下，实时生成三维声学线索与窗口边界听觉反馈。

---

## 🔬 当前研究课题

- [ ] 探索在密集 DOM 变更场景下 Wayland 无障碍树更新的零拷贝共享内存缓冲区实现。
- [ ] 针对无头屏幕朗读器，对比评估 WebAssembly SIMD 与原生 SSE4.2 文本排版算法性能。
- [ ] 制定面向消费级双单元盲文触摸板的开放规格矢量触觉图形转换引擎。

---

## 💻 工作环境与工具链

```ini
[硬件配置]
主力工作机 = Lenovo ThinkPad P1 Gen 5 (定制内存/SSD)
显示设备   = 2x 27寸 4K IPS (锁定 200% 整数无损缩放)
键盘设备   = Corne Choc Split (36键矮轴分体, Miryoku 键位布局)
音频监听   = Beyerdynamic DT 770 Pro (80Ω) + Motu M2 专业声卡

[软件环境]
操作系统   = Void Linux (基于 musl libc) / FreeBSD 14.1-RELEASE
窗口管理器 = River (Wayland 动态平铺排版合成器)
终端模拟器 = Foot / Alacritty
代码编辑器 = Neovim (纯原生手写 Lua 配置，无笨重集成框架)
Shell 环境 = Zsh + Tmux
```

---

## 📬 联系方式与公钥

- **电子邮箱**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **GPG 指纹**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*“只有当所有人都能毫无阻碍地使用它时，一款软件才算真正开发完成。”*
