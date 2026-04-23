# Life Cycle Inventory

> Part of [Sneaker Shoe Assembly Methodology](README.md)

## 6. Results (EF v3.1 — Climate Change)

Two electricity scenarios were modelled and compared using **ecoinvent 3.12** (cut-off):

- **VN**: market for electricity, medium voltage, Vietnam
- **GLO**: market group for electricity, medium voltage, GLO (global average)

GWP100 results per process (per pair):

| Rank | Process | GWP100 VN (kg CO₂-eq) | GWP100 GLO (kg CO₂-eq) | Delta |
|------|---------|----------------------:|------------------------:|------:|
| 1 | 8 - Stock fit | 0.658 | 0.425 | -35% |
| 2 | 9 - Assembly | 0.423 | 0.126 | -70% |
| 3 | 7 - Stitching | 0.154 | 0.149 | -3% |
| 4 | 6 - Nosew | 0.151 | 0.060 | -60% |
| 5 | 1 - Lamination | 0.133 | 0.133 | ~0% |
| 6 | 2 - Cutting | 0.048 | 0.065 | +36% |
| 7 | 3 - HF Welding | 0.058 | 0.017 | -71% |
| 8 | 4 - Screen Printing | 0.039 | 0.039 | ~0% |
| 9 | 5 - Insole | ~0 | ~0 | - |
| | **Total** | **1.664** | **1.014** | **-39%** |

Key findings:
- **Stock fit** is the dominant climate-change driver in both scenarios (~40% of total), driven by chemically intensive bonding/treatment systems and electricity for UV curing.
- Switching from VN to GLO electricity reduces total GWP by **39%** (1.664 → 1.014 kg CO₂-eq).
- Electricity-intensive processes (Assembly −70%, HF Welding −71%, Nosew −60%) are most sensitive to grid choice.
- Chemistry-dominated processes (Lamination, Screen Printing) are virtually unaffected.

## 7. Limitations and open items

| Item | Status | Next step |
|------|--------|-----------|
| Physical footwear materials not included | By design | Material flows modelled separately and coupled later |
| NMVOC emissions uniform across processes | Simplification | Differentiate by abatement efficiency if data available |
| Chemical proxies may affect toxicity categories | Known limitation | Refine proxies as more specific datasets become available |
