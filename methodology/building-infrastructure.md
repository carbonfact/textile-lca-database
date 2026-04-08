# Building Infrastructure in LCA

Modelling Approach, Calculation Framework and Default Values

---

## 1. Purpose and Scope

This document describes the framework for including **building infrastructure** as a capital good in the process datasets of the Carbonfact Textile LCA Database. It provides the conceptual basis, calculation method, default parameter values, and implementation guidance for allocating the environmental burden of factory buildings to textile output.

Building infrastructure is included alongside machinery capital goods to ensure completeness of the LCA model in accordance with PEF and ISO 14044 requirements.

---

## 2. Conceptual Basis

### Why include buildings

Factory buildings house the production equipment and provide the operational environment (lighting, climate control, structural support). While their per-kg contribution is typically small, PEF requires their inclusion when not demonstrably negligible. For low-throughput or space-intensive processes, the building contribution can become significant.

### Allocation principle

The building's environmental burden is allocated using an **area amortisation over lifetime output** approach:

- The floor area occupied by a production line (or machine) is identified.
- This area is divided by the total mass of textile produced over the building's useful life at that location.
- The result is a **building intensity** expressed in m² of building per kg of output.

### Background dataset

The ecoinvent dataset used to represent the building is:

| Field | Value |
|-------|-------|
| Activity name | building, hall |
| Geography | GLO |
| Unit | m² |
| Database | ecoinvent 3.12 |

This dataset represents a generic industrial hall, including structural materials (steel, concrete), roofing, and basic infrastructure. It is expressed per m² of floor area.

---

## 3. Calculation Framework

### Core formula

The building intensity (m² of building per kg of textile output) is:

$$
\text{Building intensity} \;\left(\frac{\text{m}^2}{\text{kg}}\right) = \frac{A_{\text{alloc}}}{Q_{\text{lifetime}}}
$$

where:

- $A_{\text{alloc}}$ = floor area allocated to the production line (m²)
- $Q_{\text{lifetime}}$ = total lifetime output of the production line at that location (kg)

The allocated area is derived from the machine footprint and a **cell factor** that accounts for aisle space, buffer zones, auxiliary equipment, and operator access:

$$
A_{\text{alloc}} = A_{\text{machine}} \times \text{Cell factor}
$$

### Cell factor guidance

| Layout type | Cell factor | Description |
|-------------|:---:|---|
| Dense | 2 -- 3x | Tightly packed production lines, minimal aisle space |
| Standard | 3 -- 5x | Typical factory layout with standard aisles and buffer zones |
| Spacious | 5 -- 8x | Large aisle space, quality inspection areas, storage zones |

The **Standard** cell factor (3-5x) is used as the default unless process-specific layout data is available.

### Scenario scaling

The same three operating scenarios defined in the capital goods methodology (WCS / Average / BCS) apply to the building calculation. The lifetime output $Q_{\text{lifetime}}$ is calculated using:

$$
Q_{\text{lifetime}} = \text{Productivity} \times \text{Hours/day} \times \text{Days/year} \times \text{Years}
$$

The building lifetime is assumed to match the machine lifetime for simplicity, as the building is allocated to the production activity it houses.

---

## 4. Default Values for Knitting

The following default building intensities are calculated for the **Average scenario** (15 yr lifetime, 16 h/d, 300 d/yr):

| Technology | Building intensity (m² / kg output) |
|---|---:|
| Circular knitting | 1.00E-05 |
| Seamless knitting | 1.61E-05 |
| Hosiery knitting | 1.61E-05 |
| Flat knitting | 1.39E-04 |
| 3D / WHOLEGARMENT knitting | 4.86E-04 |

> Flat knitting and 3D/WHOLEGARMENT technologies show significantly higher building intensities due to their lower throughput per unit of floor area. These machines produce shaped panels or complete garments at slower rates, requiring more building area per kg of output.

---

## 5. Adapting to Other Processes

### Step-by-step for a new process

1. **Determine the machine footprint** from manufacturer datasheets or factory layout drawings.
2. **Apply the cell factor** (typically 3-5x for standard layouts) to obtain the allocated floor area.
3. **Calculate the lifetime output** using process-specific productivity and the selected operating scenario.
4. **Divide** the allocated area by the lifetime output to obtain the building intensity.
5. **Enter** the building intensity as the amount of the "building, hall / GLO" input in the unit process.

### Indicative ranges for other textile processes

| Process | Indicative building intensity range (m² / kg output) |
|---------|---:|
| Ring spinning | 1E-06 -- 1E-05 |
| Open-end (OE) rotor spinning | 5E-07 -- 5E-06 |
| Shuttle / rapier weaving | 1E-05 -- 5E-05 |
| Airjet weaving | 5E-06 -- 2E-05 |
| Cut and sew | 1E-04 -- 5E-04 |
| Dyeing and finishing | 1E-05 -- 1E-04 |

These ranges are provided for orientation. Actual values should be calculated using process-specific data.

### Multi-process factories

When multiple processes share a single building, the total building area should be allocated to each process based on the floor area each occupies. Shared areas (offices, warehouses, corridors) can be allocated proportionally to the production area of each process or excluded if they serve non-production functions.

---

## 6. Implementation in LCA Software

### Foreground unit process

The building is entered as a **technosphere input** in the foreground unit process:

| Field | Value |
|-------|-------|
| Activity name | building, hall |
| Geography | GLO |
| Amount | Building intensity (m² / kg output) |
| Unit | m² |
| Database | ecoinvent 3.12 |

### ecoinvent format

In ecoinvent-compatible tools (Brightway, Activity Browser, SimaPro), the input is specified as:

- **Flow**: building, hall
- **Amount**: The calculated building intensity value (e.g., 1.00E-05 m²/kg for circular knitting)
- **Unit**: m²
- **Provider**: building construction, hall / GLO

### End-of-life

The ecoinvent "building, hall" dataset already includes end-of-life treatment within its system boundary (cradle-to-grave). No separate EoL input is required for the building infrastructure.

---

## 7. References

- Fazio, S., Castellani, V., Sala, S., Schau, E.M., Secchi, M., Zampori, L. and Diaconu, E. (2020). *Supporting information to the characterisation factors of recommended EF Life Cycle Impact Assessment methods*. EUR 28888 EN, European Commission, Ispra.
- Weidema, B.P., Bauer, C., Hischier, R., Mutel, C., Nemecek, T., Reinhard, J., Vadenbo, C.O. and Wernet, G. (2013). *Overview and methodology: Data quality guideline for the ecoinvent database version 3*. ecoinvent Report 1(v3), Swiss Centre for Life Cycle Inventories, St. Gallen.
- openLCA Nexus. ecoinvent 3.12 database documentation. GreenDelta GmbH, Berlin.
- Terrot GmbH. Circular knitting machine technical specifications and factory layout guidelines. Chemnitz, Germany.
- Santoni S.p.A. Seamless knitting machine technical specifications. Brescia, Italy.
- Lonati S.p.A. Hosiery knitting machine datasheets. Brescia, Italy.
- KARL MAYER STOLL. Flat knitting machine technical specifications. Reutlingen, Germany.
- SHIMA SEIKI MFG., LTD. WHOLEGARMENT knitting machine datasheets. Wakayama, Japan.
