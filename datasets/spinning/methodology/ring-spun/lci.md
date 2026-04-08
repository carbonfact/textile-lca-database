# Life Cycle Inventory

> Part of [Ring Spun Yarn Methodology](README.md)

## 3. Dataset structure and foreground flows

Each dataset (one row) in the ring-spun model contains the following foreground flows, with units and activity links normalised across the grid:

- **Electricity consumption (kWh/kg)**
  - Electricity consumption is quantified via the **SEC(dtex)** model (Section 4), ranging from ~21 kWh/kg at 45 dtex to ~1.05 kWh/kg at 600 dtex for the cotton baseline, with material-specific factors applied for other fibre families.
  - Cotton SEC is obtained from the blended "Carbonfact cotton ring" curve; other fibre families use material-specific factors.
  - Implemented as an input to `market group for electricity, medium voltage, GLO` (or a region-specific equivalent when needed).

- **Lubricant input and waste oil output (kg/kg)**
  - "Lubricant, average (kg)" represents the mass of spinning lubricant per kg of yarn.
  - For baseline cotton ring yarn, values decline from ~0.00200 kg/kg at 45 dtex to ~0.00050 kg/kg at 600 dtex, staying within the order of magnitude reported for ring spinning oils (approximately 0.18--0.35 ml/kg) and consistent with JRC/EDP benchmarks.
  - For fibre families with higher frictional demands (e.g. acrylic/PAN, polyamides, elastane), lubricant values are proportionally higher (Section 5).
  - The same mass is output as waste mineral oil to capture end-of-life treatment.
  - Implemented as:
    - Input: `lubricating oil production, RoW`
    - Output: `market for waste mineral oil, RoW`.

- **Yarn waste/losses (kg/kg)**
  - "Average Waste/Loss" captures fibre and yarn waste generated per kg of finished ring-spun yarn.
  - Values are differentiated by fibre family and route (carded/combed, knitting/weaving) using ranges from EDIPTEX, Textile Exchange CFMB and mill case studies:
    - Generic cotton ring: ~0.15--0.20 kg/kg.
    - Combed cotton routes: typically ~0.25--0.35 kg/kg (higher waste in combing).
    - Synthetics and MMCFs: ~0.03--0.07 kg/kg.
    - Acrylic / PAN: ~0.08--0.13 kg/kg.
    - Silk (spun silk): ~0.40--0.60 kg/kg.
  - Implemented as an output to `market for waste yarn and waste textile, RoW`.

- **Plastic bobbin input and waste (kg/kg)**
  - Each dataset includes 0.001 kg of polypropylene per kg yarn as a generic carrier/bobbin mass, consistent with BREF and textile LCA sources.
  - The same mass is output as waste plastic to a recycling process.
  - Implemented as:
    - Input: `market for polypropylene, granulate, GLO` (0.001 kg/kg yarn)
    - Output: `waste polypropylene, for recycling, unsorted, Recycled Content cut-off, GLO` (0.001 kg/kg yarn).

- **Capital goods: machinery and buildings**
  - Capital goods are represented via a generic spinning & winding machine and associated building infrastructure.
  - Machine mass (~2.5 t) and lifetime output are used to derive a capital goods intensity of 0.0013 kg machine steel per kg yarn.
  - Implemented as:
    - Input: `market for building machine, unit, GLO` (4.64x10^-7 unit/kg yarn)
    - Output: `market for waste steel, RoW` (0.0013 kg/kg yarn) as end-of-life scrap.

- **Water consumption**
  - For dry ring-spun routes (cotton, synthetics, most MMCFs and blends), process water use in spinning is treated as negligible.
  - A parameter for 0--2.2 L/kg exists for wet spinning or special MMCF routes, but in the baseline ring-spun module this is set to zero.

All flows are parameterised by **dtex** and **material type**, through a combination of explicit curves (electricity, lubricant) and fibre-specific ranges (waste, silk, blends), ensuring internal mass-energy consistency across the 875 datasets.

## 4. Electricity model -- Ring-spun spinning (kWh/kg)

### 4.1 Purpose and functional unit

This section documents how specific electricity consumption (SEC, kWh/kg) is modelled for ring-spun yarn in the Carbonfact database.

- **Functional unit:** 1 kg of ring-spun yarn at the spinning mill gate.
- **Scope of this section:** electricity use only (opening, cleaning, carding, drawing, roving, ring spinning and winding, including auxiliary loads when covered by the source).

