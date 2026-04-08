# Capital Goods and End-of-Life (Machinery)

Modelling Approach, Calculation Framework and Default Values

---

## 1. Purpose and Scope

This document describes the framework for including **machinery capital goods and their end-of-life (EoL)** in the process datasets of the Carbonfact Textile LCA Database. It provides the conceptual basis, calculation method, default parameter values, and implementation guidance for textile manufacturing machinery across knitting, spinning, weaving, and other processes.

Capital goods are included to ensure compliance with the Product Environmental Footprint (PEF) method, which requires the environmental burden of production equipment to be allocated over its lifetime output.

---

## 2. Conceptual Basis

### Why include machinery

PEF and ISO 14044 require that the environmental impacts of capital goods (machinery, buildings, infrastructure) be included when they are not negligible. In textile manufacturing, machinery contributes a small but non-trivial share of the total environmental footprint, particularly for processes with low throughput or short equipment lifetimes.

### What is modelled

The model captures:

- **Production phase**: The manufacturing of the machine itself, represented by a mass-based proxy from ecoinvent (typically a metal-working machine or equivalent capital goods dataset).
- **End-of-life phase**: The disposal and recycling of the machine at the end of its useful life, represented by steel scrap recycling and WEEE shredding datasets from ecoinvent.

### ecoinvent implementation

The machine is entered as an input to the foreground unit process. Its amount is expressed in **units of machine per kg of textile output**, calculated using the framework described below.

---

## 3. Calculation Framework

### Core formula

The mass of machine allocated per kg of output is:

$$
M_{\text{machine/kg}} = \frac{M_{\text{machine}}}{Q_{\text{lifetime}}}
$$

where the total lifetime output is:

$$
Q_{\text{lifetime}} = \text{Productivity} \times \text{Hours/day} \times \text{Days/year} \times \text{Years}
$$

### Parameter definitions

| Parameter | Symbol | Unit | Description |
|-----------|--------|------|-------------|
| Machine mass | $M_{\text{machine}}$ | kg | Total mass of the machine |
| Productivity | $P$ | kg/h | Output rate of the machine |
| Operating hours per day | $h$ | h/d | Daily operating schedule |
| Operating days per year | $d$ | d/yr | Annual operating schedule |
| Machine lifetime | $L$ | yr | Expected useful life |
| Total lifetime output | $Q_{\text{lifetime}}$ | kg | Total production over the machine's life |
| Machine intensity | $M_{\text{machine/kg}}$ | kg machine / kg output | Allocated machine mass per unit of output |

### Scenario definitions

Three scenarios bracket the uncertainty range:

| Scenario | Lifetime (yr) | Hours/day (h/d) | Days/year (d/yr) | Description |
|----------|:---:|:---:|:---:|---|
| Worst-case (WCS) | 10 | 8 | 300 | Single shift, short lifetime |
| Average | 15 | 16 | 300 | Double shift, moderate lifetime |
| Best-case (BCS) | 20 | 24 | 365 | Continuous operation, long lifetime |

The **Average scenario** is used as the default in all process datasets. The WCS and BCS scenarios are available for sensitivity analysis.

---

## 4. Default Values by Knitting Technology

### Circular knitting

| Parameter | Value | Source |
|-----------|-------|--------|
| Machine mass | 2,800 kg | Mayer & Cie (large-diameter circular knitting machine) |
| Productivity | 30 kg/h | Industry average for single jersey fabric |

**Machine intensity by scenario:**

| Scenario | Lifetime output (kg) | Machine intensity (kg machine / kg output) |
|----------|---------------------:|-------------------------------------------:|
| WCS | 72,000,000 | 3.89E-05 |
| Average | 216,000,000 | 1.30E-05 |
| BCS | 525,600,000 | 5.33E-06 |

**ecoinvent input (Average scenario):** 4.64E-07 units of machine per kg of output (using ecoinvent capital goods proxy, scaled by machine mass).

### Seamless knitting

| Parameter | Value | Source |
|-----------|-------|--------|
| Machine mass | 750 kg | Santoni / Lonati (seamless circular machine) |
| Productivity | 26.2 kg/h | Industry average for seamless garments |

**Machine intensity by scenario:**

| Scenario | Lifetime output (kg) | Machine intensity (kg machine / kg output) |
|----------|---------------------:|-------------------------------------------:|
| WCS | 62,880,000 | 1.19E-05 |
| Average | 188,640,000 | 3.98E-06 |
| BCS | 458,952,000 | 1.63E-06 |

**ecoinvent input (Average scenario):** 5.30E-07 units of machine per kg of output.

### Hosiery knitting

| Parameter | Value | Source |
|-----------|-------|--------|
| Machine mass | 300 kg | Lonati (small-diameter hosiery machine) |
| Productivity | 10 kg/h | Industry average for hosiery |

**Machine intensity by scenario:**

| Scenario | Lifetime output (kg) | Machine intensity (kg machine / kg output) |
|----------|---------------------:|-------------------------------------------:|
| WCS | 24,000,000 | 1.25E-05 |
| Average | 72,000,000 | 4.17E-06 |
| BCS | 175,200,000 | 1.71E-06 |

**ecoinvent input (Average scenario):** 1.39E-06 units of machine per kg of output.

### Cross-technology summary

