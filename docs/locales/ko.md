| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> 시니어 시스템 소프트웨어 및 보조 공학(Assistive Interface) 엔지니어.  
> 초저지연 OS 접근성 추상화 레이어, 촉각 점자 단말기 드라이버, 결정론적 텍스트 렌더링 엔진을 개발합니다.

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 소개 (About Me)

운영체제 커널의 입력 파이프라인과 보조 공학 입출력 하드웨어가 맞닿는 시스템 런타임 인프라를 설계하고 구현합니다.

그래픽 디스플레이 서버와 스크린 리더, 점자 디스플레이 단말기, 안구/두부 추적 포인팅 장치 간의 지연 시간(Latency Gap)을 극소화하는 작업에 전념하고 있습니다. 접근성은 사후 땜질식 UI 패치가 아니라, 결정론적 메모리 관리와 불필요한 IPC 홉을 제거한 시스템 레이어의 핵심 인프라여야 한다는 원칙을 지킵니다.

커널 입력 이벤트를 트레이싱하거나 SIMD 가속 텍스트 셰이핑 파서를 작성하지 않을 때는, 분할형 커스텀 기계식 키보드를 납땜하거나 아날로그 테이프 루프를 실험하고 그래블 바이크를 타고 여행합니다.

---

## 🛠️ 기술 역량 (Technical Competency)

### 언어 및 런타임

| 분야 | 핵심 주력 기술 | 탐구 및 보조 기술 |
| :--- | :--- | :--- |
| **시스템 프로그래밍** | Rust, C11, C++20 | Zig, Nim |
| **유저랜드 및 스크립팅** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **웹 및 임베디드 표준** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### 플랫폼 서브시스템 및 드라이버 아키텍처

| 서브시스템 | 전문 도메인 | 주요 API 및 프로토콜 |
| :--- | :--- | :--- |
| **Linux 접근성** | Direct AT-SPI2 bus IPC, `evdev` 이벤트 탭 | D-Bus, `uinput`, Wayland accessibility 프로토콜 확장 |
| **Windows 플랫폼** | Native Windows 접근성 (UIA/IA2) 프로바이더 아키텍처 | IAccessible2, WinEvents, Raw Input API |
| **macOS 접근성** | Native Accessibility API 래퍼 | `AXUIElement`, CoreGraphics event taps |
| **임베디드 및 주변기기** | 점자 디스플레이 컨트롤러 직통 통신 | USB HID-Telephony / Custom 점자 프로토콜, UART / BLE |

---

## 🚀 주요 오픈소스 프로젝트

### 1. `braille-bridge`
*점자 디스플레이(Refreshable Braille Display)를 위한 무할당(Zero-allocation) 메모리 안전 유저랜드 데몬.*
- **핵심 스택**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- 통합 영어 점자(UEB) 및 한글 컴퓨터 8점자 변환 테이블을 마이크로초 단위의 초저지연으로 실시간 처리.
- USB HID, Serial (UART), Bluetooth LE를 지원하는 플러그형 트랜스포트 백엔드 탑재.

### 2. `subtext-engine`
*결정론적 글리프 래스터라이저 및 초고대비 텍스트 렌더링 파이프라인.*
- **핵심 스택**: C11, FreeType, HarfBuzz, 소프트웨어 래스터라이저.
- 저시력자용 렌더링에 특화: 번짐 현상(Halo artifacts) 0%, 서브픽셀 기하학적 팽창 알고리즘, 사용자 맞춤형 색상 분리 곡선 적용.
- GPU 의존성 없이 저사양 임베디드 x86 및 ARM 보드에서도 결정론적 렌더링 보장.

### 3. `aria-lint-cli`
*디자인 시스템을 위한 런타임 오버헤드 0의 AST 접근성 불변식 검증기.*
- **핵심 스택**: Go, tree-sitter.
- 컴포넌트 번들링 이전 CI/CD 단계에서 접근성 트리 규약, 키보드 트랩 방지 규칙, 동적 갱신(Live Regions)을 정적 분석으로 사전 차단.

### 4. `earcon-dsp`
*비시각적 데스크톱 탐색을 위한 공간 음향 방향성 큐 신시사이저.*
- **핵심 스택**: Rust, `cpal`, HRTF 콘볼루션 필터.
- 주 음성 합성기(TTS)의 발화를 방해하지 않으면서 3차원 음향 단서와 윈도우 경계 피드백을 실시간 합성.

---

## 🔬 현재 연구 및 탐구 과제

- [ ] DOM 변동이 극심한 환경에서 Wayland 접근성 트리 업데이트를 위한 제로카피 공유 메모리 버퍼 구현.
- [ ] 헤드리스 스크린 리더 환경에서 WebAssembly SIMD와 네이티브 SSE4.2 텍스트 레이아웃 알고리즘 벤치마크 비교.
- [ ] 일반 소비자용 듀얼셀 점자 패드를 위한 오픈 스펙 촉각 벡터 그래픽 변환 엔진 설계.

---

## 💻 작업 환경 및 도구

```ini
[하드웨어]
메인 머신 = Lenovo ThinkPad P1 Gen 5 (메모리/SSD 커스텀)
디스플레이 = 2x 27인치 4K IPS (200% 정수 스케일링 고정)
키보드   = Corne Choc Split (36키 로우프로파일, Miryoku 레이아웃)
오디오   = Beyerdynamic DT 770 Pro (80옴) + Motu M2 오디오 인터페이스

[소프트웨어]
운영체제     = Void Linux (musl libc 빌드) / FreeBSD 14.1-RELEASE
윈도우 매니저 = River (Wayland 동적 타일링 컴포지터)
터미널       = Foot / Alacritty
에디터       = Neovim (직접 작성한 Lua 설정, 프레임워크 배제)
셸          = Zsh + Tmux
```

---

## 📬 연락처 및 검증

- **이메일**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **GPG 핑거프린트**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*“모든 사람이 장벽 없이 사용할 수 있을 때 비로소 그 소프트웨어는 완성된 것입니다.”*