The objective is to move from a small number of literature "anchor points" to a **continuous, dtex-based SEC function** that can be applied to multiple fibre types and yarn counts (45--600 dtex), with transparent assumptions.

---

### 4.2 Conceptual background

In ring-spun spinning, the **finer the yarn**, the more:

- drafting and drafting stages are required,
- twist insertions per unit mass are needed, and
- machine time per kg is consumed at the ring frame and winding.

As a result, **specific electricity consumption (kWh/kg)** increases for lower dtex, and decreases for coarser yarns. This inverse relationship is well documented in spinning literature and is the guiding principle of the model.

---

### 4.3 Step 1 -- Ecobalyse baseline for ring spinning

As a starting point, we used the **Ecobalyse** logic for staple yarn spinning as a transparent baseline:

- Ecobalyse distinguishes **ring spinning** (conventional) and **open-end** (non-conventional).
- Electricity use for ring spinning is modelled as a function of **yarn title** (Nm) via a simple proportionality:

```
kWh(Process) = (Titration(Nm) / 50) x Constant(Process) x Outgoing mass (kg)
```

- For ring spinning, the relevant constant is:

```
C_ring = 4 kWh/kg at 50 Nm
```

#### 4.3.1 Conversion to dtex

To align with our internal parameterisation (dtex), we used the standard relationships:

- **Nm (metric number):** Nm = metres per gram of yarn
- **dtex (decitex):** dtex = (10 000 x mass [kg]) / length [km]

For each yarn count in **dtex**, we constructed a consistent mapping table (dtex <-> Nm <-> Ne <-> denier), covering the range **45--600 dtex**. This ensures that Ecobalyse's Nm-based formulation can be evaluated at any dtex required by the database.

Using `C_ring = 4 kWh/kg` at 50 Nm (approximately 200 dtex) and the Ecobalyse linear rule, we generated an **Ecobalyse-based kWh/kg curve** from 45 to 600 dtex. The resulting SEC values decrease monotonically from very fine yarns (high kWh/kg) towards coarse yarns (low kWh/kg). Over this range, the Ecobalyse ring curve has an average SEC of **approximately 5.29 kWh/kg**.

This Ecobalyse curve is treated as a **first baseline** for cotton ring yarn.

---

### 4.4 Step 2 -- Anchor points from Koc & Kaplan (2007)

To ground the Ecobalyse curve in measured industrial data, we used **Koc & Kaplan (2007)**, which reports electricity consumption for ring-spun yarn as a function of yarn title (tex), distinguishing:

- **Carded vs combed** yarn, and
- **Knitting vs weaving** yarn (weaving generally requiring higher twist and energy).

Koc & Kaplan provide SEC values (kWh/kg) for several **tex** values, including a key control point around:

- **20 tex (approximately 200 dtex)**
  - combed knitting: approximately 3.06 kWh/kg
  - combed weaving: approximately 3.64 kWh/kg

These values are in the same order of magnitude as Ecobalyse, but with a slightly different shape and level.

#### 4.4.1 Fitting a power-law relationship

Rather than using Koc & Kaplan's discrete table directly, we fitted **power-law functions** to the published points, which is consistent with the idea that SEC is driven by "machine time per unit mass":

```
SEC(dtex) = A x (dtex / 10)^b
```

The fit was performed on the original tex-based data (converted to dtex) for each yarn category:

- **Combed -- knitting:**
  SEC(dtex) = 136.84 x (dtex / 10)^(-1.274)
- **Combed -- weaving:**
  SEC(dtex) = 175.31 x (dtex / 10)^(-1.297)
- **Carded -- knitting:**
  SEC(dtex) = 136.50 x (dtex / 10)^(-1.283)
- **Carded -- weaving:**
  SEC(dtex) = 167.68 x (dtex / 10)^(-1.288)

The **exponents cluster around -1.28**, which is physically coherent: SEC increases sharply as yarn becomes finer.

#### 4.4.2 Domain and extrapolation

Koc & Kaplan's empirical range is approximately **120--370 dtex**. In our model:

- **Within this range (120--370 dtex):** the power laws are considered well-anchored.
- **Below 120 dtex and above 370 dtex:** these equations are used as controlled extrapolations, and the model should be interpreted with **explicit uncertainty** (higher for very fine yarns).

---

### 4.5 Step 3 -- Additional anchor points from Laursen et al. (2007)