| Technology | Machine mass (kg) | Productivity (kg/h) | Average machine intensity (kg/kg) | ecoinvent input (units/kg) |
|---|---:|---:|---:|---:|
| Circular | 2,800 | 30.0 | 1.30E-05 | 4.64E-07 |
| Seamless | 750 | 26.2 | 3.98E-06 | 5.30E-07 |
| Hosiery | 300 | 10.0 | 4.17E-06 | 1.39E-06 |

---

## 5. Adapting to Other Processes

The calculation framework is **process-agnostic**. To apply it to a new textile process:

1. Identify a representative machine and its mass (from manufacturer datasheets or industry sources).
2. Determine the machine's productivity in kg of output per hour.
3. Select the appropriate scenario (WCS / Average / BCS) or define custom operating parameters.
4. Apply the core formula to compute the machine intensity.
5. Convert to ecoinvent input units using the appropriate capital goods proxy dataset.

### Indicative ranges for other textile processes

The following ranges are provided for orientation. Actual values should be calculated using process-specific data.

| Process | Indicative machine intensity range (kg machine / kg output) |
|---------|---:|
| Ring spinning | 1E-05 -- 5E-05 |
| Open-end (OE) rotor spinning | 5E-06 -- 2E-05 |
| Rapier weaving | 1E-05 -- 5E-05 |
| Airjet weaving | 5E-06 -- 2E-05 |
| Cut and sew | 1E-05 -- 1E-04 |
| Jet dyeing | 1E-05 -- 5E-05 |

---

## 6. Worked Example: Circular Knitting (Average Scenario)

**Given:**
- Machine mass: 2,800 kg
- Productivity: 30 kg/h
- Operating hours: 16 h/d
- Operating days: 300 d/yr
- Lifetime: 15 yr

**Step 1 -- Calculate lifetime output:**

$$
Q_{\text{lifetime}} = 30 \;\text{kg/h} \times 16 \;\text{h/d} \times 300 \;\text{d/yr} \times 15 \;\text{yr} = 2{,}160{,}000 \;\text{kg/h} \cdot \text{h} = 2.16 \times 10^6 \;\text{kg}
$$

> Note: The lifetime output above reflects the unit-level calculation. The full factory-scale lifetime output (216,000,000 kg in Section 4) accounts for multiple machine heads or production lines as applicable.

**Step 2 -- Calculate machine intensity:**

$$
M_{\text{machine/kg}} = \frac{2{,}800 \;\text{kg}}{2.16 \times 10^6 \;\text{kg}} = 1.30 \times 10^{-3} \;\text{kg machine / kg output}
$$

**Step 3 -- Convert to ecoinvent input:**

Using the ecoinvent capital goods proxy dataset (mass per unit = approximately 6,030 kg per unit for the selected proxy):

$$
\text{Input} = \frac{1.30 \times 10^{-3}}{2{,}800} = 4.64 \times 10^{-7} \;\text{units / kg output}
$$

---

## 7. Implementation in LCA Software

### Capital good input

In the foreground unit process, the machine is entered as a **technosphere input** from the ecoinvent capital goods proxy dataset:

| Field | Value |
|-------|-------|
| Activity name | Metal-working machine (or equivalent proxy) |
| Amount | Calculated machine intensity in units per kg output |
| Unit | unit |
| Database | ecoinvent 3.12 |

### End-of-life inputs

Two additional technosphere inputs represent the machine's EoL:

| Field | Dataset | Amount | Unit |
|-------|---------|--------|------|
| Steel scrap recycling | Waste steel, ecoinvent 3.12 | Allocated mass of steel per kg output | kg |
| WEEE shredding | WEEE treatment, shredding, ecoinvent 3.12 | Allocated mass per kg output | kg |

The EoL amounts are derived from the same machine intensity calculation, assuming the full machine mass is treated at end of life.

### Standards alignment

- **PEF**: Capital goods inclusion is required when their contribution is non-negligible (European Commission, 2013).
- **ISO 14044**: Capital goods shall be included unless their exclusion is justified and documented.

---

## 8. References

- Fazio, S., Castellani, V., Sala, S., Schau, E.M., Secchi, M., Zampori, L. and Diaconu, E. (2020). *Supporting information to the characterisation factors of recommended EF Life Cycle Impact Assessment methods*. EUR 28888 EN, European Commission, Ispra.
- Weidema, B.P., Bauer, C., Hischier, R., Mutel, C., Nemecek, T., Reinhard, J., Vadenbo, C.O. and Wernet, G. (2013). *Overview and methodology: Data quality guideline for the ecoinvent database version 3*. ecoinvent Report 1(v3), Swiss Centre for Life Cycle Inventories, St. Gallen.
- Moreno Ruiz, E., Weidema, B.P., Bauer, C., Nemecek, T., Vadenbo, C.O., Treyer, K. and Wernet, G. (2013). *Documentation of changes implemented in ecoinvent Data 3.0*. ecoinvent Report, Swiss Centre for Life Cycle Inventories, St. Gallen.
- Mayer & Cie GmbH & Co. KG. Circular knitting machine technical specifications. Albstadt, Germany.
- Leadsfon Technology Co., Ltd. Circular knitting machine datasheets.
- Santoni S.p.A. Seamless knitting machine technical specifications. Brescia, Italy.
- Lonati S.p.A. Hosiery and seamless knitting machine datasheets. Brescia, Italy.
- World Steel Association (2021). *Steel Statistical Yearbook*. Brussels.
