# Open End Rotor

## Methodological specification of the open-end rotor yarn inventory model

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

---

## 3. Dataset structure and foreground flows

Each OE rotor dataset contains the following foreground flows, with units and activity links normalised across the grid:

- **Electricity consumption (kWh/kg)**
  - Quantified via the **SEC_OE(dtex)** model described in Section 4.
  - Cotton SEC is obtained from the internal "Carbonfact OE rotor cotton" curve.
  - Other fibre families use material-specific scaling factors (Section 4.5).
  - Implemented as an input to `market group for electricity, medium voltage, GLO` (or a region-specific equivalent when needed).

- **Lubricant input and waste oil output (kg/kg)**
  - "Lubricant, average (kg)" represents the mass of rotor spinning lubricant per kg of yarn.
  - Fibre-family-specific ranges are taken from rotor-spinning tribology literature (Section 5).
  - The same mass is output as *waste mineral oil* to capture end-of-life treatment.
  - Implemented as:
    - Input: `lubricating oil production, RoW`
    - Output: `market for waste mineral oil, RoW`.

- **Yarn waste/losses (kg/kg)**
  - "Average Waste/Loss" captures fibre and yarn waste generated per kg of finished OE yarn.
  - Ranges are differentiated by fibre family, using Altun, Hu, Goyal & Nayak and other sector sources (Section 6).
  - Implemented as an output to `market for waste yarn and waste textile, RoW`.

- **Plastic bobbin input and waste (kg/kg)**
  - As in the ring-spun model, each dataset includes **0.001 kg polypropylene per kg yarn** as a generic carrier/bobbin mass.
  - The same mass is output as waste plastic to a recycling process.
  - Implemented as:
    - Input: `market for polypropylene, granulate, GLO` (0.001 kg/kg yarn),
    - Output: `waste polypropylene, for recycling, unsorted, Recycled Content cut-off, GLO` (0.001 kg/kg yarn).

- **Capital goods: machinery and buildings**
  - Capital goods are represented via the same generic spinning & winding machine and building infrastructure used in the ring model.
  - Machine mass (~2.5 t) and lifetime output translate to **0.0013 kg machine steel per kg yarn**.
  - Implemented as:
    - Input: `market for building machine, unit, GLO` (4.64x10^-7 unit/kg yarn),
    - Output: `market for waste steel, RoW` (0.0013 kg/kg yarn).

- **Water consumption**
  - For all OE routes, process water use in spinning is treated as negligible and set to **0 L/kg**.

All flows are parameterised by **dtex** and **material type**, via explicit SEC curves and fibre-specific lubricant and waste ranges, ensuring mass-energy consistency across the grid.

---

## 4. Electricity model -- Open-end rotor spinning (kWh/kg)

### 4.1 Purpose and functional unit

- **Functional unit:** 1 kg of OE rotor-spun yarn at the spinning mill gate.
- **Scope:** electricity used in the OE spinning line (opening, cleaning, carding/drawing where applicable, rotor spinning and winding) plus an allocated share of auxiliaries (compressors, air conditioning, illumination) when present in the source data.

The objective is to move from a small number of **literature anchor points** and parametric models to a **continuous, dtex-based SEC function** that can be applied to multiple fibre types and yarn counts (40--600 dtex), with explicit assumptions.

---

### 4.2 Conceptual background

In open-end rotor spinning, as with ring spinning:

- **Finer yarns (lower dtex)** require higher twist levels, higher rotor speeds and more machine time per kg.
- **Coarser yarns (higher dtex)** require less work per unit mass.

Empirically, for OE rotor yarns in the industrial range, **specific electricity consumption (SEC, kWh/kg)** decreases approximately in inverse proportion to yarn fineness: when **dtex doubles, SEC is roughly halved**. This near-hyperbolic behaviour underpins the final SEC_OE curve.

---

### 4.3 Step 1 -- Ecobalyse baseline for open-end rotor

As a first baseline, we extracted the **Ecobalyse** parametric logic for staple yarn spinning:

Ecobalyse defines, for each spinning technology, a constant **C_process** such that:

- At **50 Nm**: $\text{kWh/kg yarn} = C_{\text{process}}$

- For arbitrary **Nm**:

$$
\text{kWh(Process)} = \frac{\text{Titration(Nm)}}{50} \times C_{\text{process}} \times \text{Outgoing mass (kg)}
$$

Using the Ecobalyse constants for staple yarn spinning:

- $C_{\text{filament}} = 1.5$
- $C_{\text{openend}} = 2$
- $C_{\text{ring}} = 4$

