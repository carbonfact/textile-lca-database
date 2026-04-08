# Documentation

> Part of [Weaving Methodology](README.md)

## 1. Purpose of the study

The Life Cycle Inventory (LCI) review and modelling in this study has been undertaken with the objective of replacing the existing Environmental Footprint (EF) 3.1 datasets, which currently suffer from very low transparency, limited methodological documentation, and restricted access to underlying inventory data. In contrast, this study adopts a transparent, literature-supported, and verifiable LCI approach

### 1.1 Context

The purpose of this study is to develop fully traceable, transparent, and updatable Life Cycle Inventory (LCI) datasets for 1 kg of woven fabric, covering the most relevant process variants currently represented in the Environmental Footprint (EF) 3.1 dataset library. The intent is to replace the existing EF datasets — which offer minimal transparency, limited documentation, and outdated assumptions — with LCIs that are scientifically robust, verifiable, and aligned with real-world textile production technologies.

This involves:

- Conducting a detailed literature review of textile weaving, preparation, and ancillary processes;
- Collecting secondary data from peer-reviewed studies, industrial benchmarks, and sector reports

### 1.2 Weaving process

Weaving is the process of interlacing two sets of yarns (warp and weft) to form a fabric—one of the oldest and most foundational textile manufacturing operations. Globally, woven fabrics accounted for approximately 47.5% of the textile fabric market in 2024 [1]. Because weaving remains a large-scale workplace in textile mills and involves high-speed machines, compressed air, electricity and auxiliary systems, it is a major energy-intensive process and thus critical to investigate for footprint modelling, efficiency improvement and decarbonisation.

### 1.3 System boundary

*(figure)*

- **Warping** – Combines yarns from multiple cones into a parallel sheet and winds them onto a warp beam for weaving.
- **Sizing** – Applies a water-based protective coating to warp yarns to increase strength and reduce breakage during weaving.
- **Drawing-in / Knotting** – Threads each warp yarn through heddles and reed (or ties ends) to prepare the loom for the specific fabric pattern.
- **Weaving (Loom Operation)** – Interlaces warp and weft yarns using mechanisms such as rapier, air-jet, projectile, or shuttle to form fabric.

### 1.4 Scope

Functional unit: 1 kg of woven fabric ready for wet processing

Inclusions:

- Direct and indirect energy (electricity, thermal) consumption around weaving processes
- Sizing chemical
- Yarn losses
- Lubricating oil
- Water consumption and losses due to evaporation
- Capital goods

Exclusions

- Packaging and distribution
- Yarn production and its associated upstream process stages (fibre)
- Infrastructure related impacts

## 2. Observation and Current status of Weaving LCI through Literature review

The objective of this literature review was to identify the different weaving process variants represented in existing LCIs that require reconstruction using transparent and traceable data, to assess the gaps and limitations in current LCI datasets available in databases such as EF 3.1 and ecoinvent, and to analyse the key factors that influence or modify the life cycle inventory of weaving processes.

### 2.1 Weaving datasets in EF 3.1 database

**Observations**

- EF 3.1 includes weaving-as-a-service datasets divided by loom type (shuttle, rapier, projectile, Jacquard, air-jet, water-jet, and generic "other" looms), fabric types (cotton, twill cotton, polyester, carpet, silk, and fabrics made with spin-dyed yarn), and yarn linear densities (45–370 dtex, including an average dtex variant).
- The modelling implicitly assumes that when one parameter (e.g., loom type or dtex) is varied, all other parameters remain constant, although this is not explicitly documented.
- Electricity demand in EF 3.1 weaving datasets is almost entirely derived from **Koc & Cincik (2010)**, which provides reference electricity consumption for a cotton fabric woven with **Ne 30 (approximately 196 dtex)**. The EF modelling applies a scaling factor based on the assumption that *finer yarns require more picks per unit area*, and therefore more electrical energy per kilogram. The normalization reference (196 dtex) is maintained across all variants, regardless of fabric type.
- Differences in energy consumption between loom types (air-jet, shuttle, rapier, projectile, water-jet) are adjusted using ratios reported in **Prasanna (2016)**. However, the cited source in Prasanna et al. for the ratios is *not traceable*, and the underlying data behind these ratios are unclear, reducing the reliability of the adjustment factors.
- Lubricant consumption are assumed or drawn from **Roos (2019)**, without confirmation of technology age or regional representativeness.
- EF 3.1 documentation does not clearly state whether **sizing** is included within the system boundaries for weaving.
- Although EF 3.1 contains fabric variants (cotton, polyester, carpet, silk), the underlying Koc dataset is based **only on cotton**, and no transparent explanation is provided regarding how parameters (e.g., warp density, fabric GSM, loom efficiency) were adapted for different materials. The methodology for transferring cotton-specific data to non-cotton fabrics is not available.

**Analysis:**

*(figure)*

