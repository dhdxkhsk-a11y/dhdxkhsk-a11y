| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk)

> Systemsoftware- und Assistive-Interface-Ingenieur.  
> Spezialisiert auf latenzarme Betriebssystem-Barrierefreiheitsabstraktionen, Treiber für taktile Braillezeilen und deterministische Text-Rendering-Pipelines.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 Über mich (About Me)

Ich entwerfe und entwickle Laufzeitinfrastrukturen an der direkten Schnittstelle zwischen dem Betriebssystemkern und assistiver Ein-/Ausgabe-Hardware.

Mein technischer Schwerpunkt liegt auf der Schließung der Latenzlücke zwischen grafischen Anzeigeservern und Clients assistiver Technologien – insbesondere Screenreadern, aktualisierbaren Braille-Terminals und kopf- bzw. augengesteuerten Zeigegeräten. Barrierefreiheit darf kein nachträglicher UI-Flickenteppich sein; sie gehört als fundamentale Schicht in das System, getragen von deterministischer Speicherverwaltung und der strikten Vermeidung unnötiger IPC-Verzögerungen.

Wenn ich nicht gerade Kernel-Eingabeereignisse trace oder SIMD-beschleunigte Text-Shaping-Parser schreibe, löte ich ergonomische Split-Tastaturen, experimentiere mit analogen Tonbandschleifen oder bin mit dem Gravelbike auf Schotterpisten unterwegs.

---

## 🛠️ Technische Kompetenzen

### Programmiersprachen & Laufzeitumgebungen

| Kategorie | Primäre Technologien | Erkundung / Sekundär |
| :--- | :--- | :--- |
| **Systemprogrammierung** | Rust, C11, C++20 | Zig, Nim |
| **Userland & Skripting** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Web- & Embedded-Standards** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### Plattform-Subsysteme & Treiberarchitektur

| Subsystem | Spezialisierung | Wichtige APIs & Protokolle |
| :--- | :--- | :--- |
| **Linux-Barrierefreiheit** | Direkte AT-SPI2-Bus-IPC, `evdev`-Event-Abgriff | D-Bus, `uinput`, Wayland accessibility protocol extensions |
| **Windows-Plattform** | Native UI Automation (UIA) Provider-Architektur | IAccessible2, WinEvents, Raw Input API |
| **macOS-Barrierefreiheit** | Native Accessibility-API-Wrapper | `AXUIElement`, CoreGraphics-Event-Taps |
| **Embedded & Peripherie** | Direkte Controller-Kommunikation für Braillezeilen | USB HID-Telephony / Eigene Braille-Protokolle, UART / BLE |

---

## 🚀 Wichtige Open-Source-Projekte

### 1. `braille-bridge`
*Speichersicherer, allokationsfreier Userland-Daemon für Braillezeilen.*
- **Technologie-Stack**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- Übersetzungstabellen für Unified English Braille (UEB) und koreanische 8-Punkt-Computerbraille mit Sub-Millisekunden-Latenz.
- Modulare Transport-Backends für USB HID, serielle Schnittstellen (UART) und Bluetooth LE.

### 2. `subtext-engine`
*Deterministischer Glyphen-Rasterizer und Text-Rendering mit extrem hohem Kontrast.*
- **Technologie-Stack**: C11, FreeType, HarfBuzz, Software-Rasterizer.
- Speziell für Sehbehinderungen optimiert: keinerlei Lichthof-Artefakte (Halo), geometrische Subpixel-Expansion und frei definierbare Farbtrennungskurven.
- Vollkommen unabhängig von GPUs; läuft deterministisch auf ressourcenbeschränkter x86- und ARM-Hardware.

### 3. `aria-lint-cli`
*Statischer AST-Prüfer für Barrierefreiheitsinvarianten ohne Laufzeit-Overhead.*
- **Technologie-Stack**: Go, tree-sitter.
- Verifiziert Accessibility-Tree-Verträge, Tastaturfokussperren und dynamische Ankündigungsbereiche (Live Regions) direkt in der CI/CD-Pipeline vor dem Bündeln.

### 4. `earcon-dsp`
*Synthesizer für räumliche Richtungssignale zur nicht-visuellen Desktop-Navigation.*
- **Technologie-Stack**: Rust, `cpal`, HRTF-Faltungsfilter.
- Erzeugt 3D-Audiosignale und Fenstergrenzen-Feedback in Echtzeit, ohne die Sprachausgabe von Screenreadern zu überlagern.

---

## 🔬 Aktuelle Forschung & Schwerpunkte

- [ ] Implementierung von Zero-Copy-Speicherpuffern für Wayland-Accessibility-Bäume bei hochfrequenten DOM-Änderungen.
- [ ] Leistungsbenchmarking zwischen WebAssembly SIMD und nativem SSE4.2 bei Textlayout-Algorithmen für Headless-Screenreader.
- [ ] Ausarbeitung offener Spezifikationen für taktile Vektorgrafikkonverter auf Dual-Zellen-Braille-Pads.

---

## 💻 Arbeitsumgebung & Werkzeuge

```ini
[Hardware]
Arbeitsgerät   = Lenovo ThinkPad P1 Gen 5 (Angepasstes RAM/SSD-Setup)
Bildschirme    = 2x 27" 4K IPS (Fixiertes 200% Integer-Scaling)
Tastatur       = Corne Choc Split (Flaches 36-Tasten-Layout, Miryoku)
Audiomonitor   = Beyerdynamic DT 770 Pro (80 Ohm) + Motu M2 Audio-Interface

[Software]
Betriebssystem = Void Linux (musl libc Basis) / FreeBSD 14.1-RELEASE
Fenstermanager = River (Dynamischer Wayland-Tiling-Compositor)
Terminal       = Foot / Alacritty
Editor         = Neovim (Eigenes Lua-Setup, keine überladenen Frameworks)
Shell          = Zsh + Tmux
```

---

## 📬 Kontakt & Verifikation

- **E-Mail**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk](https://github.com/dhdxkhsk)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **GPG-Fingerabdruck**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*„Software ist erst dann wahrhaft vollendet, wenn jeder Mensch sie ohne Reibung bedienen kann.“*