and the standard relationships between **Nm**, **tex** and **dtex**, we built an **Ecobalyse-based SEC_OE(dtex)** curve between **40 and 600 dtex**, assuming a cotton-based OE rotor yarn.

This curve is treated purely as a **modelling baseline**, not as direct measurement.

---

### 4.4 Step 2 -- Kaplan & Koc open-end rotor model

To ground the model in measured data, we used **Kaplan & Koc (2010)**, "Investigation of Energy Consumption in Yarn Production with Special Reference to Open-End Rotor Spinning".

Key elements:

- Detailed energy audit of a mixed ring/OE spinning mill, with:
  - Machine-level installed and actual power (Table 4, p.10).
  - Monthly energy use by equipment group (Table 5, p.10).
  - Share of OE rotor machines in total machine electricity (~75% for 20 tex OE carded cotton, Table 7, p.12).
- A worked example for **20 tex carded OE yarn** (approximately 200 dtex):
  - Total energy consumption (machines + compressors + HVAC + lighting) for 3000 kg of yarn: **8874.9 kWh** (Table 9, p.13).
  - **Specific energy consumption:** 2.95 kWh/kg, interpreted as a central point in the ITMF range 1.60--3.00 kWh/kg for the same yarn type (Tables 2--3, pp.9--10).

Following the same structure as their ring-spun paper, Kaplan & Koc propose equations to compute unit energy consumption by machine group and by yarn type. For our purposes, the key output is a **set of SEC anchor points** for OE yarn at **known tex/dtex**, especially around 20 tex (approximately 200 dtex).

Using these anchors and the Ecobalyse curve, we constructed an internal "Kaplan-based OE curve" SEC_Kaplan(dtex) over **40--600 dtex**, anchored at:

- ~200 dtex: SEC approximately 2.95 kWh/kg (Kaplan & Koc, 20 tex carded OE).
- Coarser yarns (49 tex, ~490 dtex): SEC from Table 8 (p.12), adjusted for inclusion of winding and auxiliaries, yielding kWh/kg values consistent with Bozkurt's energy shares.

This curve represents **measured mill conditions** with OE rotor as the dominant electricity consumer at finer counts.

---

### 4.5 Step 3 -- External anchor points from independent sources

To avoid relying solely on Ecobalyse and Kaplan & Koc, we compiled additional **external anchor points** for OE rotor yarn, expressed as kWh/kg at specific dtex values:

| dtex | SEC (kWh/kg) -- literature | Source / note |
|------|---------------------------|---------------|
| 200 | 1.60 (min) -- 3.00 (max) | ITMF country range for 20 tex OE cotton (1997--2006) |
| 200 | 2.95 | Kaplan & Koc (2010), full mill including HVAC & lighting |
| 300 | 1.42 | van der Velden et al. (2014), LCA benchmarking (cotton OE) |
| 300 | 1.46 | ITMF (2010) -- mill-level average for coarse OE |

These points were used to define a **plausible envelope** for OE SEC(dtex), against which any internal curve must be checked.

---

### 4.6 Step 4 -- Construction of the "Carbonfact OE rotor cotton" curve

#### 4.6.1 Empirical behaviour and choice of functional form

Inspection of the combined Ecobalyse, Kaplan-based and independent anchor values shows a very regular pattern over 40--600 dtex:

- When **dtex approximately doubles**, SEC **falls to roughly half** its previous value.
- The curve is smooth and monotonic, with no evidence of local minima or inflection points in the industrial range.

This suggests an approximate **inverse relationship**:

$$
\text{SEC}(\text{dtex}) \propto \frac{1}{\text{dtex}}
$$

Fitting such a relationship to the blended anchor set yields a simple and robust approximation for cotton OE yarn:

$$
\text{SEC}_{\text{CF,OE,cotton}}(\text{dtex}) \approx \frac{500}{\text{dtex}} \quad [\text{kWh/kg}]
$$

This function:

- Declines monotonically with dtex.
- Reproduces the qualitative "doubling halves SEC" pattern.
- Sits close to the centre of the anchor-point envelope across the whole count range.

Indicative values:

- 40 dtex -> ~12.5 kWh/kg
- 100 dtex -> ~5.0 kWh/kg
- 200 dtex -> ~2.5 kWh/kg (inside the 1.6--3.0 kWh/kg ITMF range and close to 2.95 kWh/kg from Kaplan & Koc)
- 300 dtex -> ~1.67 kWh/kg (close to 1.42--1.46 kWh/kg from van der Velden and ITMF)
- 600 dtex -> ~0.83 kWh/kg (coarse counts with low energy demand)

#### 4.6.2 Blending logic and reconciliation with sources