1. The analysis shows a strong inverse relationship between yarn fineness (dtex) and climate-change impact, with lower dtex yarns resulting in significantly higher CO2e emissions per kilogram of woven fabric. This is technically expected because finer yarns require more picks per unit area, higher loom insertion frequency, greater warp tension stability, and higher loom energy use—especially in air-jet weaving where compressed-air demand increases substantially for lighter yarns. Additionally, finer yarns lead to more warp and weft breaks, increasing machine stoppages and energy losses. The power-law fit (R2 = 0.9997) confirms that climate-change impact decreases predictably as yarn dtex increases.
2. Weaving energy can vary by fabric attributes such as yarn friction, filament vs. spun structure, twist level, and fabric construction. For example, finer cotton and silk yarns often require higher speeds with more end breaks, while filament-based polyester may run more smoothly on air-jet looms but at higher compressed-air pressure. Carpet fabrics show lower emissions because they use coarse yarns with fewer picks per meter, reducing loom work per kilogram. Thus, variations in climate impact across material types arise from **mechanical and operational differences during weaving.**

*(figure)*

1. Loom-type analysis shows that air-jet and Jacquard looms have the highest climate-change impacts, while water-jet and shuttle looms show lower emissions. Air-jet looms consume large amounts of compressed air, making them the most energy-intensive weaving technology, whereas Jacquard looms incur additional electrical demand due to complex shedding mechanisms. Rapier, projectile, and shuttle looms fall in the mid-range because their energy demand depends mostly on mechanical motion rather than compressed air. Water-jet looms consistently show the lowest impact because water-based weft insertion requires far less power, provided the yarn is hydrophobic. Overall, the results highlight that **loom technology choice significantly influences weaving-stage energy demand and CO2e emissions**.

*(figure)*

Based on the EF 3.1 dataset review, a total of **22 weaving variants** must be reconstructed with transparent, traceable LCIs.

| **Loom type** | **Material** | **Yarn dtex** |
| --- | --- | --- |
| Shuttle loom | Cotton fabric | 45 dtex |
| Rapier loom | Twill cotton fabric | 70 dtex |
| Projectile loom | Polyester fabric | 120 dtex |
| Air-jet loom | Silk fabric | 150 dtex |
| Water-jet loom | Carpet fabric | 170 dtex |
| Jacquard loom | Fabric woven from spin-dyed yarn | 200 dtex |
|  |  | 250 dtex |
|  |  | 300 dtex |
|  |  | 330 dtex |
|  |  | 370 dtex |

### 2.2 Weaving datasets in Ecoinvent database (non-overlap with EF 3.1)

Detailed literature review for the seven ecoinvent datasets can be found in the excel file. The following are some important observations

1. Across multiple ecoinvent datasets, the same sources reappear:
   - Faist-Emmenegger et al. (Quantis) for cotton and synthetic weaving in India/Bangladesh
   - Velden et al. (2014) for cotton weaving energy use
   - Sharif et al. (2016) for separating joint energy use in jute mills
   - Carbotech / Empa (Stettler & Dinkel) for renewable bast fibre weaving
2. A significant portion of the data originates from early 2000s or 2010-era mills, mainly in India, Bangladesh, and West Bengal. Technology (air-jet efficiency, compressors, A/C loads, loom speed) has changed significantly since then, making these datasets poorly representative of modern weaving operations.
3. None of the ecoinvent weaving datasets specify yarn dtex or tex or the type of loom. This is a major limitation because weaving energy is heavily influenced by yarn fineness and fabric construction. Without these parameters, the datasets cannot be reliably scaled or compared.

Ecoinvent will be used for the background data provision for sizing, lubricating oil and other associated emissions.

### 2.3 Observations from literature review of other peer reviewed journals for weaving process

1. **Very limited availability of full LCIs for weaving**. Only a handful of studies provide an end-to-end life cycle inventory for weaving, with **Roos et al.** being the primary comprehensive reference. Most other publications report only partial data or focus on isolated process parameters.
2. A majority of weaving-related research concentrates on **electrical energy consumption at the loom**, with **thermal energy from sizing** either excluded or insufficiently detailed. This leads to incomplete modelling of the weaving preparation stages.
3. Most journal articles do not provide essential parameters such as **yarn linear density (dtex/tex/denier)** or **type of loom used**. These are critical drivers of energy consumption and breakage behaviour, resulting in LCIs that cannot be scaled or compared across processes.
4. Numerous studies rely heavily on **Koc (2010)** for both electrical and thermal energy estimates, even though:
   1. The data is more than a decade old.
   2. The modelled mill is **air-jet-dominated**, which inherently requires higher compressed-air consumption.
   3. The reported **thermal energy for sizing (9.85 kJ/kg)** appears **inconsistently low**, suggesting either a unit error or misinterpretation, since realistic thermal demand is significantly higher. This dependence introduces systematic uncertainty into subsequent LCIs.
5. Databases such as **Idemat** and studies like **Van der Velden et al.** use **interpolation/extrapolation models** to scale weaving energy based on yarn dtex, typically assuming inverse proportionality. However, the underlying empirical validation is limited.
6. There is **no peer-reviewed LCA** that systematically compares environmental impacts across **different weaving technologies** (air-jet, rapier, projectile, shuttle, water-jet). EF 3.1 datasets attempt this by applying "energy consumption ratios," but these ratios originate from **non-transparent or untraceable sources**, not from rigorous LCI studies.
7. Most weaving-related literature and industrial data are **10–15 years old**, despite rapid technological improvements. This makes current literature poorly representative of modern operations.
8. Across all reviewed sources, gaps in transparency, outdated numbers, and missing parameters highlight the necessity of **primary, mill-level data acquisition**
