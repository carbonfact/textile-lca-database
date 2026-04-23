# Spinning

> Lifecycle assessment datasets for yarn and filament production across ring spinning, open-end rotor, and filament spinning technologies for all major fibre types.

> ⚠️ **Under active revision — refreshed release expected 2026-04-24.** Methodology, inventory, and scores in this folder are being rebuilt. Values below may not match the next release; please wait for the next update before re-using results.

**159 datasets** | Functional unit: 1 kg yarn | All 16 EF 3.1 impact indicators

## Process Categories

| Technology | Datasets | Fibre Families | Description |
|------------|----------|---------------|-------------|
| [Ring Spinning](ring-spinning.md) | 90 | 10 | Dominant staple yarn method. High-quality yarns for knitting and weaving. Higher energy per kg but finer, stronger yarns. |
| [Open-End Rotor](open-end-rotor.md) | 54 | 6 | Faster, more energy-efficient alternative. Bulkier yarns for casual knit and woven fabrics. |
| [Filament Spinning](filament-spinning.md) | 15 | 8 | Melt, wet, and dry spinning of continuous filaments. Lower energy intensity per kg. |

## Fibre Types

| Fibre Family | Ring Spinning | Open-End Rotor | Filament |
|-------------|:---:|:---:|:---:|
| Cotton (carded) | | ✓ | |
| Cotton Combed -- Knitting | ✓ | | |
| Cotton Combed -- Weaving | ✓ | | |
| Polyester (PET, PBT, PTT, PLA) | ✓ | ✓ | ✓ |
| Polyamide (Nylon 6, 6.6, PA 11, 12) | ✓ | ✓ | ✓ |
| Acrylic / Modacrylic / PAN | ✓ | ✓ | ✓ |
| MMCF (Rayon, Viscose, Lyocell) | ✓ | ✓ | ✓ |
| Elastane (Spandex/Lycra) | ✓ | | ✓ |
| Wool -- Woollen | ✓ | | |
| Wool -- Worsted | ✓ | | |
| Spun Silk | ✓ | ✓ | |
| Acetate / Triacetate | | | ✓ |
| Microfibers | | | ✓ |

## Methodology

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [impact-scores.csv](impact-scores.csv) | Emission factors (LCIA results) for 16 EF 3.1 indicators + DQR scores + **Input required (kg)** loss factor |
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible inventory |