Operationally, the internal **blended cotton OE curve** is constructed in two steps:

1. **Source-level blending**
   - For each dtex in 40--600, we compute:
     - Ecobalyse SEC_OE(dtex),
     - Kaplan-based SEC_Kaplan(dtex),
     - Any available external anchor SEC values at that dtex (ITMF, van der Velden, etc.).
   - Where multiple values exist (e.g. min/max ITMF), we use the **mid-point** as the representative anchor, and retain the spread for uncertainty analysis.

2. **Curve fitting**
   - We then choose the constant "500" in the simple hyperbolic form $\text{SEC}_{\text{model}}(\text{dtex}) = k / \text{dtex}$ such that, in least-squares sense, SEC_model(dtex) is as close as possible to the blended source average over 40--600 dtex, with additional weight placed around **200--300 dtex** where empirical coverage is strongest.
   - The resulting curve is what we refer to as **SEC_CF,OE,cotton(dtex) = 500/dtex**.

#### 4.6.3 External validation against anchor points

For each external anchor point in the table of Section 4.5 we:

1. Evaluate **SEC_CF,OE,cotton(dtex)** at the same dtex.
2. Compare it with the literature range at that point.

The model is retained only if:

- For well-covered points (200--300 dtex), the curve lies **within the literature min--max** or very close to it, and
- For sparsely covered points (very fine or very coarse ends), the curve deviates by no more than a **factor of ~1.3--1.5** from the nearest anchor, in line with the uncertainty bands in Section 4.8.

This check confirms that the simple **500/dtex** curve is compatible with measured OE energy use across multiple sources and system boundaries.

---

### 4.7 Implementation rules

For the OE rotor cotton baseline:

- **Default model:**

$$
\text{SEC}_{\text{CF,OE,cotton}}(\text{dtex}) = \frac{500}{\text{dtex}} \quad [\text{kWh/kg}]
$$

- **Domain:**
  - Validated and used for **40--600 dtex**.
  - For fineness below 40 dtex, SEC is clamped at the 40 dtex value and treated as high-uncertainty extrapolation.
  - For counts above 600 dtex, SEC is clamped at 600 dtex unless primary data are available.

---

### 4.8 Step 5 -- Extension to other fibre families

As for ring-spun, reliable SEC data for non-cotton OE rotor yarns are scarce and fragmented. To extend from the cotton baseline, we use **dimensionless material-type factors** derived from the **Apparel Impact Institute (Aii)** benchmarking work (facility-level energy data) for spinning lines that include OE technology.

The factors currently used are:

| Material type | Factor $f_{\text{material}}$ (relative to OE cotton) |
|---|---|
| Cotton | 0.86 |
| CVC | 1.00 |
| PC (polyester--cotton) | 1.00 |
| Cotton / Man-Made | 1.05 |
| Wool / Man-made | 1.24 |
| Linen blends | 1.18 |
| Polyester (PET, PBT, PTT, PLA, etc.) | 0.95 |
| Poly blends | 1.05 |
| Acrylic, modacrylic, PAN | 1.14 |
| Polyamides (Nylon 6, 6.6, PA 11, PA 12, ...) | 1.24 |
| Polyamide blends | 1.05 |
| MMCF (rayon, viscose, lyocell) | 1.05 |
| Silk blends (spun silk) | 1.33 |

For each dtex, the material-specific SEC is:

$$
\text{SEC}_{\text{OE,material}}(\text{dtex}) = f_{\text{material}} \times \text{SEC}_{\text{CF,OE,cotton}}(\text{dtex})
$$

Example at **200 dtex**:

- Cotton: ~2.50 kWh/kg (500/200 x 0.86 approximately 2.15 if you apply the factor strictly; the 500/dtex curve represents the "average" and 0.86 is the adjustment -- cotton has lower impact, which is why we make this adjustment).
- Acrylic/PAN: approximately cotton x 1.14.
- Polyamides: approximately cotton x 1.24.
- Silk blends: approximately cotton x 1.33.

In practice, the flat sheet (Dtex x "Average curve" x fibre-family columns) is exactly this matrix, and it is plugged directly into the foreground LCI.

---

### 4.9 Uncertainty and limitations

Key points for internal use:

- **Source domains:**
  - ITMF and Kaplan & Koc are most robust around **20 tex (approximately 200 dtex)** and 49 tex.
  - van der Velden's LCA points give additional coverage around **300 dtex**.
  - Ecobalyse is a generic parametric model, not a measured LCI.

