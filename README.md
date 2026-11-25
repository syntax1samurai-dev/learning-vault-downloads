# Learning Vault (v0.1.0) — Official Documentation
**Built by Syntax Samurai™**

Learning Vault is a local-first, encrypted desktop study workspace and digital library engineered with **Tauri v2**, **Rust**, **React**, and **SQLite FTS5**. It allows students, researchers, and self-directed learners to organize textbooks, research papers, EPUBs, and offline lecture videos into custom bookshelves, annotate them with color-coded highlighters and bookmarks, and store every asset locally behind authenticated **AES-256-GCM** encryption.

---

## Key Features

### 1. Encrypted Bookshelves & Working Desk
* **Custom Bookshelves:** Create, rename, delete, and reorder shelves while safely migrating books when a shelf is removed.
* **Working Desk:** Pin active study materials to a focused Working Desk view so you can switch between multiple textbooks and lecture videos during a single study session.
* **Instant Full-Text Search:** Powered by **SQLite FTS5** with shelf filter pills to search across book titles, study notes, and saved highlights simultaneously.

### 2. Multi-Format Study Readers & Annotations
* **Interactive PDF Reader (`PDF.js`):** Renders crisp pages with a transparent, selectable HTML text layer for direct drag-to-highlight annotations and page jumping.
* **EPUB Book Reader:** Parses chapters cleanly with HTML sanitization (`ammonia`) and persistent inline highlights.
* **4-Color Highlighter Pen:** Toggle Pen Mode (`Yellow`, `Green`, `Blue`, `Pink`) to highlight passages directly on PDFs and EPUBs, automatically saved and re-rendered per page or chapter.
* **Smart Page & Chapter Bookmarks:** One-bookmark-per-page toggle with a quick-jump dropdown menu showing your current position.

### 3. Built-In Research Browser & Offline Lecture Archiving
* **Tabbed Research Browser:** Quick-access tabs for Wikipedia, Open Library, Internet Archive, Project Gutenberg, Standard Ebooks, arXiv, and privacy-enhanced video streaming.
* **Offline Video & Document Archiving:** Download direct PDF/EPUB links or archive online lecture videos (`yt-dlp`) directly into your encrypted offline library with real-time download progress tracking.
* **Distraction-Free Zen Mode & Spotlight Tour:** Independently collapse the sidebar, main header, and sub-toolbars for full-screen reading, plus an interactive 7-step Spotlight Guided Tour for first-time users.

---

## Security & Privacy Architecture

| Security Layer | Implementation |
| :--- | :--- |
| **Encryption at Rest** | Every imported or downloaded resource is encrypted into a `.lvault` container using **AES-256-GCM** with a unique per-file nonce and 64-byte authenticated header (`AAD`). |
| **File Header Sanitization** | Magic-byte validation verifies `%PDF-`, EPUB ZIP structures, MP4 boxes, and audio headers before ingestion, rejecting disguised executables or scripts. |
| **HTML & Script Stripping** | EPUB chapter content is sanitized through Rust's `ammonia` crate to strip `<script>`, `<iframe>`, and event handlers prior to rendering. |
| **Local-First Storage** | All encrypted vault files and SQLite indexes stay strictly on your local machine (`%LOCALAPPDATA%\com.learning-vault.app\vault\`) with zero cloud tracking. |

---

## Windows Installation & SHA-256 Verification

### System Requirements
* **OS:** Windows 10 / Windows 11 (64-bit x64)
* **Runtime:** Microsoft Edge WebView2 (pre-installed on Windows 10/11)

### Installation Steps
1. Download either installer from the **Syntax Samurai™** portal or **GitHub Releases**:
   * **NSIS Setup Installer (Recommended):** `Learning Vault_0.1.0_x64-setup.exe`
   * **Windows MSI Installer:** `Learning Vault_0.1.0_x64_en-US.msi`
2. Verify the installer's SHA-256 checksum in PowerShell before running:
   ```powershell
   Get-FileHash ".\Learning Vault_0.1.0_x64-setup.exe" -Algorithm SHA256
   ```
3. *(First-time SmartScreen notice)*: Because `v0.1.0` uses a self-signed Authenticode certificate, Windows SmartScreen may display *"Windows protected your PC"*. Click **More info** -> **Run anyway** to complete setup.

### Official Release Checksums (`v0.1.0`)
* **`Learning Vault_0.1.0_x64-setup.exe`:** `PASTE_NEW_EXE_SHA256_HERE`
* **`Learning Vault_0.1.0_x64_en-US.msi`:** `PASTE_NEW_MSI_SHA256_HERE`

---

## License & Copyright
Copyright © 2026 **Syntax Samurai™**. All Rights Reserved.
