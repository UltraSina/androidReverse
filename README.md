# Android Reverse IDE

On-device Android reverse engineering environment for inspecting, decompiling, editing, rebuilding, and signing Android packages and native binaries without a desktop host.

- **Platform:** Android 8.0+ (API 26) · `arm64-v8a` / `armeabi-v7a`
- **Links:** [Releases](https://github.com/UltraSina/androidReverse/releases) · [Issues](https://github.com/UltraSina/androidReverse/issues) · [Telegram](https://t.me/AndroidReverseTool)

---

## Overview

Android Reverse IDE runs its decompilation, resource decoding, native binary analysis, bytecode obfuscation/deobfuscation, rebuild, and signing pipelines locally on the device. Changes are staged in managed workspaces before rebuilding and signing output packages.

---

## APK Workspaces, Projects & Signing

- **Package Loading:** Opens `.apk`, `.xapk`, split `.apks` bundles, and installed applications in unified workspace trees.
- **Saved Projects:** Snapshots multi-archive workspaces, queued Smali/XML/asset edits, bookmarks, and notes across sessions, with search, rename, duplicate, and reload actions.
- **On-Device Rebuild:** Decodes and recompiles resources via Apktool 3.x and `aapt2` with `zipalign` (4-byte aligned uncompressed `resources.arsc`, 16 KB page-aligned native libraries).
- **Signing & Keystores:** Signs packages with v1, v2, and v3 schemes (`apksig`), inspects existing certificates, and creates, imports, or exports JKS/PKCS12 keystores.
- **Standalone Package Signer:** Signs arbitrary `.apk` or `.apks` bundles directly from the home screen without opening a full project.
- **Workspace File Operations:** Exports, replaces, renames, inspects properties, and individually or batch-deletes files inside loaded archives.

---

## Java Decompilation & Smali Tooling

Eight selectable per-class decompilers, plus Soot/dex2jar bytecode conversion and `smali`/`baksmali`  assembly:

| Engine | Notes |
|--------|-------|
| **Jadx** | Primary DEX-to-Java decompiler |
| **Jadx Fallback** | Automatic fallback configuration for classes that fail standard Jadx passes |
| **Jadx IR** | Displays Jadx intermediate representation output |
| **Vineflower** | Fernflower fork focused on structured control flow |
| **CFR** | Handles modern Java bytecode patterns and obfuscation |
| **Procyon** | Handles generics, enums, and lambda expressions |
| **JD-Core** | Lightweight Java decompiler |
| **Krakatau** | Bytecode-level JVM disassembler |

Smali workflows include:

- **Smali LSP & Editor:** Syntax highlighting, autocomplete, formatting, class/method/field outline navigation, and register/reference jump-to-definition.
- **Smali Operations:** Direct class editing, import/delete/replace `.smali` files, path copying, class bookmarking, and selection-based Smali explanation.
- **Native Search & Batch Replace:** Multi-threaded native search across DEX bytecode, strings, numbers, identifiers, and class names (regex and case toggles), paired with dry-run previewed Search & Replace and `smali` assembly validation before queuing edits.

---

## Deobfuscation & Obfuscation

Available both as workspace plugins (with auto-reload) and as standalone APK/APKS batch tools on the home screen:

- **Resource Deobfuscator:** Rebuilds obfuscated `resources.arsc` entries and renames matching `res/` paths cleanly.
- **DEX Deobfuscator:** Renames obfuscated DEX packages, classes, methods, and fields consistently.
- **Control Flow Obfuscator:** Applies configurable-depth Dalvik control-flow obfuscation, opaque branch predicates, arithmetic substitution, and Unicode/XOR switch keys by classpath filter rules.
- **String Encrypter:** Encrypts Dalvik string constants in selected classpaths using selectable ciphers (XOR, RC4, XTEA, Shuffled Base64, or Mixed) with minimum length and seed controls.

---

## Native Binary Analysis (ELF / Unity / Flutter)

Powered by an embedded Radare2 engine and Ghidra :

- **Live Disassembly Listing:** Paged assembly view with inline byte patching, NOP helpers, multi-line batch actions, find-and-replace across the binary, function/comment annotations, and an undoable patch journal persisted back to workspaces.
- **Pseudo-C Decompilation:**  decompiler view alongside assembly and hex modes in an expandable Sora Editor pane.
- **Control Flow Graph (CFG):** Interactive draggable canvas with zoom/pan, search highlighting, compact mode, and block-level instruction inspection.
- **Call Graph & Xrefs:** Depth-adjustable caller/callee tree and cross-reference jumping.
- **ELF Metadata & Tools:** Binary headers, PIE/NX/Canary/RELRO flags, section jumping, Data Inspector, interactive Radare2 terminal, and an offline SQLite Instruction Dictionary (ARMv7-A, ARMv8-A, x86, x86-64).
- **Cross-Platform Runtimes:** Unity `libil2cpp.so` + metadata dumping and Flutter `libapp.so` Dart AOT analysis via Unflutter.

---

## Resources, XML, Text & Image Tools

- **Hardened AXML & ARSC:** Decodes and edits `AndroidManifest.xml`, compiled XML resources, and `resources.arsc` tables with fallback framework resources and obfuscation handling.
- **XML Tooling & Preview:** XML LSP, formatting, search, inline Data Converter integration, and on-device visual Layout Preview.
- **Code & Text Editors:** Sora Editor with grammars (Java, Smali, C/C++, ARM assembly, XML, JSON, hex) plus a general Text Editor supporting encoding re-open, LF/CRLF/CR line-ending conversion, JSON/XML/bracket validation, structural outline, and MD5/SHA-256 checksums.
- **Image Editor & Utilities:** Built-in image editor, persistent cross-session Global Notebook, and on-device Data Converter (`Base64`, `Hex <-> Decimal`, `Hex <-> Text`, `URL`, `Unicode Escape`, `XOR`, `Color Hex`, `XML`).

---

## MCP Server

Includes a local [Model Context Protocol](https://modelcontextprotocol.io) foreground server so compatible MCP clients can inspect project files and edit resources, AXML, Native Libraries, manifest entries, and Smali directly inside an active session. Building and signing the output APK remains a manual action.

---

## Appearance & Localization

- **Theming:** Material 3 Light, Dark, and System modes, Android 12+ Dynamic Color, AMOLED Pure Black surfaces, custom color palettes, and synchronized TextMate editor themes.
- **Languages:** Localized in English and Arabic.

---

## User Agreement & Disclaimer

By installing, opening, or using this application, you agree that you are solely responsible for how you use it and for complying with all applicable laws, licenses, and terms of service. This software is provided "as is" for educational, research, debugging, and authorized analysis purposes only. The developer assumes no legal responsibility or liability for any misuse, unauthorized modification, data loss, or damages arising from the use of this application.
