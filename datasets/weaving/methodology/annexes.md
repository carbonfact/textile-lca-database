# Annexes

> Part of [Weaving Methodology](README.md)

## 5. Inferences

### Flexibility with Carbonfact weaving LCI model

- The new LCI model allows weaving impacts to be calculated for any yarn count, enabling scenarios beyond the limited dtex ranges provided in EF datasets.
- Energy consumption in weaving can now be dynamically linked to yarn count, replacing EF's static, count-independent assumptions.
- Lubricating oil usage is included based on literature-backed values, providing more complete process inventories than EF datasets.
- Yarn loss (%) can be varied by loom type and later updated when primary data becomes available, improving accuracy over EF's generic assumptions.
- The model supports optional inclusion or exclusion of the sizing process, allowing realistic modelling of fabrics and materials that do not undergo sizing (e.g., carpet, primary backing, silk).

### Sizing process enhancements

- The sizing module distinguishes between **natural and synthetic yarns**, enabling material-specific sizing impacts.
- Users can modify **size composition**, affecting size pick-up, water uptake and water evaporation, allowing much higher process fidelity.
- If drying energy is known, it can be **directly entered** to compute thermal energy from evaporation, providing traceable and transparent energy modelling.

### Data gaps & priorities

- To further strengthen model accuracy, **primary weaving data for silk, carpet, and primary backing fabrics** is needed, since EF provides energy values without any process descriptions.
- **Water-jet weaving** remains a significant uncertainty: Carbonfact results differ from EF values by **more than 50%**, whereas all other loom types differ by only **5–20%**, indicating the need for reliable industry benchmarks.

## 6. References

