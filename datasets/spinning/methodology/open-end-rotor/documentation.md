# Documentation

> Part of [Open End Rotor Methodology](README.md)

This section describes the construction of a parametric life cycle inventory (LCI) for **open-end (OE) rotor-spun yarn**, covering multiple fibre families and yarn fineness classes. The aim is to provide a transparent, literature-based module that can be used consistently across product LCAs and in parallel with the ring-spun model.

---

## 1. Scope and functional unit

- **Process:** Open-end rotor yarn production, including preparation, spinning and winding.
- **Functional unit:** 1 kg of finished OE yarn at the spinning mill gate.
- **System boundaries (foreground):**
  - Electricity consumption in the OE line (opening, cleaning, carding/drawing where relevant, rotor spinning and winding, including auxiliaries where covered by sources).
  - Lubricant input and waste oil output.
  - Yarn waste/losses (sliver and yarn).
  - Plastic bobbins/carriers and their end-of-life.
  - Capital goods (machines and buildings).
- **Background data:** Linked to standard LCI databases (e.g. ecoinvent/EF 3.1) via generic market processes (GLO/RoW), as in the ring-spun model.

**Water use** is not modelled explicitly for the OE spinning step; for all materials, process water is set to zero in the foreground, in line with the dry-process character of the technology.

Capital goods, plastic bobbin usage and associated waste flows are **harmonised with the ring-spun model** (Section 7), to maintain consistency across spinning technologies.

---

## 2. Inventory grid: materials x yarn fineness

The OE model is defined on a discrete grid combining:

- **Yarn fineness:** 40--600 dtex, using the same industrially relevant list as the ring module, extended down to 40 dtex for OE:
  - 40, 45, 50, 60, 70, 80, 83, 90, 100, 110, 120, 130, 140, 148, 150, 160, 169, 170, 180, 190, 197, 200, 210, 220, 230, 240, 250, 260, 270, 280, 290, 300, 320, 340, 360, 380, 400, 420, 440, 460, 480, 500, 520, 540, 560, 580, 600 dtex.

- **Yarn types / fibre families actually used in OE rotor spinning:**
  - Cotton (100%).
  - CVC (cotton-rich blends).
  - PC (polyester--cotton).
  - Cotton / man-made generic blends.
  - Wool / man-made blends.
  - Linen blends.
  - Polyester (PET, PBT, PTT, PLA, etc.).
  - Generic poly blends.
  - Acrylic, modacrylic, PAN.
  - Polyamides (Nylon 6, 6.6, PA11, PA12, ...).
  - Polyamide blends.
  - MMCFs (rayon, viscose, lyocell).
  - Silk blends (spun silk).

Each (yarn type, dtex) combination corresponds to one LCI row. Together, these form the OE rotor section of the spinning database, aligned structurally with the 875-dataset ring-spun grid.
