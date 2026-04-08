# Hosiery Knitting

## 1. Background

### 1.1 Context

This document presents the modelling assumptions and data sources for **hosiery knitting**, representing the production of socks or similar small-diameter tubular knitted goods.

The model follows the same methodological principles applied in flat and circular knitting, ensuring coherence across all knitting process datasets.

### 1.2 Scope and functional unit

- **Functional unit:** 1 kg of hosiery fabric (average of mixed cotton and synthetic yarns).
- **System boundary:** Gate-to-gate hosiery knitting.
- **Included:**
  - Yarn losses, lubricants and related emissions
  - Electricity consumption (direct and indirect)
  - Machine depreciation (capital goods) and end-of-life (EoL)
  - Textile waste to treatment
- **Excluded:**
  - Fibre and yarn production (modelled upstream)
  - Sewing, dyeing, finishing and packaging
  - Factory building and auxiliary systems beyond indirect energy allocation

## 2. Technical Overview

### 2.1 Process characteristics

Hosiery knitting uses small-diameter single-cylinder circular knitting machines designed for automatic toe closure and optional linking.

Production rates, power consumption and material losses are highly dependent on the gauge, feed configuration and automation level.

Key benchmarks:

- **Output:** ~300--400 pairs/day per standard machine; premium multi-feed models can exceed 800 pairs/day (~33 pairs/h).
- **Machine weight:** typically **230--320 kg**.
- **Energy:** **0.5--1.2 kWh/kg** (machine electricity only).
- **Lubricant consumption:** **0.05--0.10 L/kg**, depending on lubrication system efficiency.
- **Yarn waste:** **2--5%**, depending on toe-closing system and yarn type.

## 3. Inventory Data

| Category | Flow | Amount | Unit | Comment |
|---|---|---|---|---|
| **Product** | Hosiery fabric (average mix) | 1 | kg | Representative of mixed cotton/synthetic yarn composition. |
| **Technosphere flows** | Dtex Yarn, "e.g. Cotton" (yarn losses) | 0.02 | kg | Default 2% waste. Consistent with defect rates <2% reported for modern hosiery machines (Laursen 2007; van der Velden 2014; Sandin 2019; Accio, 2023). |
| | Lubricant, average | 0.008 | kg | Lubricant: 8 g/kg fabric (Sandin et al. 2019, p. 45 -- "The lubricant was assumed to correspond to 8% of the weight of the knit.") |
| | Air emissions from lubricant | 0.008 | kg | Equal to lubricant input for simplification. |
| **Electricity / heat** | Electricity mix | 1.2 | kWh | Average SEC derived from literature and manufacturer data: circular knitting approximately 0.8--1.2 kWh/kg (Maity et al., 2021; Lonati GK series approximately 0.5 kW for 0.9 kg/h output). |
| **Indirect energy** | Compressors, HVAC, lighting, robots | 4.46 | kWh | Indirect uses (air compressors ~6 bar, cooling, illumination, auxiliaries). Harmonised with other knitting processes for methodological consistency. |
| **Capital goods** | Building Machine (market for building machine) | 0.0004 | kg/kg fabric | Based on 300 kg machine amortised over 720,000 kg lifetime output (see below). |
| **Waste to treatment** | EoL Machine (Steel) | 0.00035 | kg | 85% of total mass (steel) distributed per kg of fabric. |
| | Recycling (Other materials) | 0.00006 | kg | 15% of total mass (motors, electronics, plastics). |
| | Textile waste incineration (no credits) | 0.02 | kg | Seamless knitting eliminates cutting losses; total waste typically <5% (K&G Garment, 2025; AATCC in GIZ 2023). |

---

## 4. Capital Goods (Machine)

### 4.1 Equipment data

| Machine | Weight (kg) | Source |
|---|---|---|
| Lonati GE616DF / GE516DF (family) | 300 | Lonati / Santoni technical brochures (2023) |

### 4.2 Allocation parameters

| Scenario | Years | Hours/day | Days/year | Productivity (kg/h) | Lifetime output (kg) | Allocation (kg/kg fabric) |
|---|---|---|---|---|---|---|
| **Average** | 15 | 16 | 300 | 10 | 720,000 | 0.0004 |

### 4.3 End-of-Life (EoL) allocation

| Material | Share (%) | Weight (kg) | Allocation (kg/kg fabric) |
|---|---|---|---|
| Steel | 85 | 255 | 0.00035 |
| Other materials | 15 | 45 | 0.00006 |

These allocations show the portion of the machine infrastructure "consumed" per kilogram of hosiery fabric.

### 4.4 Representation in ecoinvent

For the dataset **"market for building machine"**:

- **Amount:** 1.4E-07 unit/kg (0.0004 kg/kg / 300 kg/machine)
- **Unit:** unit
- **Product:** building machine
- **Geography:** GLO

This approach mirrors that used for flat and circular knitting, aligning with EF and ecoinvent rules for infrastructure amortisation.

### 4.5 Building Infrastructure

The hosiery knitting process model includes an optional building infrastructure (pavilion) share as a modular and auditable input. The building is represented by an ecoinvent-style construction dataset ("building, hall") whose reference flow is m^2 of industrial hall.

**4.5.1 Allocation principle (area amortisation over lifetime output).**
Building infrastructure is attributed to 1 kg of knitted hosiery by amortising the allocated hall area over the lifetime production associated with the knitting cell:

