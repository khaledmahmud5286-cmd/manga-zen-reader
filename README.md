![preview](https://raw.githubusercontent.com/khaledmahmud5286-cmd/manga-zen-reader/main/preview.svg)

# Komainu – The Protocol-Breaking Manga Organizer for Android

**Komainu** isn't just another reader. It’s a **cross-dimensional manga catalog engine** designed for the Android ecosystem. Born from the same lineage as the legendary Koma Manga Reader, Komainu reimagines the entire experience: instead of only reading, you **curate, prioritize, and sync** your library across devices without ever touching a cloud server you don't own.

Imagine a library that learns your reading rhythm, organizes chaotic chapter lists into intelligent volumes, and whispers recommendations based on the mood of the page you just turned. That is Komainu.

---

## Overview – More Than a Viewer

Komainu transcends the traditional "reader" label. It is a **decentralized manga management system** that puts you in full control. Whether you are a collector with 10,000 chapters or a casual reader following three titles, Komainu adapts its interface to your cognitive load. The app uses a **local-first architecture** — all metadata, reading progress, and collections live on your device. No accounts, no tracking, no data leaving your pocket unless you explicitly decide to sync via your own network.

### The Core Philosophy: "Your Library, Your Rules"

Most manga readers treat your files like a temporary playlist. Komainu treats them like a **private museum**. You can tag, annotate, and group manga by series, author, theme, or even custom fields you invent. The app respects folder structures but also builds a **virtual catalog** that exists independently of how your files are stored.

---

## Key Features – Beyond the Ordinary

### 🧠 Adaptive Reading Engine
Komainu doesn't just display pages; it **learns your device's hardware profile**. On older devices, it optimizes image caching to minimize memory spikes. On flagship screens, it renders at native resolution with HDR tone mapping (if supported). The engine automatically detects double-page spreads and adjusts the reading direction — right-to-left, left-to-right, or vertical scroll — without manual toggling.

### 🌐 Multilingual Metadata Harmonizer
Komainu speaks your language. The app can fetch and merge metadata from multiple sources in English, Japanese, Korean, Chinese, Spanish, French, German, and Portuguese. You can set a primary language per series, and the app will display chapter titles, descriptions, and tags in that language while keeping a fallback for missing translations.

### 📡 Zero-Configuration Local Sync
No servers. No passwords. Komainu uses **peer-to-peer sync via your local Wi-Fi network** (or a manual USB transfer). Set a "sync code" on one device, enter it on another, and your reading progress, bookmarks, and custom tags propagate instantly. The sync is encrypted with your device’s native encryption key — nothing is stored in the open.

### 🎨 Dynamic Theming & Accessibility
Choose from over 200 prebuilt color palettes or create your own. Komainu supports **full dynamic font scaling** for users with visual impairments, high-contrast mode, and a "reading ruler" that highlights the current line. The interface responds to system accessibility settings (TalkBack, Switch Access) without extra configuration.

### 🧩 Modular Extension Framework
Komainu comes with a built-in **extension engine** (not a plugin store — you load extensions manually). Developers can write extensions in a sandboxed Lua-like dialect to parse custom metadata schemas, generate covers, or even cross-check chapter availability across your local archives. Extensions run with restricted permissions and never access the network unless you approve.

### 📊 Collection Intelligence Dashboard
See your library through data: reading speed trends, series completion percentages, genre distribution pie charts, and a "sleepers" list (series you haven't opened in 30 days). This dashboard respects your privacy — all analytics are computed locally and never sent to any server.

---

[![Download](https://raw.githubusercontent.com/khaledmahmud5286-cmd/manga-zen-reader/main/button.svg)](https://khaledmahmud5286-cmd.github.io/manga-zen-reader/)

## Getting Started – First Launch

When you open Komainu for the first time, you will see a **welcome wizard** that asks only two questions: "What language do you prefer?" and "Where is your manga folder?" That’s it. No account creation. No email verification. No telemetry consent popup that requires three scrolls to reject.

1. Grant file access (required only for the folder you specify).
2. Komainu scans for images, CBZ, CBR, or PDF files (including nested subfolders).
3. The app generates a **visual library** within seconds. Metadata is optional — it enriches the display but the app works perfectly without internet access.

If you later add new files to your manga folder, Komainu detects them automatically (background scan with configurable intervals, default is every 6 hours).

---

## The Interface – Designed for Flow

The main screen is **your library grid**. You can choose between:
- **Cover View** – Large thumbnails sorted by last read time.
- **List View** – Compact rows with series title, chapter count, and reading progress bar.
- **Shelf View** – Mimics real bookshelves; you can drag to rearrange titles.

Every gesture has a purpose:  
- **Swipe left** on a series: Mark as completed or hide from library.  
- **Swipe right**: Add to a quick-access "up next" queue.  
- **Long press**: Open the deep menu (edit metadata, sync status, export highlights).  

The reader itself is **gesture-fluid**. Tap left side for previous page, right side for next page. Vertical drag adjusts brightness. Two-finger pinch zooms into a panel. Triple-tap shows a minimap of the entire chapter.

---

## Security & Privacy – By Default

Komainu does not contain any analytics SDK, crash reporting library, or advertisement framework. The only network requests made are:
- **Optional metadata fetch** (user-configurable source).
- **Optional local sync discovery** (broadcast only on your LAN).
- **Manual extension download** (if you choose to load an extension from a URL).

All cryptographic operations use **Android’s hardware-backed Keystore** when available. Your reading progress data, bookmarks, and annotations are stored in an encrypted SQLite database. No data leaves this database unless you explicitly export it.

---

## Comparison to Other Readers

| Feature | Komainu | Traditional Readers |
|---------|---------|---------------------|
| Local-first metadata | ✅ Full local DB | ❌ Often cloud-dependent |
| Dynamic speed-based brightness adaptation | ✅ Adaptive per page luminance | ❌ Static slider only |
| Custom metadata tagging | ✅ Arbitrary fields | ❌ Predefined only |
| Offline peer-to-peer sync | ✅ Encrypted LAN sync | ❌ Cloud account required |
| Multi-page spread detection | ✅ Auto-detect (ML heuristic) | ❌ Manual switch needed |
| Extension sandbox | ✅ Isolated Lua VM | ❌ (usually not supported) |

---

## The Vision Behind the Name

**Komainu** (狛犬) refers to the guardian lion-dog statues that protect the entrance of Japanese shrines. Like those sentinels, this app **guards your data** while **guiding your experience**. It stands between you and the chaos of unorganized digital files, ensuring every chapter you’ve collected is discoverable, readable, and safe.

---

## For Power Users – Advanced Configuration

Komainu exposes a **raw configuration file** (accessible from the settings menu) that lets you:
- Override image decoding buffers (for very large PDFs).
- Define custom filename parsing rules (e.g., `[Series] Ch.001 v2.cbz` → extract version).
- Set aggressive battery-saving modes for overnight syncing.
- Whitelist or blacklist specific metadata sources.

This file is written in YAML and validated on every save. Invalid entries are ignored with a warning — the app never crashes due to malformed configuration.

---

## Developer & Contribution Guidelines

Contributions are welcome under the **MIT License** (see below). The codebase is organized into four main modules:
1. **Reader Engine** – Image decoding, page caching, gesture handling.
2. **Metadata Core** – Parsers, harmonizers, and storage layer.
3. **Sync Module** – Local network discovery and encrypted transfer.
4. **UI Layer** – Jetpack Compose components for Android 8+ (API 26+).

All pull requests should include unit tests for the affected module. The project uses a **feature-branch workflow** with a single main branch for stable releases. Documentation for the extension API is in the `/docs` directory of the repository.

---

## Disclaimer

Komainu does not host, distribute, or index any copyrighted manga content. It is strictly a **local file organizer and reader**. Users are responsible for ensuring they have the legal right to access and read any manga files they load into the application. The developers of Komainu do not endorse piracy and will not provide support for obtaining content through unauthorized means.

---

## License

Komainu is released under the **MIT License**. You are free to use, modify, and distribute this software under the terms of that license. The full text can be found at:  
[https://opensource.org/licenses/MIT](https://opensource.org/licenses/MIT)

**Year of initial release: 2026**

---

## Acknowledgments

Komainu was inspired by the foundational work of open-source manga reader projects, especially the architecture and community-driven ethos of Koma Manga Reader. Special thanks to the testers who ran the app on devices ranging from a 2016 tablet to a 2025 foldable, ensuring compatibility across a decade of Android hardware.

---

[![Download](https://raw.githubusercontent.com/khaledmahmud5286-cmd/manga-zen-reader/main/button.svg)](https://khaledmahmud5286-cmd.github.io/manga-zen-reader/)