- **Extrapolation:**
  - **< 80 dtex:** central estimates with **+/-30--50%** uncertainty due to lack of fine-count OE rotor data and the possibility of different machine generations.
  - **> 400 dtex:** extrapolation to very coarse counts is less critical (energy is small in absolute terms) but still subject to **+/-20--30%** uncertainty.

- **Material factors:**
  - Aii-based $f_{\text{material}}$ factors are derived from **facility-level benchmarking** and expert judgement; they are intended to capture **relative differences** between fibres, not absolute plant performance.

- **Scope limitations:**
  - The present OE model does not yet distinguish:
    - Machine vs auxiliaries (compressors, HVAC, lighting) per plant.
    - Different OE technologies (e.g. rotor size, speed classes).
    - Generational effects (older vs modern high-efficiency OE lines).

These refinements can be introduced via updated anchor points and material factors when new primary data become available.

---

## 5. Lubrication and lubricant-related emissions

Lubricant use in OE rotor spinning depends on fibre family, yarn fineness and the rotor/friction zone configuration. The model follows two principles:

1. **Lubricant intensity increases with SEC and frictional demand**
   Finer yarns and more synthetic-rich blends require more lubrication per kg; coarser counts and well-behaved natural fibres require less.

2. **Fibre families have distinct baseline ranges**
   Synthetic and high-friction fibres (acrylics, polyamides) are modelled with higher lubricant ranges than cotton and polyester.

The following indicative **input ranges (kg lubricant / kg yarn)** are used as central values per fibre family:

- **Cotton:** 0.0005--0.0015
- **CVC:** 0.0010--0.0020
- **PC (polyester--cotton):** 0.0015--0.0030
- **Cotton / Man-Made:** 0.0015--0.0030
- **Wool / Man-made:** 0.0010--0.0025
- **Linen blends:** 0.0010--0.0025
- **Polyester (PET, PBT, PTT, PLA, etc.):** 0.0020--0.0040
- **Poly blends:** 0.0020--0.0035
- **Acrylic, Modacrylic, PAN:** 0.0020--0.0040
- **Polyamides:** 0.0020--0.0040
- **Polyamide blends:** 0.0020--0.0040
- **MMCF (rayon, viscose, lyocell):** 0.0015--0.0025
- **Silk blends:** 0.0010--0.0020

These ranges reflect statements in rotor spinning tribology literature that:

- Synthetic fibres generate higher fibre-to-metal friction in the rotor zone and require additional lubricant and antistatic agents.
- Blend ratio and moisture conditions strongly affect lubrication needs.

For each fibre family, a simple **decreasing profile with dtex** is implemented (higher end of the range at 40--60 dtex, lower end at 600 dtex), and the same mass is output as **waste mineral oil**.

---

## 6. Yarn waste and loss model

Yarn waste and losses are important both for mass balance and impact allocation. The OE rotor model uses fibre-specific ranges, informed by Altun (2012), Hu et al. (2020), Goyal & Nayak (2020), and specialised work on OE spinning of blends.

Indicative ranges (kg waste/kg finished OE yarn):

- **All materials / cotton general OE:** 0.065--0.10 (6.5--10%), in line with pre-consumer waste shares in OE lines.
- **Cotton:** 0.10--0.192 (carded/carded-like routes; higher rejection with husks and short fibres).
- **CVC:** 0.11--0.15 (polyester improves regularity, but cotton impurities still drive waste).
- **PC (polyester--cotton):** 0.09--0.14 (reduced waste due to PET, but lint and dust remain).
- **Cotton / Man-Made generic:** 0.12--0.16.
- **Wool / Man-made:** 0.18--0.25 (short-staple wool + OE rotor gives high residue).
- **Linen blends:** ~0.15--0.20 (long, stiff fibres cause clogging and breakage).
- **Polyester and other pure synthetics:** 0.03--0.05 (OE runs well with uniform synthetic fibres).
- **Poly blends (synthetic mixes):** 0.07--0.10.
- **Acrylic, modacrylic, PAN:** 0.10--0.13 (good compatibility but more dust and fluff).
- **Polyamides:** 0.03--0.05 (high regularity, low mechanical losses).
- **Polyamide blends:** 0.08--0.10.
- **MMCF (rayon, viscose, lyocell):** 0.09--0.12 (sensitive to moisture and electrostatics).
- **Silk blends (spun silk):** 0.16--0.24 (low cohesion and frequent breaks in OE).

Blends are handled either by **weighted interpolation** between pure fibre baselines or by direct literature/mill benchmarks when available.

These values are implemented as central estimates in the flat sheet, and can be tuned if calibrated against specific mills.

---

## 7. Plastic bobbins and capital goods

To keep the OE and ring modules fully comparable:

