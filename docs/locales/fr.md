| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> Ingénieur Logiciel Senior Systèmes & Interfaces d'Accessibilité.  
> Spécialisé dans les abstractions d'accessibilité à faible latence pour OS, les pilotes de plages braille tactiles et les moteurs de rendu textuel déterministes.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 Présentation (About Me)

Je conçois et développe l'infrastructure d'exécution à l'intersection exacte entre le noyau du système d'exploitation et le matériel d'assistance en entrée/sortie.

Mon objectif d'ingénierie principal est de combler le fossé de latence entre les serveurs d'affichage graphique et les clients des technologies d'assistance : lecteurs d'écran, terminaux braille éphémères et dispositifs de pointage par suivi oculaire ou céphalique. L'accessibilité ne doit jamais être reléguée au rang de correctif cosmétique superficiel ; elle relève du niveau système, fondée sur une gestion déterministe de la mémoire et la suppression de tout saut IPC superflu.

Lorsque je ne suis pas en train de tracer des événements d'entrée du noyau ou d'écrire des analyseurs de glyphes accélérés par SIMD, vous me trouverez en train de souder des claviers mécaniques ergonomiques scindés, de manipuler des boucles de bande magnétique analogique, ou de voyager à vélo sur les pistes de gravier.

---

## 🛠️ Compétences Techniques

### Langages & Environnements d'Exécution

| Catégorie | Technologies Principales | En Exploration / Complémentaires |
| :--- | :--- | :--- |
| **Programmation Système** | Rust, C11, C++20 | Zig, Nim |
| **Espace Utilisateur & Scripts** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Standards Web & Embarqués** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### Sous-systèmes d'Exploitation & Architecture de Pilotes

| Sous-système | Spécialisation | APIs & Protocoles Clés |
| :--- | :--- | :--- |
| **Accessibilité Linux** | IPC direct sur bus AT-SPI2, capture `evdev` | D-Bus, `uinput`, extensions Wayland accessibility |
| **Plateforme Windows** | Architecture de fournisseurs natifs d'accessibilité (UIA/IA2) | IAccessible2, WinEvents, Raw Input API |
| **Accessibilité macOS** | Wrappers natifs Accessibility API | `AXUIElement`, écoutes d'événements CoreGraphics |
| **Systèmes Embarqués & Périphériques** | Communication directe contrôleur braille | USB HID-Telephony / Protocoles braille propriétaires, UART / BLE |

---

## 🚀 Projets Open-Source Majeurs

### 1. `braille-bridge`
*Démon utilisateur à mémoire sûre et sans allocation dynamique pour terminaux braille interactifs.*
- **Technologies Clés**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- Tables de conversion pour le Braille Anglais Unifié (UEB) et le Braille Informatique Coréen à 8 points avec une latence sub-milliseconde.
- Modules de transport interchangeables pour USB HID, liaison série (UART) et Bluetooth LE.

### 2. `subtext-engine`
*Pixellisateur déterministe de glyphes et chaîne de rendu textuel à très haut contraste.*
- **Technologies Clés**: C11, FreeType, HarfBuzz, moteur logiciel dédié.
- Optimisé pour la basse vision sévère : zéro artefact de halo, dilatation géométrique sous-pixel et courbes d'étalonnage colorimétrique personnalisées.
- Aucune dépendance GPU requise ; exécution déterministe sur microprocesseurs embarqués x86 et ARM.

### 3. `aria-lint-cli`
*Analyseur statique d'invariants d'accessibilité AST sans surcoût à l'exécution.*
- **Technologies Clés**: Go, tree-sitter.
- Valide les contrats de l'arbre d'accessibilité, la capture du focus clavier et les zones d'annonce dynamiques (Live Regions) directement en CI/CD avant assemblage.

### 4. `earcon-dsp`
*Synthétiseur de signaux sonores directionnels 3D pour la navigation non-visuelle.*
- **Technologies Clés**: Rust, `cpal`, filtres de convolution HRTF.
- Génère des repères acoustiques spatiaux et des retours de délimitation de fenêtres sans interférer avec la clarté du synthétiseur vocal principal (TTS).

---

## 🔬 Recherches & Explorations en Cours

- [ ] Implémentation de mémoires partagées sans copie (zero-copy) pour l'arbre d'accessibilité Wayland lors de mutations DOM massives.
- [ ] Mesure comparative des performances entre WebAssembly SIMD et SSE4.2 natif pour les algorithmes de mise en page de texte.
- [ ] Conception de spécifications ouvertes pour convertisseurs graphiques vectoriels tactiles adaptés aux dalles braille double-cellule.

---

## 💻 Environnement de Travail & Outillage

```ini
[Matériel]
Station Principale = Lenovo ThinkPad P1 Gen 5 (RAM/SSD configurés sur mesure)
Écrans             = 2x 27" 4K IPS (Mise à l'échelle entière 200% verrouillée)
Clavier            = Corne Choc Split (36 touches, profil bas, disposition Miryoku)
Écoute             = Beyerdynamic DT 770 Pro (80Ω) + Interface audio Motu M2

[Logiciel]
Système d'Exploitation = Void Linux (musl libc) / FreeBSD 14.1-RELEASE
Gestionnaire de Fenêtres = River (Compositeur dynamique en mosaïque Wayland)
Terminal               = Foot / Alacritty
Éditeur de Code        = Neovim (Configuration Lua maison, aucun framework lourd)
Shell                  = Zsh + Tmux
```

---

## 📬 Contact & Clés Publiques

- **Courriel**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **Empreinte GPG**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*« Un logiciel n'est véritablement abouti que lorsque chacun peut l'utiliser sans la moindre friction. »*