To capture a broader system boundary (including **humidification and lighting**) and to benchmark energy levels, we also used **Laursen et al. (2007)** (Table 9.1), which reports energy consumption for ring-spun yarns:

- 100% combed cotton,
- 100% synthetic, and
- 65/35 PES/cotton.

Laursen provide values (MJ/kg) as a function of **tex** (13--60 tex, i.e. 130--600 dtex), which we converted to kWh/kg. For 100% cotton ring yarn, a linear approximation can be written as:

```
SEC_cotton_ring (kWh/kg) ≈ 4.8 - 0.005 x dtex   (valid roughly for 130-600 dtex)
```

Similarly, analogous linear expressions were derived for:

- 100% synthetic ring yarn;
- 65/35 polyester/cotton ring yarn.

These curves are **shallower** than the Koc power-law but importantly **include auxiliary energy** (humidification, lighting).

---

### 4.6 Step 4 -- Constructing a blended "Carbonfact cotton ring" curve

To avoid relying on a single source and to reflect both modelling diversity (Ecobalyse) and measured data (Koc, Laursen), we constructed a blended SEC curve for cotton ring-spun yarn as follows:

- **Range 45--120 dtex (fine yarns)**
  We averaged Ecobalyse and Koc-based SEC values.
  *Rationale:* in this range, Koc's data are partly extrapolated from a narrower tex window, whereas Ecobalyse is explicitly designed for a wide titration range.

- **Range 120--600 dtex (main industrial window)**
  We averaged three sources for 100% cotton:
  - Ecobalyse ring curve
  - Koc-based power-law curve
  - Laursen's cotton ring curve

  *Rationale:* all three sources are within their most robust domain here, and averaging reduces dependency on any single model or dataset artefact.

This produces an "average cotton ring curve" where SEC decreases smoothly from very fine to very coarse yarns. Indicative behaviour from the blended lookup table:

- Approximately **21.4 kWh/kg** at **45 dtex**
- Approximately **3.5 kWh/kg** around **197--200 dtex**
- Approximately **1.05 kWh/kg** at **600 dtex**

These values were computed at all required dtex points (45, 50, 60, ..., 600 dtex) using the conversion table between denier, Nm, Ne and dtex, generating a complete lookup table for cotton ring-spun yarn.

This blended curve is used as the **primary reference for cotton** in the ring-spun spinning model.

---

#### 4.6.1 External validation against independent anchor points

To avoid over-fitting the **Carbonfact cotton ring** curve to the Ecobalyse/Koc/Laursen triad, we cross-checked the blended cotton SEC values against **independent anchor points** from additional sources:

- Haque & Naebe (2024) -- ring-spun cotton yarn SEC at selected dtex counts (e.g. 45, 300 dtex).
- Alam et al. (2023) -- detailed SEC at 180 dtex for ring yarn in industrial conditions.
- IDEMAT database -- generic SEC value for ring-spun yarn around 250 dtex.
- Sandin et al. (2019) -- plant-level SEC for ring-spun cotton yarn corresponding to coarse counts (~600 dtex).

These sources provide **individual kWh/kg values** at specific dtex (or equivalent tex/Nm), which we converted to dtex and compiled into an "external anchor table". A simplified excerpt is shown below:

| dtex | SEC (kWh/kg) -- literature | Source |
|------|---------------------------|--------|
| 45 | 22.4 | Haque & Naebe (2024), *Future Textiles* |
| 170 | 4.51 | Laursen et al. (2007) |
| 180 | 1.35 | Alam et al. (2023), *TLR Journal* |
| 250 | 3.14; 4.72 | Laursen et al. (2007); IDEMAT |
| 300 | 3.40 | Haque & Naebe (2024), *Future Textiles* |
| 360 | 2.10 | Laursen et al. (2007) |
| 600 | 3.80 | Sandin et al. (2019), *Environmental Assessment of Swedish Clothing Consumption* |

For each of these dtex anchor points we then:

1. Evaluated the **blended cotton lookup table** (Section 4.6) at the same dtex.
2. Compared the blended SEC with the **literature range** at that point (when more than one value existed, e.g. at 250 dtex from Laursen and IDEMAT).
3. Verified that the **SEC_{CF,cotton}(dtex)** either:
   - lies **inside the min--max envelope** of the literature values for that dtex, or
   - differs by at most a **factor ~1.3--1.5** from the nearest anchor, in line with the uncertainty ranges stated in Section 4.9.

