# Documentation

> Part of [Melt Spinning Methodology](README.md)

This section describes the construction of a parametric life cycle inventory (LCI) for **synthetic filament yarn production** (melt, dry, and wet spinning), covering multiple polymer families and process types. The aim is to provide a transparent, literature-based module that can be used consistently across product LCAs and in parallel with the staple spinning models.

---

## 1. Scope and functional unit

- **Process:** Synthetic filament yarn production via melt spinning, dry spinning or wet spinning, including extrusion, solidification, drawing, texturing (where applicable) and winding.
- **Functional unit:** 1 kg of finished filament yarn at the spinning mill gate.
- **System boundaries (foreground):**
  - Electricity consumption (extrusion, drawing, texturing, winding, auxiliaries).
  - Thermal energy (melt spinning only: barrel heating, melt pumps).
  - Lubricant (spin finish oil) input and waste oil output.
  - Process water consumption and wastewater generation.
  - Yarn waste/losses.
  - Plastic bobbins/carriers and their end-of-life.
  - Capital goods (machines and buildings).
- **Background data:** Linked to standard LCI databases (e.g. ecoinvent/EF 3.1) via generic market processes (GLO/RoW), as in the staple spinning models.

**Key difference from staple spinning:** Energy consumption is **independent of yarn fineness (dtex)** -- it scales with mass throughput (kg/hr), not with yarn count. This is a physics-based departure from the Ecobalyse Nm-proportionality used for ring and open-end spinning (see Section 4.2 for full justification).

---

## 2. Inventory grid: materials x process type x yarn fineness

The model is defined on a discrete grid combining:

- **Yarn fineness:** 45--600 dtex (same list as staple spinning models).
  - **Important:** Energy values are **constant across all dtex** for a given (material, process) combination. The dtex column serves as structural metadata for database compatibility.

- **Process types:**
  - **Melt spinning -- POY** (Partially Oriented Yarn): extrusion + partial drawing.
  - **Melt spinning -- FDY** (Fully Drawn Yarn): extrusion + full drawing.
  - **Melt spinning -- DTY** (Draw Textured Yarn): POY + texturing (energy-equivalent to FDY).
  - **Dry spinning:** solvent-based extrusion, solvent evaporation and recovery.
  - **Wet spinning:** solution spinning into coagulation bath + washing.

- **Material families / polymer types:**
  - **Melt spinning:** Polyester (PET, PBT, PTT, PLA, etc.), Polyamides (PA6, PA66, PA11, PA12), Acrylic/Modacrylic/PAN, Elastane (Spandex/Lycra/TPU), Acetate/Triacetate, Microfibers, Recycled PA 6.6.
  - **Dry spinning:** Generic extruder polymer (acetate, acrylic without steam utilities), Elastane.
  - **Wet spinning:** MMCF (Rayon, Viscose, Lyocell), Polyamide blends.

Each (polymer type, process type, dtex) combination corresponds to one LCI row. Together, these form the synthetic filament section of the spinning database, aligned structurally with staple spinning grids.