$$
\text{Building intensity (m²/kg)} = \frac{A_{\text{alloc}} \text{ (m²)}}{Q_{\text{lifetime}} \text{ (kg)}}
$$

$$
Q_{\text{lifetime}} = \text{productivity (kg/h)} \times \text{hours/day} \times \text{days/year} \times \text{years}
$$

where $A_{\text{alloc}}$ is the hall area allocated to the knitting cell (machine footprint + access + yarn supply + maintenance space + internal logistics), and $Q_{\text{lifetime}}$ is the total knitted output produced during the reference service life under the chosen operating regime.

**4.5.2 Technology rationale.**
Hosiery machines are physically small relative to other knitting technologies (individual machine envelope below 1.5 m^2), but are typically deployed in multi-machine cells with shared yarn feed, collective creel systems, and common aisles. The resulting cell area, normalised by throughput, is comparable to seamless knitting, placing hosiery in the same intensity band. Additionally, the low mass per article and relatively slow cycle time per gram of output sustain a moderate building intensity per kg.

**4.5.3 Practical implementation.**
In the hosiery knitting foreground unit process, we add an input: *building, hall* (unit = m^2) with amount = 1.61E-05 m^2/kg.

**4.5.4 End-of-life of the building.**
The building dataset includes construction, maintenance and decommissioning within the background system model. No separate building EoL module is created in the foreground; only the amortised m^2/kg input is provided.

**4.5.5 Default value (this study).** In the absence of site-specific $A_{\text{alloc}}$ and $Q_{\text{lifetime}}$, the following reference intensity is applied, shared with the seamless technology group given comparable normalised throughput per allocated space:

> Hosiery knitting: **1.61E-05 m^2/kg**

Physical plausibility was cross-checked using machine envelope data from Lonati GE616DF3 (width 127.3 cm x depth 114.8 cm, envelope approximately 1.46 m^2) with a higher cell factor to account for multi-machine layout, shared yarn supply infrastructure, and aisles, yielding an allocated area consistent with the adopted default.

---

## 5. Indirect Energy Allocation

Indirect energy includes electricity consumed by **compressors**, **HVAC systems**, **lighting**, and **auxiliary robots** for automatic toe linking, packaging or maintenance.

As sub-metering is rarely available, the **total indirect energy of 4.46 kWh/kg** is used -- the same reference adopted across all knitting processes for consistency.

This total can later be divided into subsystems using the default mid-range distribution:

| Subsystem | Share (%) | Equivalent (kWh/kg) |
|---|---|---|
| Knitting machines | 35 | 1.56 |
| Compressors | 25 | 1.12 |
| HVAC | 30 | 1.34 |
| Lighting | 6.5 | 0.29 |
| Cleaning / auxiliaries | 3.5 | 0.16 |

---

## 6. Waste Generation

Seamless hosiery knitting produces **minimal cutting waste**, in contrast to conventional cut-and-sew garments that lose 10--25% of material during trimming.

Industrial data (K&G Garment, 2025; GIZ 2023) show material utilisation above 95%, corresponding to **<5% total losses**.

The LCI therefore assumes **2--5% total yarn waste**, and **0.02 kg/kg textile waste** is modelled for treatment.

---

## 7. Key Assumptions Summary

| Parameter | Average value | Comment |
|---|---|---|
| **Electricity (machine)** | 1.2 kWh/kg | Lonati / literature average |
| **Indirect energy (HVAC, compressors, etc.)** | 4.46 kWh/kg | Harmonised default for knitting |
| **Lubricant** | 0.008 kg/kg | 8 g/kg fabric typical maximum |
| **Yarn loss** | 0.02 kg/kg | <2% defect rate typical |
| **Machine mass allocation** | 0.0004 kg/kg | 300 kg machine amortised |
| **EoL (steel)** | 0.00035 kg/kg | 85% share |
| **Textile waste** | 0.02 kg/kg | <5% utilisation loss |

## 8. References

- AATCC (2023). *Cutting Waste in Textile Manufacturing.* In: GIZ Sustainable Apparel Series.
- Accio (2023). *Socks Knitting Machine Benchmark.* <https://www.accio.com/plp/socks_knitting_machine>
- Emdadul Haq, M., et al. (2022). *Lubricant consumption in hosiery production.* *PrimeAsia Journal*.
- Hasanbeigi, A. & Price, L. (2015). *Energy Efficiency in the Textile Industry.* Lawrence Berkeley National Laboratory.
- K&G Garment (2025). *What is seamless knitting?* <https://kggarment.com/blogs/news/what-is-seamless-knitting-a-complete-guide-for-brands>
- Laursen, S. E., et al. (2007). *EDIPTEX -- Environmental Assessment of Textiles.* Danish EPA.
- Lonati S.p.A. (2023). *GE516DF / GE616DF Technical Catalogue.*
- Maity, S., et al. (2021). *Textile Energy Efficiency.* Elsevier.
- Sandin, G., et al. (2019). *Environmental Assessment of Swedish Fashion Consumption.* Mistra.
- van der Velden, N. M., Patel, M. K., & Vogtlander, J. G. (2014). *LCA Benchmarking Study on Textiles.* *Int. J. Life Cycle Assess.*
