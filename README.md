# Android Reverse IDE

On-device Android reverse engineering environment for inspecting, decompiling, editing, rebuilding, and signing Android packages and native binaries without a desktop host.

- **Platform:** Android 8.0+ (API 26) · `arm64-v8a` / `armeabi-v7a`
- **Links:** [Releases](https://github.com/UltraSina/androidReverse/releases) · [Issues](https://github.com/UltraSina/androidReverse/issues) · [Telegram](https://t.me/AndroidReverseTool)

---

## Overview

Android Reverse IDE runs decompilation, resource editing, native binary analysis, obfuscation/deobfuscation, rebuilding, and signing locally on the device. Edits are managed inside workspaces before building and signing output packages.

---

## APK Workspaces, Projects & Signing

- **Package Loading:** Opens `.apk`, `.xapk`, split `.apks` bundles, and installed applications in unified workspace trees.
- **Saved Projects:** Saves multi-archive workspaces, pending Smali/XML/asset edits, bookmarks, and notes across sessions, with search, rename, duplicate, and reload actions.
- **On-Device Rebuild:** Rebuilds modified APKs and split bundles directly on the device, ready for installation on modern Android versions.
- **Signing & Keystores:** Signs packages with v1, v2, and v3 schemes, inspects existing certificates, and creates, imports, or exports JKS/PKCS12 keystores.
- **Standalone Package Signer:** Signs arbitrary `.apk` or `.apks` bundles directly from the home screen without opening a full project.
- **Workspace File Operations:** Exports, replaces, renames, inspects properties, and individually or batch-deletes files inside loaded archives.

---

## Java Decompilation & Smali Tooling

Switch between eight selectable per-class decompilers, alongside full Smali editing and analysis:

| Engine | Notes |
|--------|-------|
| **Jadx** | Primary DEX-to-Java decompiler |
| **Jadx Fallback** | Fallback mode for classes that fail standard Jadx passes |
| **Jadx IR** | Jadx intermediate representation output |
| **Vineflower** | Java decompiler focused on structured control flow |
| **CFR** | Handles modern Java patterns and obfuscation |
| **Procyon** | Handles generics, enums, and lambda expressions |
| **JD-Core** | Lightweight Java decompiler |
| **Krakatau** | Bytecode-level disassembler |

Smali workflows include:

- **Smali Editor:** Syntax highlighting, autocomplete, formatting, class/method/field outline navigation, and jump-to-definition.
- **Smali Call Graph:** Traces incoming and outgoing method invocations and field read/write references across DEX files with configurable traversal depth.
- **Smali Control Flow Graph (CFG):** Interactive method-level basic block graph showing entry/catch blocks and branch, fallthrough, switch, and exception edges.
- **Fast Smali & XML Search & Batch Replace:** Fast search across Smali, decoded XML resources (`AndroidManifest.xml` and `res/`), strings, numbers (decimal/hex), and class/method/field names (regex, case-sensitivity, history, and result filtering), paired with previewed batch Search & Replace and syntax validation.
- **Smali Operations:** Direct class editing, import/delete/replace `.smali` files, path copying, class bookmarking, and selection-based Smali explanation.

---

## Deobfuscation & Obfuscation

Available both as workspace plugins (with auto-reload) and as standalone APK/APKS batch tools on the home screen:

- **Resource Deobfuscator:** Restores obfuscated resource entries and matching `res/` paths cleanly.
- **DEX Deobfuscator:** Renames obfuscated DEX packages, classes, methods, and fields consistently.
- **Control Flow Obfuscator:** Obfuscates Dalvik control flow inside selected packages or classes with configurable depth and include/exclude classpath rules.
- **String Encrypter:** Encrypts Dalvik string constants in selected classpaths with selectable encryption modes, minimum length filters, and custom seed controls.

---

## Native Binary Analysis (ELF / Unity / Flutter)

Powered by Radare2 and Ghidra:

- **Live Disassembly Listing:** Assembly view with inline instruction/byte patching, NOP helpers, batch actions, binary find-and-replace, function/comment annotations, and undoable patch history.
- **Pseudo-C Decompilation:** Decompiler view alongside assembly and hex modes in an expandable code viewer.
- **Control Flow Graph (CFG):** Interactive draggable canvas with zoom/pan, search highlighting, compact mode, and block-level instruction inspection.
- **Call Graph & Xrefs:** Depth-adjustable caller/callee tree and cross-reference jumping.
- **ELF Metadata & Tools:** Binary headers, PIE/NX/Canary/RELRO flags, section jumping, Data Inspector, interactive Radare2 terminal, and an offline Instruction Dictionary (ARMv7-A, ARMv8-A, x86, x86-64).
- **Cross-Platform Runtimes:** Unity `libil2cpp.so` metadata dumping and Flutter `libapp.so` Dart AOT analysis.

---

## Resources, XML, Text & Image Tools

- **AXML & Resource Editing:** Decodes and edits `AndroidManifest.xml`, compiled XML resources, and `resources.arsc` tables, including obfuscated resources.
- **XML Tooling & Preview:** Syntax highlighting, autocomplete, formatting, fast workspace-wide and in-file XML search, inline Data Converter, and on-device visual Layout Preview.
- **Code & Text Editors:** Syntax-highlighted code editors (Java, Smali, C/C++, ARM assembly, XML, JSON, hex) plus a general Text Editor supporting custom encodings, line-ending conversion, syntax validation, document outline, diff view, and checksums.
- **Image Editor & Utilities:** Built-in image editor, persistent cross-session Global Notebook, and on-device Data Converter (`Base64`, `Hex <-> Decimal`, `Hex <-> Text`, `URL`, `Unicode Escape`, `XOR`, `Color Hex`, `XML`).

---

## MCP Server

Includes a local [Model Context Protocol](https://modelcontextprotocol.io) server so compatible MCP clients can inspect project files and edit resources, AXML, native libraries, manifest entries, and Smali directly inside an active session. Building and signing the output APK remains a manual action.

---

## Appearance & Localization

- **Theming:** Material 3 Light, Dark, and System modes, Android 12+ Dynamic Color, AMOLED Pure Black surfaces, custom color palettes, and synchronized editor themes.
- **Languages:** Localized in English and Arabic.

---

## User Agreement & Disclaimer

By installing, opening, or using this application, you agree that you are solely responsible for how you use it and for complying with all applicable laws, licenses, and terms of service. This software is provided "as is" for educational, research, debugging, and authorized analysis purposes only. The developer assumes no legal responsibility or liability for any misuse, unauthorized modification, data loss, or damages arising from the use of this application.
