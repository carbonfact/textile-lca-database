# Documentation

> Part of [Ring Spun Yarn Methodology](README.md)

This section describes the construction of a parametric life cycle inventory (LCI) for ring-spun yarn, covering multiple fibre families and yarn fineness classes. The aim is to provide a transparent, literature-based module that can be used consistently across product LCAs.

### 1. Scope and functional unit

- **Process:** Ring-spun yarn production, including preparation, spinning and winding.
- **Functional unit:** 1 kg of finished yarn, at the spinning mill gate.
- **System boundaries (foreground):** Electricity and thermal energy, lubrication, yarn waste/losses, plastic bobbins and capital goods (machines and buildings).
- **Background data:** Linked to standard LCI databases (e.g. ecoinvent/EF3.1) via generic market processes (GLO/RoW).

The model is explicitly foreground-oriented: it parameterises the key mass and energy flows that are sensitive to yarn fineness and fibre type, while delegating upstream and downstream processes to background databases.

### 2. Inventory grid: materials x yarn fineness

The model is defined on a discrete grid combining:

- **Yarn fineness:** 45--600 dtex, in industrially relevant steps (45, 50, 60, ..., 600 dtex).
- **Yarn types / fibre families:**
  - Generic **"Baseline ring-spun cotton"** (formerly "Average").
  - 100% cotton (generic ring yarn).
  - Acrylic / modacrylic / PAN.
  - Cotton / man-made (50/50).
  - CVC (cotton + polyester, 50/50).
  - Elastane (spandex/lycra).
  - MMCFs (rayon, viscose, lyocell).
  - PC-acrylic blends.
  - Generic poly blends.
  - Polyamides (Nylon 6, 6.6, PA11, PA12, ...).
  - Polyamide blends.
  - Polyester (PET, PBT, PTT, PLA, etc.).
  - Silk blends (spun silk).
  - Worsted wool.
  - Woollen wool.
  - Cotton ring yarn differentiated by preparation and end-use:
    - Combed -- knitting.
    - Combed -- weaving.
    - Carded -- knitting.
    - Carded -- weaving.

Each (yarn type, dtex) combination corresponds to one LCI row. The full grid comprises **875 individual process datasets**.