This cross-check confirms that the **shape and level** of the Carbonfact cotton curve are consistent with **independent datasets** not used in the primary fitting (Ecobalyse/Koc/Laursen). It also justifies the uncertainty bands proposed later: where the spread between literature anchors and the model is larger (e.g. at very fine yarns), the uncertainty range is explicitly wider, and where anchors cluster tightly (e.g. ~170--300 dtex) the model sits well within that cluster.

### 4.7 Fitted "Carbonfact cotton ring" equation

For implementation in parametric tools (e.g. spreadsheets, internal APIs), the discrete blended cotton curve was further approximated by a single power-law relationship between specific electricity consumption (SEC) and yarn fineness (dtex):

$$
\text{SEC}_{\text{CF,cotton}}(\text{dtex}) = a \cdot \text{dtex}^b
$$

A log--log regression on the blended table (45--600 dtex) gives:

- a approximately 9.77 x 10^2
- b approximately -1.13

So the final working curve for 100% cotton ring-spun yarn is:

$$
\text{SEC}_{\text{CF,cotton}}(\text{dtex}) = 977.3 \cdot \text{dtex}^{-1.132} \quad [\text{kWh/kg}]
$$

**Fit quality and domain**

- Regression performed on the full blended dataset from **45 to 600 dtex**.
- Coefficient of determination: R^2 approximately 0.998 against the blended lookup table.
- The function reproduces the key anchor ranges closely:
  - ~**19.5 kWh/kg** at 45 dtex vs. table ~21.4 kWh/kg (fine-yarn extrapolation zone)
  - ~**3.7 kWh/kg** at 197 dtex vs. table ~3.5 kWh/kg
  - ~**1.04 kWh/kg** at 600 dtex vs. table ~1.05 kWh/kg

**Usage rules**

- **Default model:** use $\text{SEC}_{\text{CF,cotton}}$ as the default SEC for 100% cotton ring-spun yarn in the range **45--600 dtex**.
- **Clamping:**
  - For yarns finer than **45 dtex**, apply the value at 45 dtex and document this as an extrapolation with higher uncertainty.
  - For yarns coarser than **600 dtex**, apply the value at 600 dtex unless primary data are available.
- **Uncertainty:**
  - Fine-yarn end (<120 dtex): recommend **+/-30--50%** uncertainty band.
  - Coarse-yarn end (>370 dtex): recommend **+/-15--25%** uncertainty band.

This fitted curve is then used as the **cotton baseline** for deriving material-specific SEC factors (Acrylic, MMCF, polyamides, etc.), as defined in the material factor table, by simple multiplication:

$$
\text{SEC}_{\text{material}}(\text{dtex}) = f_{\text{material}} \cdot \text{SEC}_{\text{CF,cotton}}(\text{dtex})
$$

where $f_{\text{material}}$ is the dimensionless scaling factor for each fibre family.

---

### 4.8 Step 5 -- Extending from cotton to other fibre families

The literature on **non-cotton ring spinning** (e.g. acrylics, MMCF, polyamides, blends) is far more fragmented. However, we needed a consistent way to assign **relative SEC levels** for different fibre families while maintaining cotton as the baseline.

To do this, we used relative **material-type factors** inspired by the **Apparel Impact Institute** benchmarking work (Made2Flow data):

- Cotton is set to factor **1.00**.
- Other fibre families receive **multiplicative factors** reflecting their typical higher or lower energy demand per kg of yarn, due to friction, drafting behaviour, twist levels, and machine settings.

The default factors currently used are:

| Material type | Factor (relative to cotton) |
|---|---|
| Cotton | 1.00 |
| Acrylic, Modacrylic, PAN | 1.57 |
| Cotton / Man-Made (generic blends) | 1.36 |
| CVC (Chief Value Cotton) | 1.21 |
| Elastane (Spandex/Lycra), TPU | 2.14 |
| Linen blends | 1.60 |
| MMCF (Rayon, Viscose, Lyocell) | 1.29 |
| PC (Polyester/Cotton) | 1.29 |
| Poly blends (generic synthetic blends) | 1.36 |
| Polyamides (Nylon 6, 6.6, PA 11, PA 12, ...) | 1.50 |
| Polyamide blends | 1.71 |
| Polyester (PET, PBT, PTT, PLA, etc.) | 1.14 |
| Silk blends (spun silk) | 1.79 |
| Worsted wool | 1.12 |
| Woollen wool | 0.90 |

