| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> Ingeniero Senior de Software de Sistemas e Interfaces Asistivas.  
> Especializado en abstracciones de accesibilidad de baja latencia a nivel de SO, controladores de terminales braille táctiles y motores deterministas de renderizado de texto.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 Acerca de mí (About Me)

Diseño y construyo infraestructura en tiempo de ejecución donde el núcleo del sistema operativo converge con el hardware de entrada/salida asistivo.

Mi principal enfoque técnico consiste en cerrar la brecha de latencia entre los servidores gráficos de pantalla y los clientes de tecnología asistiva, específicamente lectores de pantalla, terminales braille interactivos y dispositivos de puntero controlados por seguimiento ocular y de cabeza. Sostengo firmemente que la accesibilidad no debe ser tratada como un parche superficial de interfaz; pertenece al nivel del sistema, respaldada por una gestión de memoria determinista y la eliminación de saltos de IPC innecesarios.

Cuando no estoy rastreando eventos de entrada en el kernel o escribiendo analizadores de perfilado de glifos acelerados por SIMD, me encontrarás soldando teclados mecánicos ergonómicos divididos, experimentando con bucles de cinta analógica o pedaleando por caminos de grava con mi bicicleta de bikepacking.

---

## 🛠️ Competencias Técnicas

### Lenguajes y Entornos de Ejecución

| Categoría | Tecnologías Principales | Exploración / Secundarias |
| :--- | :--- | :--- |
| **Programación de Sistemas** | Rust, C11, C++20 | Zig, Nim |
| **Espacio de Usuario y Scripts** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Estándares Web y Embebidos** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### Subsistemas de Plataforma y Arquitectura de Controladores

| Subsistema | Especialización | APIs y Protocolos Clave |
| :--- | :--- | :--- |
| **Accesibilidad en Linux** | IPC directo sobre bus AT-SPI2, captura `evdev` | D-Bus, `uinput`, extensiones de protocolo Wayland |
| **Plataforma Windows** | Arquitectura de proveedores nativos de accesibilidad (UIA/IA2) | IAccessible2, WinEvents, Raw Input API |
| **Accesibilidad en macOS** | Wrappers nativos sobre Accessibility API | `AXUIElement`, intercepciones CoreGraphics |
| **Embebidos y Periféricos** | Comunicación directa con controladores braille | USB HID-Telephony / Protocolos braille, UART / BLE |

---

## 🚀 Proyectos de Código Abierto Destacados

### 1. `braille-bridge`
*Demonio en espacio de usuario, seguro en memoria y con cero asignaciones dinámicas para pantallas braille.*
- **Tecnologías Clave**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- Tablas de traducción para Braille Inglés Unificado (UEB) y Braille Computacional Coreano de 8 puntos con latencia inferior al milisegundo.
- Módulos de transporte desacoplables para USB HID, Serial (UART) y Bluetooth LE.

### 2. `subtext-engine`
*Rasterizador determinista de glifos y tubería de renderizado de texto de ultra alto contraste.*
- **Tecnologías Clave**: C11, FreeType, HarfBuzz, rasterizador puramente software.
- Optimizado para visión reducida extrema: cero artefactos de halo, expansión geométrica subpíxel y curvas de separación de color personalizables.
- Sin dependencias de GPU; se ejecuta determinísticamente en arquitecturas embebidas x86 y ARM.

### 3. `aria-lint-cli`
*Analizador estático de invariantes de accesibilidad AST sin sobrecarga en tiempo de ejecución.*
- **Tecnologías Clave**: Go, tree-sitter.
- Valida contratos de árboles de accesibilidad, prevención de trampas de teclado y regiones activas dinámicas (Live Regions) directamente en CI/CD antes de empaquetar.

### 4. `earcon-dsp`
*Sintetizador de señales acústicas direccionales 3D para navegación de escritorio no visual.*
- **Tecnologías Clave**: Rust, `cpal`, filtros de convolución HRTF.
- Produce pistas auditivas espaciales y retroalimentación de bordes de ventanas sin interferir con la dicción de los sintetizadores de voz primarios (TTS).

---

## 🔬 Investigación Actual

- [ ] Implementación de búferes de memoria compartida sin copia (zero-copy) para árboles de accesibilidad Wayland bajo alta mutación del DOM.
- [ ] Evaluación comparativa de rendimiento entre WebAssembly SIMD y SSE4.2 nativo en composición de texto para lectores sin interfaz gráfica.
- [ ] Definición de especificaciones abiertas para convertidores de gráficos vectoriales táctiles en dispositivos braille duales.

---

## 💻 Entorno de Trabajo y Herramientas

```ini
[Hardware]
Equipo Principal = Lenovo ThinkPad P1 Gen 5 (RAM/SSD personalizados)
Monitores        = 2x 27" 4K IPS (Escalado entero 200% bloqueado)
Teclado          = Corne Choc Split (36 teclas, perfil bajo, layout Miryoku)
Monitorización   = Beyerdynamic DT 770 Pro (80Ω) + Interfaz de audio Motu M2

[Software]
Sistema Operativo = Void Linux (entorno musl libc) / FreeBSD 14.1-RELEASE
Gestor de Ventanas = River (Compositor de mosaico dinámico Wayland)
Terminal           = Foot / Alacritty
Editor de Código   = Neovim (Configuración artesanal en Lua, sin frameworks)
Shell              = Zsh + Tmux
```

---

## 📬 Contacto y Verificación

- **Correo electrónico**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **Huella GPG**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*“Un software solo está verdaderamente terminado cuando cualquier persona puede utilizarlo sin fricción.”*
