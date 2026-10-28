# Scriptura

> **"A hit is not proof of anything."** — *Scriptura is an offline research tool. Scripture is never modified; sealed texts are integrity-protected research data.*[cite: 8]

Scriptura is a high-performance desktop application built in pure Rust for Windows. It is engineered for reading the King James Bible and conducting rigorous, honest research on equidistant letter sequences (ELS) with deterministic multi-threaded CPU execution[cite: 10, 12, 21].

---

## Core Guarantees & Principles

* **100% Offline & Private:** Zero internet dependencies, telemetry, network code, or background calls[cite: 10, 12, 21].
* **Sealed, Protected Texts:** User-supplied KJV and Hebrew text files are verified via SHA-256 hashes and permanently sealed against modification[cite: 10, 12, 14].
* **Pure CPU Execution:** No GPU offloading, no AI models, and no artificial heuristics. All search results are exact, transparent, and reproducible across any hardware[cite: 10, 12, 21].
* **Empirical Controls:** Evaluates findings against scrambled control copies to compute empirical $p$-values, explicitly accounting for the look-elsewhere effect[cite: 11, 19, 21].

---

## Hardware Optimization & Performance

Scriptura dynamically detects your host architecture and distributes compute tasks across available cores based on your active Performance Profile (**Quiet**, **Balanced**, or **Maximum**):[cite: 10, 16]

* **Baseline Performance:** Native Rust execution optimized for multi-threading (tested on AMD Ryzen 9 9950X3D 16c/32t with 64 MiB 3D V-Cache).
* **Medium Verification Tier:** Completes fixed Hebrew checks in ~2 seconds[cite: 17].
* **Deep Verification Tier:** Executes multi-order ELS ladders and 100-copy control shuffles in ~30–42 seconds[cite: 17].

---

## Project Structure (Cargo Workspace)

```text
Scriptura/
├── crates/
│   ├── scriptura-core/       # Core domain types, progress tracking, and error handling[cite: 22]
│   ├── scriptura-system/     # Hardware detection, topology, and thread placement[cite: 22]
│   ├── scriptura-texts/      # Sealed text loading and SHA-256 integrity verification[cite: 22]
│   ├── scriptura-els/        # Core 1D ELS search algorithm and normalization[cite: 22]
│   ├── scriptura-matrix/     # Grid layout and geometry for 2D matrix view[cite: 22]
│   ├── scriptura-stats/      # Text scrambling algorithms and empirical statistics[cite: 22]
│   ├── scriptura-notebooks/  # Saved research records and provenance logging[cite: 22]
│   ├── scriptura-app/        # Workflow orchestrator and application services[cite: 22]
│   └── scriptura-gui/        # Immediate-mode desktop interface (egui/eframe)[cite: 22]
├── docs/                     # Technical documentation, user manual, and guides[cite: 22]
└── packaging/                # Installer scripts (NSIS) and distribution assets[cite: 22]