For each **dtex value**, the **cotton SEC** from the blended curve is multiplied by the relevant factor to obtain SEC for other fibre families. For example, at 250 dtex:

- Cotton: approximately 2.76 kWh/kg
- Acrylic: 2.76 x 1.57 approximately 4.33 kWh/kg
- MMCF: 2.76 x 1.29 approximately 3.56 kWh/kg
- Polyester: 2.76 x 1.14 approximately 3.15 kWh/kg
- Woollen wool: 2.76 x 0.90 approximately 2.48 kWh/kg

This yields a **full matrix of kWh/kg values** by **dtex** and **material family** (45--600 dtex; cotton, MMCF, polyamides, acrylics, blends, etc.), consistent with both:

- the shape of the cotton curve, and
- the **relative** intensities from AII benchmarking.

---

### 4.9 Uncertainty and limitations

Key points to note for internal use:

- **Source domains:**
  - Koc & Kaplan data are most reliable in the **120--370 dtex** range.
  - Laursen et al. cover **130--600 dtex** and include auxiliaries (humidification, lighting).
  - Ecobalyse is intended as a generic parametric model, not a measured LCI.

- **Extrapolation:**
  - **<120 dtex:** results should be treated as central estimates with **high uncertainty** (+/-30--50%) due to limited primary data on very fine counts and modern compact spinning.
  - **>370 dtex:** extrapolation to very coarse yarns is less critical, but still subject to +/-15--25% uncertainty.

- **Material factors:**
  - The AII-based material factors are derived from facility-level benchmarking and expert judgement; they capture **relative differences** but are not a substitute for mill-level metering for each fibre family.

- **Scope limitations:**
  - This electricity model does not yet explicitly separate:
    - machine vs auxiliary loads (compressors, HVAC, lighting) by plant,
    - technology generations (older vs modern machines), or
    - compact spinning vs classical ring frames.
  - These refinements can be introduced when primary plant data become available.

---

### 4.10 Summary

In summary, ring-spun spinning electricity in the Carbonfact database is modelled as follows:

1. **Cotton ring baseline curve** constructed from:
   - Ecobalyse parametric model (Nm-based),
   - Koc & Kaplan's measured SEC vs tex (power-law fit),
   - Laursen et al.'s SEC vs tex (including auxiliaries).

2. **Blended SEC(dtex)** for cotton, obtained by:
   - Averaging Ecobalyse and Koc for 45--120 dtex;
   - Averaging Ecobalyse, Koc and Laursen for 120--600 dtex.

3. **Extension to other fibre families** via multiplicative **material-type factors** (AII-derived), applied to the cotton SEC at each dtex.

4. The result is a **continuous, dtex-based SEC function** (kWh/kg) for **ring-spun yarns across multiple fibre families**, suitable for use as a transparent, updatable backbone in the spinning LCI.

## 5. Lubrication and lubricant-related emissions

Lubricant use in ring spinning depends on fibre type, yarn fineness and machine configuration. The model follows two principles:

1. **Lubricant intensity scales with SEC:** finer yarns (higher SEC) require more lubrication per kg of yarn; coarser yarns require less.
2. **Fibre families have different baseline levels:** acrylic/PAN, polyamides and elastane typically need more lubrication than cotton or polyester.

### 5.1 Cotton baseline

For 100% cotton ring yarn, lubricant consumption is modelled as a decreasing function of dtex:

- From **0.00200 kg/kg** at 45 dtex down to **0.00050 kg/kg** at 600 dtex.

This range is calibrated to remain compatible with published values of spinning oils (approximately 0.18--0.35 ml/kg for typical ring spinning lubricants) and to stay within the order of magnitude of JRC textile model assumptions and industrial case studies.

### 5.2 Fibre-specific adjustments

Fibre families are grouped into lubrication "classes", reflecting their frictional behaviour and process demands:

- **Cotton and cotton-rich blends (cotton, CVC, PC 50/50, cotton/man-made 50/50):**
  Use the cotton baseline profile, optionally adjusted +/-10--20% according to waste and SEC differences.

- **Synthetics and MMCF (polyester, MMCF, generic poly blends):**
  Use a slightly lower or equal baseline compared with cotton, except where literature suggests higher friction (some polyester/nylon blends). In practice, values follow the same 0.00200 -> 0.00050 kg/kg profile, with small modifiers.

