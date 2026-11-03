| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> Engenheiro Sênior de Software de Sistemas e Interfaces Assistivas.  
> Focado em abstrações de acessibilidade de baixa latência no nível do SO, drivers para linhas braille táteis e motores determinísticos de renderização de texto.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 Sobre Mim (About Me)

Projeto e construo infraestruturas de execução no ponto exato onde o núcleo do sistema operacional se conecta ao hardware assistivo de entrada e saída.

Meu principal objetivo de engenharia consiste em eliminar a lacuna de latência entre servidores de exibição gráfica e clientes de tecnologia assistiva — especialmente leitores de tela, terminais braille dinâmicos e dispositivos de ponteiro controlados por rastreamento ocular e de cabeça. Acessibilidade não deve ser tratada como um remendo cosmético superficial de interface; pertence ao nível fundamental do sistema, com gerenciamento determinístico de memória e eliminação de saltos desnecessários de IPC.

Quando não estou rastreando eventos de entrada no kernel ou escrevendo analisadores de modelagem de glifos acelerados por SIMD, estou soldando teclados mecânicos ergonômicos divididos, experimentando com loops de fita magnética analógica ou pedalando por estradas de terra em viagens de bikepacking.

---

## 🛠️ Competências Técnicas

### Linguagens e Ambientes de Execução

| Categoria | Tecnologias Principais | Em Exploração / Secundárias |
| :--- | :--- | :--- |
| **Programação de Sistemas** | Rust, C11, C++20 | Zig, Nim |
| **Espaço do Usuário e Scripts** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Padrões Web e Embarcados** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### Subsistemas de Plataforma e Arquitetura de Drivers

| Subsistema | Especialização | APIs e Protocolos Principais |
| :--- | :--- | :--- |
| **Acessibilidade no Linux** | IPC direto no barramento AT-SPI2, captura `evdev` | D-Bus, `uinput`, extensões de acessibilidade Wayland |
| **Plataforma Windows** | Arquitetura de provedores nativos de acessibilidade (UIA/IA2) | IAccessible2, WinEvents, Raw Input API |
| **Acessibilidade no macOS** | Wrappers nativos sobre Accessibility API | `AXUIElement`, interceptações CoreGraphics |
| **Embarcados e Periféricos** | Comunicação direta com controladores braille | USB HID-Telephony / Protocolos braille dedicados, UART / BLE |

---

## 🚀 Principais Projetos de Código Aberto

### 1. `braille-bridge`
*Daemon em espaço de usuário com segurança de memória e zero alocações dinâmicas para displays braille.*
- **Tecnologias Principais**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- Tabelas de conversão para Braille Inglês Unificado (UEB) e Braille Computacional Coreano de 8 pontos com resposta sub-milissegundo.
- Módulos de transporte desacopláveis para USB HID, Serial (UART) e Bluetooth LE.

### 2. `subtext-engine`
*Rasterizador determinístico de glifos e pipeline de renderização de texto de altíssimo contraste.*
- **Tecnologias Principais**: C11, FreeType, HarfBuzz, rasterizador via software.
- Especialmente otimizado para baixa visão severa: zero artefatos de halo, expansão geométrica subpixel e curvas personalizadas de separação de cores.
- Independente de GPU; opera de forma determinística em hardware embarcado x86 e ARM.

### 3. `aria-lint-cli`
*Analisador estático de invariantes de acessibilidade AST com sobrecarga zero em tempo de execução.*
- **Tecnologias Principais**: Go, tree-sitter.
- Valida contratos da árvore de acessibilidade, armadilhas de foco do teclado e regiões dinâmicas ativas (Live Regions) diretamente no CI/CD antes do empacotamento.

### 4. `earcon-dsp`
*Sintetizador de pistas acústicas direcionais em 3D para navegação não visual no desktop.*
- **Tecnologias Principais**: Rust, `cpal`, filtros de convolução HRTF.
- Gera referências auditivas espaciais e feedback de limites de janelas sem sobrepor a clareza da voz do leitor de tela principal (TTS).

---

## 🔬 Pesquisas e Explorações Atuais

- [ ] Implementação de buffers de memória compartilhada sem cópia (zero-copy) para a árvore de acessibilidade Wayland sob mutações intensas do DOM.
- [ ] Benchmarking comparativo entre WebAssembly SIMD e SSE4.2 nativo em algoritmos de diagramação de texto para leitores de tela headless.
- [ ] Desenvolvimento de especificações abertas para conversores de gráficos vetoriais táteis em pads braille de célula dupla.

---

## 💻 Estação de Trabalho e Ferramentas

```ini
[Hardware]
Máquina Principal = Lenovo ThinkPad P1 Gen 5 (RAM/SSD personalizados)
Monitores         = 2x 27" 4K IPS (Escalonamento inteiro de 200% travado)
Teclado           = Corne Choc Split (36 teclas, perfil baixo, layout Miryoku)
Monitoramento     = Beyerdynamic DT 770 Pro (80Ω) + Interface de áudio Motu M2

[Software]
Sistema Operacional = Void Linux (base musl libc) / FreeBSD 14.1-RELEASE
Gerenciador Janelas = River (Compositor Wayland de mosaico dinâmico)
Terminal            = Foot / Alacritty
Editor de Código    = Neovim (Configuração artesanal em Lua, sem frameworks)
Shell               = Zsh + Tmux
```

---

## 📬 Contato e Verificação

- **E-mail**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **Impressão Digital GPG**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*“Um software só está verdadeiramente concluído quando qualquer pessoa consegue utilizá-lo sem atrito.”*