[1] [Mordor Intelligence](https://www.mordorintelligence.com/industry-reports/global-textile-industry---growth-trends-and-forecast-2019---2024)

[2] Prassana et al, Koc et al.

[3] Senol F.; Energy Consumption and Conservation in Weaving Preparation Mill, Seminar Notes about Energy Consumption and Conservation in Textile Mills, Bursa: Sumerbank Textile Education and Research Institute.

[4] [Literature review file for weaving](https://docs.google.com/spreadsheets/d/1Kv2Fbj4XN0vh-NefBYk-l9FxsiUeALKB/edit?usp=drive_link&ouid=109658983613223573958&rtpof=true&sd=true)

[5] [LCI for weaving and sizing](https://docs.google.com/spreadsheets/d/1jmVFE7R4B-803EcJ2yD-xd3bQ4gtC3Sz/edit?usp=drive_link&ouid=109658983613223573958&rtpof=true&sd=true)

[6] [LCIA - dynamic LCA tool for weaving and sizing](https://docs.google.com/spreadsheets/d/1CvCSQHsEVUAKKwetNszcA_lhsNXUIv5t/edit?usp=drive_link&ouid=109658983613223573958&rtpof=true&sd=true)

## 7. Linking weaving technologies and fabric types

The information that Carbonfact generally collects from customers regarding weaving are the following:

- Fabric material: cotton, viscose, polyester, polycotton blend...
- Fabric type/product application: denim, tshirt...
- Yarn count in dtex

The equipment type is not common, meaning we would need to build some dataset archetypes based on these 3 informations. For that matter, the following framework proposes to link weaving technologies with specific materials and product applications.

| Technology | Typical energy ratio | Fabric material | Fabric type | Explanation |
| --- | --- | --- | --- | --- |
| **Air-jet loom** | 1 | Cotton, Polyester, Polycotton | Light wefts |  |
| **Rapier loom** | 0.78 | All yarns | Delicate fabrics | Most versatile loom. |
| **Projectile loom** | 0.41 | Cotton, synthetics | Denim without elastane, Heavy wefts and coarse yarns |  |
| **Water-jet loom** | 0.28 | Synthetic yarns |  | Water damages hydrophilic materials (cotton, viscose), only used for synthetics |
| **Shuttle** | 0.56 | Cotton, Wool, Linen, Silk |  |  |
| **Jacquard** | 0.84 | All yarns | Complex pattern apparel, Upholstery, Curtains |  |

*Draft: Product category taxonomy match with weaving technologies*

| **Product category** | **Weaving technologies** | **Comment** |
| --- | --- | --- |
| ACCESSORY | Rapier / Air-jet / Shuttle / Jacquard | Depends on the type of accessory |
| BAG | Rapier / Air-jet / Projectile | Woven canvases, twills, oxfords for many bags. |
| DRESS | Rapier / Air-jet / Jacquard | Many dresses use woven fabrics; knits also common. |
| FURNITURE | Rapier / Jacquard | When textile upholstery is used, often woven. |
| HOUSEWARE | Rapier / Air-jet / Jacquard | Many flat linens are woven. |
| JACKET | Rapier / Air-jet / Projectile | Woven shells for many jackets; knits for some styles. |
| SLEEPING_BAG | Air-jet / Rapier | Shells are lightweight woven; insulation nonwoven. |
| SNOWSUIT | Rapier / Air-jet | Woven outer shell fabrics with coatings. |
| SUIT | Rapier / Projectile / Jacquard | Woven wool/poly fabrics, sometimes jacquard. |
| SWEATER | Not woven | Knitted by definition. |
| SWIMWEAR | Rapier / Air-jet | Outer shorts segment often woven microfiber. |
| TENT | Air-jet / Water-jet / Rapier | Woven polyester/nylon, often filament, hydrophobic. |
| TRACKSUIT | Not woven | Frequently knit (tricot, jersey) rather than woven. |
| TSHIRT | Not woven | Classic jersey T-shirt, knitted. |
| UNDERWEAR | Rapier / Air-jet | Category dominated by knits. |
| WORKWEAR | Rapier / Air-jet / Projectile | Heavy woven cotton/poly twills, canvases. |

| **Material category** | **Weaving technologies** | Comment |
| --- | --- | --- |
| ANIMAL_FIBERS | Rapier / Shuttle / Projectile / Jacquard |  |
| CELLULOSE_BASED_FIBERS | Rapier / Shuttle / Projectile / Jacquard |  |
| PLANT_FIBERS | Rapier / Shuttle / Projectile / Air-jet / Jacquard |  |
| SYNTHETIC_FIBERS | Rapier / Shuttle / Projectile / Air-jet / Water-jet / Jacquard |  |

## 8. Comparison with Apparel Impact Institute

**Methodology of Apparel Impact Institute for weaving energy intensity:**

Based on expert advice, the following parameters have been indicated to influence the weaving energy intensity.

- Loom type,
- fabric construction,
- material type

Major source for energy intensity of various products are from Made2Flow - which has a database of complex facility data from over 12,000 facilities in 53 countries. The relative energy intensity factors for the key parameters for weaving and prototype energy intensity figures for the listed yarns, fabrics, and final product types.

| Loom type | Fabric category | Indicative dtex range | Weaving type | Material type |
| --- | --- | --- | --- | --- |
| Air jet loom | Fabrics used as garment linings <60–150 gsm | 40–150 dtex | Dobby | Bast / Leaf (Linen, Hemp, etc.) |
| Water jet loom | Heavy-weight Denim 300–450+ gsm | 600–1200 dtex | Double weave | Cotton |
| Rapier loom | Heavy-weight non-Stretch Fabrics 260–350+ gsm | 400–800 dtex | Jacquard | Man-Made Protein (Soya, Casein, etc.) |
| Projectile loom | Heavy-weight Stretch Fabrics 260–350+ gsm | 450–900 dtex | Leno | Man-Made (Polyester, etc.) |
|  | Home Textiles (Bed sheets) | 100–250 dtex | Pile | MMCF (Viscose, Lyocell) |
|  | Home Textiles (Upholstery / Curtains) | 300–1000 dtex | Plain | Silk |
|  | Lace, Crochet & Embroidery | 50–200 dtex | Satin | Wool |
|  | Light-weight Denim <180–240 gsm | 200–350 dtex | Twill |  |
|  | Light-weight non-Stretch Fabrics up to 150 gsm | 60–160 dtex |  |  |
|  | Light-weight Stretch Fabrics up to 150 gsm | 70–180 dtex |  |  |
|  | Mid-weight Denim 240–300 gsm | 350–600 dtex |  |  |
|  | Mid-weight non-Stretch Fabrics 150–260 gsm | 150–400 dtex |  |  |
|  | Mid-weight Stretch Fabrics 150–260 gsm | 180–450 dtex |  |  |
|  | Narrow fabrics (Labels, Ribbons, Tapes) | 50–600 dtex |  |  |
|  | Towels / Terry Fabrics 300–600 gsm | 600–2000+ dtex |  |  |
|  | Worsted wool / wool blends fabric 180–350+ gsm | 150–800 dtex |  |  |

It seems from the calculator that based on loom type and product - weaving energy intensity has been obtained from Made2Flow database and a weaving type factor and material factor has been added to accommodate the other variants.

**Key takeaway 1: Loom-type-specific energy intensity patterns**

Across most product categories, the observed trend differs from both the EF datasets and our internal database, where air-jet looms consistently showed higher energy intensity.

**Question 1:**

> Does the benchmarking tool include compressor and other auxiliary/utility energy in the energy figures?

**Question 2:**

> The weaving calculator refers to a loom-specific energy table, but this table does not appear to be referenced in the actual calculations. Were these loom-type energy ratios applied in the model, or were the calculations based solely on primary energy data from individual facilities?

| Loom type | kWh/kg |
| --- | --- |
| Rapier | 2.10 |
| Airjet | 1.80 |
| Water | 1.61 |
| Projectile | 2.30 |

**Key takeaway 2: Weaving-type-specific ratios can be integrated into the Carbonfact database**

Energy intensities differentiated by weaving type have been derived using expert judgment, assuming constant loom type and material type while adjusting for relative increases or decreases in energy demand. These ratios can be incorporated into our model to further expand the range of process-level variations.

| Weaving type |
| --- |
| Dobby |
| Double weave |
| Jacquard |
| Leno |
| Pile |
| Plain |
| Satin |
| Twill |

**Key takeaway 3: Material-type-specific ratios can be integrated into the Carbonfact database**

Similar ratio has been applied for weaving energy intensities for different material types whilst keeping constant loom type, weaving pattern and product type.

**Key takeaway 4: Weaving energy intensity is reported only at broad GSM-based product levels, not by yarn count**

The benchmarking tool reports weaving energy intensities only for aggregated product categories defined by broad GSM ranges, without differentiation by yarn count. As a result, a like-for-like dataset-to-dataset benchmarking is not fully possible, unlike the EF database and the Carbonfact database.

Significant difference in energy intensity values for weaving with EF and Carbonfact database as compared to AII benchmarking tool. Although we can point to EF and Carbonfact database referring to decade old values for energy and AII benchmarking tool taking latest facility data, still a 10 time less value can't be justified. We need to understand more on the system boundary used by the benchmarking tool.

| Weaving Machine Type | Product Type | Product Type (mj/kg) | Weaving type | Weaving type (Factor) | Material type | Material type (Factor) | MJ/kg | Unadjusted kWh/kg | Adjusted kWh/kg |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Air-Jet Loom | Fabrics used as garment linings <60-150 gsm | 3.96 | Dobby | 1.23 | Cotton | 1.00 | 4.87 | 1.36 | 2.73 |

| dtex range | EF 3.1 (kWh/kg) | Carbonfact (kWh/kg) | Benchmarking AII (kWh/kg) |
| --- | --- | --- | --- |
| Fabrics used as garment linings <60-150 gsm (assuming between 45-150 dtex) | 24.21 | 19.28 | 2.73 |

Even if we assume the average, max, min of the three databases in terms of energy intensity values reported, we gather that

| Database | Average (kWh/kg) |
| --- | --- |
| EF 3.1 | 14.23 |
| Carbonfact | 11.77 |
| AII benchmarking tool | 3.53 |

**Potential root causes**

- **System boundary differences**: The benchmarking tool may exclude auxiliary energy uses such as compressors (critical for air-jet looms), humidification systems, material handling, or shared utilities, while EF and Carbonfact datasets typically include these within the weaving process boundary.
- **Allocation methodology**: Energy may be allocated in the benchmarking tool based on fabric output area (m2) or loom runtime rather than mass (kg), which can significantly reduce apparent kWh/kg values for lighter fabrics.
- **Temporal differences in data sources**: While EF and Carbonfact datasets may indeed rely on older reference data, the magnitude of the difference observed cannot be explained by efficiency improvements alone over time.