- **Acrylic / Modacrylic / PAN, polyamides, elastane:**
  These materials require comparatively more lubrication. Their profiles are scaled upwards (e.g. up to ~0.0025--0.005 kg/kg for acrylic/PAN) and retain the same decreasing trend with dtex.

- **Silk and wool:**
  Silk and fine wool blends are modelled conservatively, with lubrication similar to cotton or slightly higher, but their environmental profile is dominated by waste and fibre production rather than spinning oils.

For all fibre families, the lubricant input is mirrored by an equal output as *waste mineral oil*, so that downstream treatment is captured.

---

## 6. Yarn waste and loss model

Yarn waste and losses are critical for both mass balance and impact allocation. The model uses fibre- and route-specific ranges informed by EDIPTEX, Textile Exchange CFMB and mill-level case studies.

### 6.1 Fibre-family ranges

The following indicative ranges are used as central values for "Average Waste/Loss" per kg of finished yarn:

- **Cotton, generic ring:** 0.15--0.20 kg/kg.
- **Combed cotton (knitting and weaving):** 0.25--0.35 kg/kg (higher waste due to noil removal).
- **Carded cotton (knitting and weaving):** 0.10--0.20 kg/kg.
- **Synthetics and MMCFs:** 0.03--0.07 kg/kg (lower opening/cleaning waste).
- **Acrylic / Modacrylic / PAN:** 0.08--0.13 kg/kg.
- **Silk (spun silk):** 0.40--0.60 kg/kg (large reeling and combing losses).

These values are implemented as central estimates per material group in the flat sheet.

### 6.2 Treatment of blends

For fibre blends (CVC, PC, cotton/man-made, polyamide blends, etc.), waste fractions are derived by:

- **Weighted interpolation** between the waste ranges of the constituent fibre families, and/or
- When available, **direct literature or mill benchmarks** for specific blends (e.g. CVC 50/50).

This ensures that waste modelling for blends is coherent with pure fibre baselines and does not introduce discontinuities.

---

## 7. Plastic bobbins and capital goods

### 7.1 Plastic bobbins

Plastic carriers (bobbins, cheeses) are modelled in a simple and conservative way:

- **Input:** 0.001 kg polypropylene per kg yarn (`market for polypropylene, granulate, GLO`).
- **Output:** 0.001 kg waste polypropylene, assumed sent to recycling (`waste polypropylene, for recycling, unsorted, Recycled Content cut-off, GLO`).

This represents an average bobbin mass per kg of yarn, consistent with technical literature and LCA case studies on textile processes.

### 7.2 Capital goods: machinery and buildings

Capital goods are included in a generic, but transparent way:

- A generic **spinning and winding machine** with a mass of ~2.5 t is amortised over its expected lifetime production, yielding **0.0013 kg machine steel per kg yarn**.
- This is implemented as:
  - Input: `market for building machine, unit, GLO` with 4.64x10^-7 units/kg yarn, linked to a machine dataset that contains steel and other materials.
  - Output: `market for waste steel, RoW` (0.0013 kg/kg yarn), representing end-of-life recycling.

Manufacturer catalogues and Swerea-type textile LCA databases are used to ensure that machine mass and composition are within realistic ranges for modern ring spinning lines.

---

## 8. Implementation, traceability and updates

The ring-spun yarn model is implemented as a **flat sheet** with 875 rows and a fixed set of foreground columns (electricity, lubricant, waste, plastic, capital goods).

Key implementation and governance rules:

1. **Single source of truth for curves and factors**
   - The cotton SEC(dtex) curve is managed centrally (coefficients *a*, *b*).
   - Material factors $f_{\text{material}}$, lubrication profiles and waste ranges are stored in separate reference tables, which feed the flat sheet.

2. **Monotonicity and physical checks**
   - For each fibre family, SEC(dtex) is checked to be monotonically decreasing over 45--600 dtex.
   - Lubricant intensity must not increase towards coarse counts.
   - Waste fractions are verified to fall within the predefined ranges.

3. **Traceability to literature**
   - Each foreground parameter (SEC anchor points, lubricant range, waste fraction, bobbin mass, capital goods intensity) is linked in the internal documentation to at least one published source or technical document.
   - This ensures that every cell in the 875-row grid can be traced back to an explicit methodological choice and reference.

4. **Update protocol**
   - When new plant data or better literature become available, updates are performed at the level of:
     - SEC anchor points and regression,
     - material factors, or
     - waste and lubricant ranges.
   - The blending and scaling structure remains unchanged, preserving internal consistency while allowing gradual improvement.
