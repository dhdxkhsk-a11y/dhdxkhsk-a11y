| [KR 한국어](./ko.md) | [US English](../../README.md) | [JP 日本語](./ja.md) | [CN 简体中文](./zh-CN.md) | [ES Español](./es.md) |
| :---: | :---: | :---: | :---: | :---: |
| [FR Français](./fr.md) | [DE Deutsch](./de.md) | [RU Русский](./ru.md) | [BR Português](./pt-BR.md) | [SA العربية](./ar.md) |

---

# Min (@dhdxkhsk-a11y)

> シニア・システムソフトウェア ＆ アシスティブ・インターフェース エンジニア。  
> 低遅延OSアクセシビリティ抽象化レイヤー、触覚点字ディスプレイのドライバ、および決定論的テキストレンダリングエンジンの開発。

```text
  _  _  _    _      _   _       _       
 | || |(_)__| |_  _| |_| |_  __| |__ ___
 | __ || / _` \ \ /| / / ' \(_-< / // -_)
 |_||_||_\__,_/_\_\|_\_\_||_/__/_\_\\___|
 [ Low-Latency UI IPC ] [ Screen Reader Bridges ] [ Rust / C11 ]
```

---

## 🧭 自己紹介 (About Me)

OSの入力サブシステムと支援技術（Assistive Technology）の入出力ハードウェアが交差するランタイム基盤を設計・構築しています。

グラフィックディスプレイサーバとスクリーンリーダー、点字端末、アイトラッキング機器間のレイテンシギャップを極限まで縮めることに注力しています。アクセシビリティは後付けのパッチではなく、決定論的なメモリ管理と不要なIPCホップを排除したシステムレイヤーの本質的な基盤であるべきだと考えています。

カーネル入力イベントのトレースやSIMDアクセラレーションによるテキストシェーピングの実装を行っていないときは、自作スプリットキーボードのはんだ付け、アナログテープループの実験、あるいはグラベルロードバイクでのツーリングを楽しんでいます。

---

## 🛠️ 技術スタック (Technical Competency)

### 言語およびランタイム

| カテゴリ | 主な技術 | 探求・サブ技術 |
| :--- | :--- | :--- |
| **システムプログラミング** | Rust, C11, C++20 | Zig, Nim |
| **ユーザーランド・スクリプト** | Go, TypeScript, POSIX Shell | Python 3, Lua 5.4 |
| **Webおよび組み込み標準** | WebAssembly (SIMD), WAI-ARIA 1.3 | WebGPU, WebRTC DataChannels |

### プラットフォーム・サブシステムおよびドライバ構造

| サブシステム | 専門領域 | 主なAPI・プロトコル |
| :--- | :--- | :--- |
| **Linux アクセシビリティ** | 直接 AT-SPI2 bus IPC, `evdev` イベントタップ | D-Bus, `uinput`, Wayland accessibility protocol extensions |
| **Windows プラットフォーム** | ネイティブ Windows アクセシビリティ (UIA/IA2) プロバイダ設計 | IAccessible2, WinEvents, Raw Input API |
| **macOS アクセシビリティ** | ネイティブ Accessibility API ラッパー | `AXUIElement`, CoreGraphics event taps |
| **組み込み・周辺機器** | 点字ディスプレイコントローラ直結通信 | USB HID-Telephony / Custom 点字プロトコル, UART / BLE |

---

## 🚀 主なオープンソースプロジェクト

### 1. `braille-bridge`
*リフレッシャブル点字ディスプレイのためのメモリ安全・ゼロアロケーションなユーザーランドデーモン。*
- **コア技術**: Rust, `hidapi`, D-Bus / Windows Named Pipes.
- 統合英語点字（UEB）および韓国語コンピュータ8点点字の変換テーブルをマイクロ秒単位でリアルタイム処理。
- USB HID、シリアル（UART）、Bluetooth LE対応のプラグ可能トランスポートバックエンドを搭載。

### 2. `subtext-engine`
*決定論的グリフラスタイザおよび超高コントラストテキスト描画パイプライン。*
- **コア技術**: C11, FreeType, HarfBuzz, ソフトウェアラスタイザ。
- ロービジョン（弱視）向け描画に最適化：ハロー効果ゼロ、サブピクセル幾何学的拡張アルゴリズム、ユーザー定義のカラー分離曲線。
- GPUに依存せず、省電力な組み込みx86およびARMボード上でも決定論的に動作。

### 3. `aria-lint-cli`
*デザインシステムのためのゼロランタイムASTアクセシビリティ不変条件アナライザ。*
- **コア技術**: Go, tree-sitter.
- バンドル前のCI/CD環境において、アクセシビリティツリー規約、キーボードトラップ防止、動的アナウンス領域（Live Regions）を静的解析により事前検出。

### 4. `earcon-dsp`
*非視覚的デスクトップナビゲーション用 空間オーディオ指向性キューシンセサイザ。*
- **コア技術**: Rust, `cpal`, HRTF畳み込みフィルタ。
- メインの音声合成（TTS）の聞き取りを妨げることなく、3D音響手がかりやウィンドウ境界フィードバックをリアルタイム生成。

---

## 🔬 現在の研究テーマ

- [ ] DOM構造が頻繁に変動する状況下でのWaylandアクセシビリティツリー高速更新用ゼロコピー共有メモリバッファの実装。
- [ ] ヘッドレススクリーンリーダー環境におけるWebAssembly SIMDとネイティブSSE4.2テキストレイアウト処理の性能比較検証。
- [ ] コンシューマー向け2セル触覚点字パッド用オープン仕様ベクターグラフィック変換エンジンの策定。

---

## 💻 開発環境・ツール

```ini
[ハードウェア]
メインマシン   = Lenovo ThinkPad P1 Gen 5 (RAM/SSDカスタム)
ディスプレイ   = 2x 27インチ 4K IPS (200% 整数スケーリング固定)
キーボード     = Corne Choc Split (36キー ロープロファイル, Miryokuレイアウト)
オーディオ     = Beyerdynamic DT 770 Pro (80Ω) + Motu M2 オーディオインターフェース

[ソフトウェア]
OS             = Void Linux (musl libc環境) / FreeBSD 14.1-RELEASE
ウィンドウマネージャ = River (Wayland 動的タイリングコンポジタ)
ターミナル     = Foot / Alacritty
エディタ       = Neovim (手書きLua構成, 重量級フレームワーク不使用)
シェル         = Zsh + Tmux
```

---

## 📬 連絡先・公開鍵

- **Email**: `dhdxkhsk@gmail.com`
- **GitHub**: [@dhdxkhsk-a11y](https://github.com/dhdxkhsk-a11y)
- **GitLab**: [@dhdxkhsk](https://gitlab.com/dhdxkhsk)
- **Hugging Face**: [@r3eaw3](https://huggingface.co/r3eaw3)
- **GPG Fingerprint**: `9F8A 2B71 C4E0 813D 6D25  E4A9 72B0 11C8 40A5 E68F`

---

*「すべての人が障壁なく操作できて初めて、そのソフトウェアは完成したと言える。」*
