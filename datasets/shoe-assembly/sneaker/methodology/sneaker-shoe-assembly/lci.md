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

## 7. Contribution analysis

### 7.1 Stock fit (VN scenario, 0.658 kg CO₂-eq)

| Input | Amount | Unit | GWP (kg CO₂-eq) | Share |
|-------|-------:|------|------------------:|------:|
| **Electricity (medium voltage, VN)** | 0.454 | kWh | 0.233 | 35.4% |
| **Methyl ethyl ketone** | 0.028 | kg | 0.194 | 29.4% |
| Ethyl acetate | 0.014 | kg | 0.056 | 8.5% |
| Oxalic acid | 0.003 | kg | 0.052 | 7.9% |
| Corrugated board box (packaging) | 0.027 | kg | 0.036 | 5.4% |
| PU adhesive | 0.006 | kg | 0.030 | 4.5% |
| PU flexible foam | 0.004 | kg | 0.024 | 3.7% |
| Other (11 inputs) | | | 0.033 | 5.2% |

Stock fit is driven primarily by **electricity** (35%) and **methyl ethyl ketone** (29%). Together these two inputs account for nearly two-thirds of the process footprint. Methyl ethyl ketone (butan-2-one, CAS 78-93-3) has a high emission factor in ecoinvent 3.12 (~7.1 kg CO₂-eq/kg for RoW, ~6.3 for RER) — roughly 2× higher than acetone and 1.8× higher than ethyl acetate — due to petrochemical-intensive production from butane oxidation.

### 7.2 Stitching (VN scenario, 0.154 kg CO₂-eq)

| Input | Amount | Unit | GWP (kg CO₂-eq) | Share |
|-------|-------:|------|------------------:|------:|
| **Methyl ethyl ketone** | 0.009 | kg | 0.058 | 37.6% |
| **Ethyl acetate** | 0.013 | kg | 0.053 | 34.2% |
| Rosin size | 0.003 | kg | 0.010 | 6.3% |
| Synthetic rubber | 0.003 | kg | 0.009 | 6.0% |
| Methylcyclohexane | 0.003 | kg | 0.007 | 4.9% |
| LDPE granulate (packaging) | 0.002 | kg | 0.007 | 4.8% |
| Electricity (medium voltage, VN) | 0.010 | kWh | 0.005 | 3.4% |
| Other (3 inputs) | | | 0.004 | 2.9% |

Stitching is dominated by **solvents** (methyl ethyl ketone + ethyl acetate = 72%), with electricity playing a minor role (3.4%).

## 8. Limitations and open items

| Item | Status | Next step |
|------|--------|-----------|
| Physical footwear materials not included | By design | Material flows modelled separately and coupled later |
| NMVOC emissions uniform across processes | Simplification | Differentiate by abatement efficiency if data available |
| Chemical proxies may affect toxicity categories | Known limitation | Refine proxies as more specific datasets become available |