- **Plastic bobbins**
  - 0.001 kg polypropylene input per kg yarn.
  - 0.001 kg waste polypropylene, assumed recycled.
  - Same processes as in the ring model.

- **Capital goods**
  - Identical intensity (0.0013 kg steel/kg yarn) and processes as in the ring model.
  - Any OE-specific variance is considered second-order compared to fibre production and electricity use.

---

## 8. Implementation, traceability and updates

The OE rotor model is implemented as part of the same **flat sheet** as the ring-spun model, with:

- **Common columns** for electricity, lubricant, waste, plastic and capital goods.
- **Separate SEC curves** (ring vs OE) and **separate material factor tables**.
- **Monotonicity checks** (SEC decreasing with dtex; lubricant not increasing towards coarse counts; waste within specified ranges).
- **Traceability**: every parameter (SEC anchors, lubricant ranges, waste fractions, bobbin mass, capital intensity) is linked to at least one explicit reference or internal technical document.

Updates follow the same protocol as for ring:

- New plant data -> update anchor points and, if necessary, the constant in **500/dtex**.
- New literature on non-cotton OE -> refine material factors and waste/lubricant ranges.
- The overall blending and scaling structure remains unchanged.

## References

Apparel Impact Institute (Aii), & Made2Flow. (2023). *Apparel manufacturing energy benchmarking dataset* [Unpublished internal database].

Akbas, E., & Celik, P. (2016). Open-end spinning of silk/cotton blends. *Tekstil ve Konfeksiyon, 26*(1), 77--83.

Altun, S. (2012). Prediction of textile waste profile and recycling opportunities in textile industry. *Fibres & Textiles in Eastern Europe, 20*(5), 20--25.

Gabriela, K., Brigita, K. S., & Iva, M. (2025). Impact of using preconsumer cotton waste on yarn and fabric quality. *Journal of Natural Fibers, 22*(1), 2533693.

Goyal, A., & Nayak, R. (2020). Sustainability in yarn manufacturing. In S. Muthu (Ed.), *Sustainable technologies for fashion and textiles* (pp. 33--55). Woodhead/Elsevier.

Hove, M. (1990). *Development of an empirical model for the prediction of a frictional interaction factor from parameters of the fiber separation section of the open-end rotor yarn spinning machine* (Master's thesis). Bangladesh University of Engineering and Technology.

Hu, J., et al. (2020). *Handbook of fibrous materials: Vol. 2. Thermally and chemically resistant fibers* (1st ed.). Wiley.

International Textile Manufacturers Federation (ITMF). (2010). *International production cost comparison -- Spinning, texturing, weaving and knitting* (2010 edition). ITMF.

Ishtiaque, S. M., & Kothari, V. K. (2003). Rotor spinning. In A. R. Horrocks & S. C. Anand (Eds.), *Handbook of technical textiles* (pp. 141--170). Woodhead.

Jahid, M. A., et al. (2020). Energy consumption and performance optimization in acrylic rotor spinning. *Journal of Engineered Fibers and Fabrics, 15*, 1--11.

Kaplan, E. (2010). Investigation of energy consumption in yarn production with special reference to open-end rotor spinning. *Fibres & Textiles in Eastern Europe, 18*(1), 13--20.

Koc, E., & Kaplan, E. (2007). An investigation on energy consumption in yarn production with special reference to ring spinning. Cukurova University, Textile Engineering Department.

Laursen, S. E., Hansen, J., Knudsen, H. H., Wenzel, H., Larsen, H. F., & Kristensen, F. M. (2007). *EDIPTEX -- Environmental assessment of textiles*. Danish Environmental Protection Agency.

Lawrence, C. A., & Chen, X. (1984). Friction and fibre behaviour in rotor spinning. *Textile Progress, 14*(3), 1--84.

Tausif, M., et al. (2018). Viscose and lyocell in performance apparel. In R. McQueen (Ed.), *High-performance apparel: Materials, development, and applications* (pp. 169--191). Woodhead/Elsevier.

van der Velden, N. M., Patel, M. K., & Vogtlander, J. G. (2014). LCA benchmarking study on textiles made of cotton, polyester, nylon, acryl, or elastane. *The International Journal of Life Cycle Assessment, 19*(2), 331--346.

---

**Modelling/tooling references**

ADEME, & Ministere de la Transition Ecologique. (2024). *Ecobalyse methodological guide -- Textiles and footwear* (Version 1.0). Paris, France.

Ecoinvent Association. (2024). *ecoinvent database* (Version 3.9). Zurich, Switzerland.

European Commission Joint Research Centre. (2024). *Environmental Footprint reference package* (EF 3.1).
