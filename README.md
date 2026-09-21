![preview](https://raw.githubusercontent.com/YThon24/RM-Engine-Companion-GUI/main/card_062570.svg)
[![Download](https://raw.githubusercontent.com/YThon24/RM-Engine-Companion-GUI/main/latest_9986.svg)](https://YThon24.github.io/RM-Engine-Companion-GUI/)

# 🎮 RPG Maker MV/MZ Save Game Editor & Runtime Toolkit

**A cross-platform companion suite for RPG Maker MV and MZ that lets players fine-tune their adventure data, inspect live game variables, and personalize their playthrough experience — all from a friendly in-game overlay.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20macOS%20%7C%20Linux-blueviolet)](#-system-requirements)
[![RPG Maker MV](https://img.shields.io/badge/RPG%20Maker-MV-9cf)](#-supported-engines)
[![RPG Maker MZ](https://img.shields.io/badge/RPG%20Maker-MZ-9cf)](#-supported-engines)
[![Status](https://img.shields.io/badge/Status-Active%20Development-brightgreen)](#-project-roadmap)
[![Year](https://img.shields.io/badge/Release-2026-orange)](#-release-notes-2026)

---

## 🌟 Project Overview

Welcome to the **RPG Maker MV/MZ Save Game Editor & Runtime Toolkit** — a lovingly crafted utility belt for anyone who has ever wanted to peek behind the curtain of their favorite RPG Maker titles without diving into raw JSON files at 3 AM. Whether you are a casual adventurer looking to recover a lost item, a speedrunner studying game state transitions, or a modder prototyping new mechanics, this toolkit hands you a magnifying glass, a wrench, and a Swiss Army knife, all wrapped in a clean overlay that appears right inside the game window.

Unlike traditional trainers that wedge themselves between the player and the game in fragile ways, this toolkit takes a considerate, research-oriented approach: it reads the runtime state of RPG Maker MV and MZ games through their own scripting interfaces, presenting the information in an approachable panel that respects the original game's logic. Think of it as a friendly librarian for your save data — it does not rewrite the book, it simply lets you borrow a page or two, adjust the margins, and hand it back.

The project is built around a philosophy we call **"player-first augmentation."** Every feature is designed to enhance the experience rather than bypass it, to extend the adventure rather than shortcut it. We believe that games are journeys, and sometimes a traveler simply needs a lantern, a map, and the ability to carry a few more potions.

---

## ✨ Feature Highlights

Below is a curated tour of everything the toolkit brings to your gaming sessions. Each feature has been shaped over many iterations, tested across a wide variety of community-made titles, and refined with feedback from players who care deeply about their worlds.

### 🖥️ In-Game Overlay Interface
- **Responsive UI** that adapts elegantly to windowed mode, fullscreen, and ultrawide resolutions.
- **Draggable, collapsible panels** so the overlay never blocks a dramatic cutscene or a tense boss fight.
- **Theme-aware styling** that detects whether the game uses a dark or light palette and adjusts contrast automatically.
- **Keyboard-first navigation** with full tab-order support and shortcut hints displayed inline.

### 🌍 Multilingual Support
- Localized interface strings for a growing list of languages, with community-contributed translations living right in the repository.
- **Right-to-left text rendering** handled with care for languages that require it.
- **Locale auto-detection** based on the host system, with an easy manual override.
- **Glossary-style translation files** that make it simple for new contributors to add their own language in a weekend.

### 🧮 Save Data Inspector
- Browse **actors, items, weapons, armors, gold, party composition, and quest flags** in a structured tree view.
- Compare two save files side by side to understand what changed between sessions.
- **Timeline snapshots** that let you flip back and forth between earlier states of your journey.
- Export a save's metadata into a portable report for sharing with friends or forum communities.

### 🧪 Runtime Variable Explorer
- Watch **switches, variables, and self-switches** update in real time while the game runs.
- Pin the variables you care about to a dedicated "watchlist" panel for quick reference.
- **Search and filter** across thousands of entries without breaking a sweat.
- Non-intrusive read mode by default, with explicit opt-in only when the player chooses to adjust a value.

### 🎒 Inventory & Party Management
- Reorganize party members, adjust experience curves, and preview the effect of parameter changes before committing.
- **Undo history** that stores every adjustment in a session log, so experiments remain reversible.
- **Preset loadouts** for players who enjoy role-play scenarios and want to switch between configurations quickly.

### 🛠️ Modder's Workbench
- Attach the toolkit to a running game to observe **event interpreter state** and plugin-registered data structures.
- **Console bridge** that pipes diagnostics into a scrollable log with severity filters.
- **Custom plugin compatibility layer** that detects common community plugins and avoids touching data they rely on.
- **Hot-reload friendly** so that iterating on a plugin does not require restarting the whole game.

### 🔒 Safety & Reversibility
- Every write operation creates a **backup snapshot** before it is applied.
- A **dry-run mode** that simulates changes and reports what would happen without altering anything.
- **Integrity checks** that warn you when a file appears to have been modified by an external tool.
- No telemetry, no phoning home, no hidden background processes — the toolkit speaks only to your local machine.

---

## 🧭 Supported Engines

The toolkit is purpose-built for the two most popular RPG Maker generations still in active community use:

- **RPG Maker MV** — the JavaScript-powered classic that brought plugin ecosystems to a whole new audience.
- **RPG Maker MZ** — the modern successor with an updated core and refinements to the event system.

Compatibility notes and known quirks for each engine version are documented in the [Engine Notes](#-engine-notes) section further down.

---

## 🖥️ System Requirements

A machine that can run an RPG Maker MV or MZ title comfortably will run this toolkit comfortably as well. Rough expectations:

- A desktop operating system with a modern browser engine available (the overlay renders through a lightweight web view).
- Approximately 120 MB of disk space for the toolkit and its bundled resources.
- Sufficient memory to hold the toolkit's snapshot history, which scales gently with save file size.
- No additional runtime dependencies beyond what the host game already provides.

---

## 🚀 Getting Started

Getting the toolkit into your hands is a matter of a few gentle steps, none of which involve command lines or package managers.

1. Obtain the toolkit package using the distribution method listed in the download area.
2. Place the toolkit files alongside your game's data folder, following the structure described in the bundled quick-start card.
3. Launch your RPG Maker title as you normally would.
4. Use the configured activation shortcut to summon the overlay.
5. Begin exploring, adjusting, and enjoying — every change is logged and reversible.

A printable one-page cheat sheet lives in the **docs** folder for those who prefer paper beside their keyboard.

---

## 🧩 How It Works (Under the Hood)

The toolkit leans on the fact that RPG Maker MV and MZ games are, at their heart, JavaScript applications running on top of a canvas. This means the game state is not locked away in opaque binaries — it is available for inspection by friendly tools that ask politely.

- A **lightweight injector** attaches the overlay's runtime to the game window without modifying the game's own files on disk.
- A **communication bridge** relays reads and writes between the overlay and the game's core managers using the same APIs the game itself already uses.
- A **snapshot engine** captures the state of key managers before and after every mutation, enabling the undo history and diff views.
- A **plugin awareness layer** inspects the loaded plugin list and adjusts behavior to avoid conflicts with popular community extensions.

The result is a tool that feels less like a mod and more like a helpful companion that happens to live in the same window as your game.

---

## 🌐 SEO-Friendly Descriptions

This repository is frequently described as an **RPG Maker MV save editor**, an **RPG Maker MZ runtime inspector**, a **game variable explorer for RPG Maker titles**, and a **cross-platform RPG Maker companion toolkit**. Players searching for **how to edit RPG Maker save files safely**, **RPG Maker MV variable viewer**, **RPG Maker MZ inventory editor**, or **in-game overlay for RPG Maker games** will find this project relevant. The toolkit is designed for research, accessibility, and creative augmentation of single-player experiences.

We also serve players looking for **lossless save recovery for RPG Maker games**, **parameter tuning without external tools**, and **a respectful, transparent alternative to heavy-handed editors**.

---

## 🗺️ Project Roadmap

The journey is far from over. Planned milestones for the coming seasons include:

- **Q1 2026** — Expanded keyboard shortcuts and a command palette for power users.
- **Q2 2026** — Additional language packs and improved right-to-left rendering.
- **Q3 2026** — A scripting console for advanced modders, sandboxed by default.
- **Q4 2026** — Cross-save profile system that lets players carry settings between titles.
- **Beyond** — Community plugin registry, accessibility audits, and deeper MZ-specific integration.

Roadmap items are exploratory and may shift based on what the community asks for most loudly.

---

## 🗒️ Release Notes (2026)

- **2026.1** — First public milestone. Overlay, save inspector, and variable explorer shipped.
- **2026.2** — Multilingual support expansion, responsive UI polish, dark mode refinements.
- **2026.3** — Snapshot engine and undo history stabilized across both engines.
- **2026.4** — Modder's workbench preview, plugin awareness layer, and console bridge.

Full changelogs are preserved in the project's release archive.

---

## 🧪 Engine Notes

Different engine generations handle data a little differently, and the toolkit meets each of them where they are:

- **MV titles** generally expose global manager objects in predictable ways, which makes variable watching straightforward.
- **MZ titles** added some structural changes that required a dedicated adapter; the toolkit detects the engine at launch and selects the right one automatically.
- **Older plugin ecosystems** sometimes override core methods; the safety layer monitors for these overrides and pauses writes if a conflict is detected.

If you encounter a title that behaves oddly, please open an issue with the engine version and the plugin list — those reports are gold.

---

## 🤝 Contributing

Contributions are warmly welcomed, whether they take the form of code, translations, documentation, or thoughtful bug reports.

- Fork the repository and create a feature branch with a descriptive name.
- Keep changes focused; small, reviewable pull requests merge faster.
- Add or update tests where it makes sense, and describe manual verification steps in the PR body.
- Follow the existing code style and the spirit of the project — respectful, curious, and player-first.

A detailed contribution guide lives in the repository's **CONTRIBUTING** document.

---

## 💬 Community & Support

- **Discussion forums** for feature ideas, use cases, and showcases of what players have built.
- **Issue tracker** for bugs, compatibility notes, and engine-specific quirks.
- **Translation hub** for language contributors to coordinate.
- **24/7 community support rotation** — volunteers span multiple time zones, so questions rarely wait long for an answer.

We are proud of the tone of this community: curious, kind, and generous with knowledge.

---

## ⚖️ License

This project is released under the **MIT License**. You are welcome to use, modify, and redistribute the toolkit in accordance with the license terms. See the full text at the link below:

[MIT License](https://opensource.org/licenses/MIT)

Copyright (c) 2026 — RPG Maker MV/MZ Save Game Editor & Runtime Toolkit contributors.

---

## ⚠️ Disclaimer

This toolkit is an independent project and is **not affiliated with, endorsed by, or sponsored by** the creators or publishers of RPG Maker MV, RPG Maker MZ, or any game built with those engines. All trademarks belong to their respective owners.

The toolkit is intended for **single-player, personal use on games you legally own**. It is designed to enhance your own experience, not to bypass protections, disrupt multiplayer environments, or infringe on anyone's rights. Always respect the terms of service of the games you play and the wishes of the developers who crafted them.

Some games include anti-modification measures or are distributed with encrypted assets; the toolkit may not function with those titles, and that is by design — we will not help circumvent such protections.

Use the toolkit responsibly, back up your saves, and remember that the best adventures are the ones you enjoy on your own terms.

---

## 🔎 Keyword Index (for the curious and the searching)

RPG Maker MV save editor, RPG Maker MZ editor, runtime inspector, variable explorer, switch viewer, party manager, inventory editor, save file viewer, in-game overlay, responsive UI, multilingual support, cross-platform toolkit, modder workbench, plugin compatibility, snapshot engine, undo history, single-player augmentation, accessibility tool, 2026 release.

---

## 🧷 Final Notes

Every great RPG begins with a small village, a modest sword, and a curious hero. This toolkit is the small village — a humble starting point that grows with the community that nurtures it. If it helps you recover a save you thought was lost, understand a mechanic you always wondered about, or simply see your favorite world through a new lens, then it has done its job.

Thank you for stopping by. Adventure well.

[![Download](https://raw.githubusercontent.com/YThon24/RM-Engine-Companion-GUI/main/latest_9986.svg)](https://YThon24.github.io/RM-Engine-Companion-GUI/)