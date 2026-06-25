# Android Reverse

[![Platform](https://img.shields.io/badge/Platform-Android-green.svg?logo=android)](https://github.com/UltraSina/androidReverse)
[![Architecture](https://img.shields.io/badge/Arch-arm64--v8a%20%7C%20armeabi--v7a-ff69b4.svg)](https://github.com/UltraSina/androidReverse)
[![Status](https://img.shields.io/badge/Status-Active_Development-blue.svg)](https://github.com/UltraSina/androidReverse)

[![Download](https://img.shields.io/badge/📦_Download-Latest_Release-00FF87?style=for-the-badge&logo=android&logoColor=black)](https://github.com/UltraSina/androidReverse/releases)

A reverse engineering suite that runs entirely on Android. No PC, no ADB, no desktop tools — everything from APK extraction to native binary analysis happens on-device.

---

## MCP Server

androidReverse includes a built-in [Model Context Protocol](https://modelcontextprotocol.io) server, allowing MCP-compatible AI clients to connect and interact with the tool directly.

---

## Java Decompilation

Eight engines selectable per-class with a single tap:

| Engine | Notes |
|--------|-------|
| **CFR** | Handles most modern obfuscation well |
| **Procyon** | Good with generics and lambdas |
| **JD-Core** | Fast, lightweight |
| **Krakatau** | Bytecode-level accuracy |
| **Vineflower** | Fernflower fork, strong on control flow |
| **Jadx** | Primary engine |
| **Jadx Fallback** | Activates automatically on Jadx failure |
| **Jadx IR** | Raw intermediate representations |

---

## Native Binary Analysis

Powered by an embedded Radare2 engine via JNI.

- **Control Flow Graphs (CFG):** Interactive draggable node canvas with pinch-to-zoom, built on Compose Canvas
- **Call Graph & Xref Tracing:** Depth-adjustable graphs for incoming/outgoing calls and field read/write references
- **Multi-mode output:** Switch between Pseudo-C decompilation, raw assembly, and hex dumps
- **Block Inspector:** Assembly instructions with memory addresses and execution heuristics
- **Binary Info Panel:** Executable metadata at a glance
- **Function Rename & Comments:** Annotate binary functions directly within the decompiler

---

## APK & Resource Handling

- **Universal extraction:** `.apk`, `.xapk`, and split `.apks` — from storage or installed apps
- **Hardened AXML decoding:** Reflection-backed `AXMLPrinter` that bypasses modern manifest obfuscation
- **Deep ARSC parsing:** Navigate resource tables, string pools, and XML attribute mappings in a unified tree view

---

## Smali Tools

- **Jump-to-definition:** Navigate directly to class and method definitions from Smali registers
- **Class Structure Compass:** Filter and jump to methods or fields within large classes
- **Smart Smali Explainer:** Select any block of Smali lines and get an instant plain-language explanation of what the code does

---

## Cross-Platform App Support

- **Flutter:** Dart AOT analysis via Unflutter
- **Unity:** Native il2cpp metadata parsing and function recovery

---

## Code Editor

Built on [Sora Editor](https://github.com/Rosemoe/sora-editor) with TextMate grammar pipelines and Darcula theme. Syntax highlighting for Java, Smali, ARM assembly, C, and hex.

---

## Built-in Utilities

**Data Converter** — On-the-fly encoding/decoding with no external tools:

`Base64` · `Hex ↔ Decimal` · `Hex ↔ Text` · `URL Encode/Decode` · `Unicode Escape` · `XOR Cipher` · `Color Hex Preview`

**Global Notebook** — Persistent notes across sessions. Track offsets, document findings, save snippets.

**Class Bookmarking** — Pin critical classes for fast access during long sessions.

**Deep Memory Search** — Regex-supported search across Smali, class names, and native binary patterns simultaneously.

---

## Screenshots

| Dashboard & Extraction | Smali Navigation | Native CFG |
|---|---|---|
| ![Dashboard](docs/screenshots/placeholder_dashboard.png) | ![Smali](docs/screenshots/placeholder_smali.png) | ![CFG](docs/screenshots/placeholder_cfg.png) |
| *Tree-view extraction & package parsing* | *Sora Editor with Jump-to-Definition* | *Interactive Radare2 assembly blocks* |

| Call Graph | AXML Decoding | Notebook |
|---|---|---|
| ![CallGraph](docs/screenshots/placeholder_callgraph.png) | ![XML](docs/screenshots/placeholder_xml.png) | ![Notebook](docs/screenshots/placeholder_notebook.png) |
| *Depth-adjustable xref mapping* | *Syntax-highlighted XML viewing* | *Persistent multi-session notes* |

---

## Known Limitations

- Code editing and APK recompilation are not yet available. This release focuses on analysis and inspection.

---

## Disclaimer

For educational purposes and security research on applications where you have explicit permission from the author. The developer assumes no liability for misuse.

---

## Credits

- [Sora Editor](https://github.com/Rosemoe/sora-editor) — mobile code editor
- [radare2](https://github.com/radareorg/radare2) — native binary analysis engine
- CFR, Procyon, JD-Core, Krakatau, Vineflower, Jadx — Java decompiler engines
