# Weaving

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

## 3. Life Cycle Inventory development for weaving

This chapter focuses on the life cycle inventory developed after literature review and secondary data collection for the weaving process keeping in the mind the variants.

### 3.1 Electricity consumption

**Methodology for weaving electricity consumption with respect to yarn linear density (dtex)**

The weaving energy model in this LCI covers the full set of preparatory and weaving operations—warping, sizing, drawing-in, loom operation, and inspection—as a combined energy value per kilogram of woven fabric.

Additionally, for transparency and diagnostic purposes, the underlying split of electricity across these individual subprocesses is retained in case root-cause analysis or sensitivity checks are required.

To model the effect of yarn dtex on weaving energy, all available literature reporting weaving-related energy consumption at known yarn fineness—including Koc et al. (2010) and the Idemat database was tabulated across multiple dtex values.

For each of these three sources, a best-fit curve was developed (typically inverse-power or logarithmic, consistent with weaving theory, where finer yarn requires more picks per unit area). The average of the two best-fit curves was then evaluated. This equation is subsequently used to calculate weaving energy for all dtex values in the inventory.

This approach is methodologically valid because

- Uses multiple independent data sources, reducing bias,
- Captures the well-established inverse relationship between yarn linear density and weaving energy

*(figure)*

*(figure)*

$$
Electricity (kWh/kg)= 1653.6(dtex) ^{-0.996}
$$

**Methodology for weaving electricity consumption with respect to loom technologies**

For variation across loom technologies, the model applies specific energy consumption ratios between loom types (air-jet, rapier, projectile, shuttle, water-jet, Jacquard) based on published comparisons from peer-reviewed papers and technical reports.

These ratios—derived for similar yarn dtex and fabric constructions—are used to scale the baseline weaving energy. The underlying assumption is that the relative energy difference between loom technologies (e.g., air-jet using 1.3–1.8x more energy than rapier) remains proportionally similar when applied to the combined weaving energy value. All consumable flows (size chemicals, humidity losses, auxiliary electricity) are assumed to remain constant across loom technologies, except for water-jet looms, where water consumption is explicitly added to reflect hydrodynamic weft insertion. This assumption is acceptable because loom-type differences predominantly affect weft insertion energy and compressed air demand, while preparation processes like sizing, warping, and drawing-in remain largely unchanged.

| Loom type | Specific energy consumption (kWh/kg) [2] | Ratio |
| --- | --- | --- |
| Shuttle loom | 1.8 | 0.5625 |
| Projectile loom | 1.3 | 0.40625 |
| Rapier loom | 2.5 | 0.78125 |
| Air jet loom | 3.2 | 1 |
| Water jet loom | 0.9 | 0.28125 |
| Jacquard loom | 2.7 | 0.84375 |

### 3.2 LCI for sizing

For producing a woven fabric, sizing is one of the important steps to increase the efficiency of weaving productions. Sizing operation is the only process step requiring steam and indirect heating is performed through electricity, coal or natural gas combustion through boilers.

**Electricity and thermal energy**

Most studies show that the energy demand of sizing is driven mainly by the machine's fixed mechanical load which remain largely independent of yarn count, fiber type (cotton vs. synthetics), or the specific size material used.

Research in textile processing consistently reports that electrical consumption for warp transport, immersion, squeezing, and cylinder rotation is effectively constant per machine at a given speed.

Therefore, assuming the same electrical energy inputs across all yarn counts and fiber types is considered reasonable and does not materially affect LCI accuracy.

| **Reference** | **Sizing electricity consumption (MJ/kg)** | **Sizing thermal energy consumption (MJ/kg)** |
| --- | --- | --- |
| Training for Energy Managers in T&G Factories_Day2_HO_The Textile Company_Energy Baseline_Solution - [Sustainable Industrial Areas](http://sia-toolbox.net/resources?name=textile&field_topics_target_id=5) | 0.953 | 10 |
| Koc E., Cincik E.; [Analysis of Energy Consumption in Woven Fabric Production.](https://scispace.com/pdf/analysis-of-energy-consumption-in-woven-fabric-production-5aahud6bvl.pdf) FIBRES & TEXTILES in Eastern Europe 2010, Vol. 18, No. 2 (79) pp. 14-20. | 1.08 | 5 |
| [Use of Radio Frequency Energy to Dry Warp Yarn in Sizing](https://www.researchgate.net/publication/249776268_Use_of_Radio_Frequency_Energy_to_Dry_Warp_Yarn_in_Sizing) MORTON W. REED AND WARREN S. PERKINS Auburn University Department of Textile Engineering | Unavailable | Ethermal_MJ_per_kg = (2.257 * W) / efficiency Where: **Ethermal_MJ_per_kg** = Thermal energy in MJ per kg yarn **W** = kg water evaporated per kg yarn **efficiency** = dryer thermal efficiency (e.g., 0.55–0.75) |

Electricity consumption for sizing was chosen as 1.08 MJ/kg - conservative estimate.

For thermal energy, the formula related to amount of water evaporated was used.

$$
E_{thermal}(MJ / kg) = (2.75 * W) / efficiency
$$

Where:

- **W** = kg of water evaporated per kg of yarn
- **efficiency** = dryer thermal efficiency (0.55 – 0.75 range from source; **0.65** average was chosen)

**Sizing material**

Sizing recipes were chosen according to the type of yarn fibre as widely reported in literature.

**Natural Fibers (Cotton)**

The cotton sizing recipe was extracted from a [study](https://www.wtin.com/article/2023/november/06-11-23/investigating-textile-sizing-polymers/) conducted by a sizing chemical supplier. This source presents a commercially-representative formulation based on maize starch and wax.

**Recipe summary:**

| Component | Amount | % of Solids | % of Total Recipe |
| --- | --- | --- | --- |
| Maize starch | 72 kg | 92% | 8% |
| Wax | 6 kg | 8% | 1% |
| Water | 822 kg | – | 91% |
| **Final liquor volume** | **900 L** | – | – |

The resulting **solids concentration** was computed as:

$$
\text{Solid concentration (\%)} = \frac{\text{Amount of size chemical}}{\text{Total liquor volume}} \times 100
$$

Here Solids concentration (%)= 9 %

---

**Synthetic Fibers (Polyester / Synthetic Spun Yarn)**

The synthetic sizing recipe was taken from the industrial formulation provided by [Textile Trainer](https://textiletrainer.com/standard-sizing-recipe-of-synthetic-spun-yarn/) ("Standard Sizing Recipe of Synthetic Spun Yarn", 2023).

**Recipe summary:**

| Component | Amount | % of Solids | % of Total Recipe |
| --- | --- | --- | --- |
| Starch | 160 kg | 70% | 13% |
| CMC | 30 kg | 13% | 2% |
| PVOH | 30 kg | 13% | 2% |
| Wax | 10 kg | 4% | 1% |
| Water | 1000 kg | – | 81% |
| **Final liquor volume** | **1230 L** | – | – |

The resulting **solids concentration** was computed as:

$$
\text{Solid concentration (\%)} = \frac{\text{Amount of size chemical}}{\text{Total liquor volume}} \times 100
$$

Here Solids concentration (%)= 19 %

---

**Yarn count-based calculations**

The variation of **size add-on percentage** with yarn count (Ne) was derived from a sizing performance document published by Karl Mayer, a leading sizing machine manufacturer. This source provides empirically observed size add-on values across common yarn counts.

- **User selects the yarn fineness (dtex).** This value serves as the primary input for determining sizing requirements.
- **Determine the size add-on percentage using the linear correlation model.**

$$
y = -0.0004x + 0.198
$$

*(figure)*

The model is derived from empirical data (Karl Mayer technical report) linking dtex or Ne to dry size add-on (%).

- **Convert dry add-on (%) to liquor wet pick-up (%) using solids concentration.**

$$
\text{Wet pick-up \%} = \frac{\text{Add-on \%}}{\text{Concentration \%}}
$$

- **Calculate water pick-up based on the water composition of the final liquor.** The wet pick-up (%) is multiplied by the water fraction in the final liquor volume:
- **Apply the fiber-specific moisture retention factor.** A **moisture retention factor of 7%** (kg water retained per kg oven-dry cotton yarn) was adopted based on [thumb-rule values](https://csitc.org/sitecontent/RTCEA/internal_ea/02_RTC_Content/022_Training/0222_Training_documents/02222_TICS/Yarn_Fabric_Processing/0222251_TICS_sizing_calculations.pdf). Moisture retention for synthetic yarns was taken as **3%**, consistent with standard sizing guidelines indicating significantly lower moisture regain for hydrophobic fibers.

The amount of water retained in the yarn (e.g., 7% for cotton, 3% for synthetic fibers) is subtracted from the total water picked up to obtain.

- **Calculate thermal energy consumption (MJ/kg yarn).** Thermal energy is computed using the latent heat of evaporation (2.75 MJ/kg water) and dryer efficiency of 0.55

Additional information on recipes, concentration calculations, moisture retention factors, and energy assumptions is documented in the accompanying LCI file for sizing.

Sizing calculation and general rules of thumb - [csitc.org](https://csitc.org/sitecontent/RTCEA/internal_ea/02_RTC_Content/022_Training/0222_Training_documents/02222_TICS/Yarn_Fabric_Processing/0222251_TICS_sizing_calculations.pdf)

Sizing presentation - [Sizing](https://www.slideshare.net/slideshow/sizing/37598595#1)

**Capital goods and building infrastructure**

Similar to knitting datasets, using weight of the machinery, lifespan and productivity (kg/h), the building machinery associated with 1 kg sizing has been calculated. The building infrastructure values were taken from ecoinvent dataset on weaving.

**LCI for 1 kg of input yarn undergoing sizing (example: natural fibre and 197 dtex)**

| **Activity** | **Value** | **Unit** | **Source / Rationale** |
| --- | --- | --- | --- |
| **Sizing agent** | 0.109664 | kg | Derived from **8% of total size chemicals**, as reported in the sizing supplier's technical data for synthetic yarn formulations. The value is scaled according to the total solids requirement calculated from yarn count-dependent size add-on. |
| **Wax** | 0.009536 | kg | Corresponds to **92% of total sizing auxiliaries** based on the supplier's material composition breakdown. Wax contributes to lubrication and abrasion resistance and is included proportionally to the sizing solids applied. |
| **Water** | 1.2004 | kg | Computed from the **wet pick-up** derived from size add-on (%) and solids concentration (%) of the liquor. Water requirement varies by yarn count and liquor composition; the detailed calculation procedure is described in the methodology section. |
| **Building hall** | 6.90E-05 | m2 | Allocated share of building area using the **Ecoinvent dataset**: textile production, cotton, weaving |
| **Building machinery** | 1.17E-08 | item | Estimated based on the **total weight and expected lifetime** of sizing machinery. Infrastructure impacts are amortised over total production output to obtain use-phase allocation. |
| **Electricity** | 0.264722222 | kWh | Electricity consumption per kg yarn sourced from the **Resource Efficient Management of Energy (REME) – SIA Project (Bangladesh)**, which provides benchmark energy use for sizing, drying, and auxiliary operations. |
| **Thermal energy** | 5.58186 | MJ | Computed from the **amount of water evaporated** (difference between water pick-up and moisture retention) multiplied by the latent heat of evaporation and divided by the assumed dryer efficiency. Full methodology is presented in the main report. |
| **Wastewater** | 0.0558186 | kg | Assumes **5% loss of size liquor** in the form of overflow, drainage, and preparation losses, consistent with typical sizing room loss factors reported in technical guidelines. |
| **Water to air** | 1.0605534 | kg | Represents **95% of water evaporated** in the dryer section, based on standard operational assumptions for slasher sizing where nearly all absorbed water is removed thermally. |
| **End-of-life machinery** | 1.76E-05 | kg | Calculated using the **sizing machine mass and service lifetime**, with end-of-life impacts allocated proportionally to throughput. |
| **Output: sized yarn** | 1.203228 | kg | Total output mass equals the input dry yarn mass plus retained moisture and applied size solids after drying. |

### 3.3 Life cycle inventory for weaving

Apart from the energy consumption highlighted in previous section, the following assumptions were made for LCI of weaving as a service.

**Capital goods:**

Similar to knitting datasets, using weight of the machinery, lifespan and productivity (kg/h), the building machinery associated with 1 kg sizing has been calculated. The building infrastructure values were taken from ecoinvent dataset on weaving. Further information on capital good related assumptions can be viewed in the LCI file.

**Yarn loss:**

Loom type is the dominant driver of yarn loss during weaving (selvedge method, weft insertion system, lubrication and oiling losses, number/type of moving parts, and stoppage profile vary strongly by loom). Yarn fineness (dtex/Ne) matters as it affects knotting/splice loss and breakage probability but its influence is secondary and usually shows up within the failure modes controlled by the loom and process settings.

| Loom type | Recommended typical yarn-loss (%) per kg woven fabric | Rationale |
| --- | --- | --- |
| **Air-jet loom** | **6%** | Haque & Majumder, *Study on Material Wastes in Air-jet Weaving Mills* — reported warp waste 2.59–3.96% and weft waste 2.43–3.51% in two sample mills (sum approximately 5–7%). |
| **Rapier loom** | **7%** | Rapier looms commonly show higher selvedge consumption (study reports 4–8% selvedge alone) and moderate breakage. Hence compared with air-jet, a slight increase of yarn loss% is assumed |
| **Projectile loom** | **6%** | Projectile looms are shuttleless with robust weft insertion and relatively low selvedge waste versus rapier. They tend to have slightly lower stoppages than rapier but somewhat higher mechanical complexity than air-jet. Due to dearth of data, same yarn loss % as air jet is assumed. |
| **Water-jet loom** | **4%** | Water-jet looms generally have low mechanical weft handling losses for synthetic yarns and efficient insertion; empirical vendor notes and industry summaries indicate lower yarn loss than rapier/rapier-like looms. |
| **Shuttle** | **12%** | Historic shuttle looms exhibit much higher waste due to shuttle handling, larger selvedge waste and more frequent manual stoppages. Due to unavailability of data, two times more yarn loss than air jet loom is assumed. |
| **Jacquard** | **9%** | Jacquard heads increase small-part motion and selvedge/auxiliary consumption. |

Below is the life cycle inventory of weaving operation for 197 dtex natural fibre

| **Activity** | **Value** | **Unit** | **Source / Rationale** |
| --- | --- | --- | --- |
| **Lubricating oil** | 0.0305 | kg | Value taken from Roos et al. (2015), Chemical LCI Inventory, which provides default lubricant consumption factors for weaving machinery. This represents typical oil losses from central and point lubrication systems under standard operating conditions. |
| **Sizing operation (sized warp input)** | 1.203 | kg | Represents the input warp yarn after sizing, entering the weaving stage. The mass reflects size add-on and moisture retention calculated in the sizing LCI. Documented in the sizing methodology section. |
| **Building hall** | 6.90E-05 | m2 | Derived from the Ecoinvent dataset: "textile production, cotton, weaving" |
| **Building machinery** | 4.93E-07 | item | Calculated based on the total mass of weaving machinery (loom plus auxiliary devices) and its expected technical lifetime (years and operating hours). The infrastructure burden is amortized over total loom output. |
| **Electricity** | 8.57318 | kWh | Calculated based on the yarn count - power |
| **Waste yarn** | 0.07219368 | kg | Computed based on average yarn-loss percentages by loom type, derived from literature and mill-study data. Includes warp & weft waste, selvedge waste, and knotting losses. |
| **Waste paperboard** | 0.02 | kg | Adopted from Ecoinvent dataset "textile production, cotton, weaving" |
| **Waste mineral oil** | 0.0305 | kg | Estimated using Ecoinvent waste flows for weaving and consistent with the assumed input of lubricating oil. |
| **End-of-life machinery** | 2.22E-03 | kg | Calculated through capital goods amortization: machinery mass divided by total lifetime production. Includes disposal burdens of steel at end of life. |
| **Output woven fabric (from sized yarn)** | 1.13103432 | kg | Resulting mass of woven fabric after subtracting yarn waste fractions from the sized yarn input. |

## 4. Life Cycle Impact Assessment

Below are the comparison of climate change (kg CO2eq) values between available EF 3.1 datasets and LCI weaving model developed by Carbonfact.

| **S.No** | **Process Name** | **EF 3.1 (kg CO2eq)** | **Carbonfact LCI (kg CO2eq)** | **Percentage reduction in impacts from EF datasets %** | **Analysis** |
| --- | --- | --- | --- | --- | --- |
| 1 | weaving, 45 dtex-41 denier- 130/1 ne-222 nm service | 28.9 | 22.2 | 23% |  |
| 2 | weaving, 70 dtex-63 denier-84/1 ne-143 nm service | 18.8 | 14.95 | 20% |  |
| 3 | weaving, 120 dtex-108 denier-49/1 ne-83 nm service | 11.22 | 9.43 | 16% |  |
| 4 | weaving, 150 dtex-135 denier-40/1 ne-67 nm service | 9.09 | 7.86 | 14% |  |
| 5 | weaving, 170 dtex-153 denier-34/1 ne-59 nm service | 8.08 | 7.11 | 12% |  |
| 6 | weaving, 200 dtex-180 denier-30/1 ne-50 nm service | 6.96 | 6.26 | 10% |  |
| 7 | weaving, 250 dtex-225 denier-24/1 ne-40 nm service | 5.68 | 5.27 | 7% |  |
| 8 | weaving, 300 dtex-270 denier-20/1 ne-33 nm service | 4.82 | 4.57 | 5% | On average, the Carbonfact LCI shows about a 10-11% on average lower electricity demand than the EF 3.1 dataset, partly because the two systems use different electricity suppliers and grid emission factors. In addition, Carbonfact LCI adjusts sizing energy consumption based on yarn count, whereas EF 3.1 applies a single, fixed sizing impact across all counts, further contributing to the difference between the two results. |
| 9 | weaving, 330 dtex-297 denier-18/1 ne-30 nm service | 4.44 | 4.25 | 4% |  |
| 10 | weaving, 370 dtex-333 denier-16/1 ne-27 nm service | 4.02 | 3.87 | 4% |  |
| 11 | weaving (different fabric counts) service, Mix of different counts | 10.21 | 8.58 | 16% | This dataset from EF 3.1 is an average of the previous 10 datasets of yarn count ranging from 45 dtex to 370 dtex |
| 12 | weaving, air-jet service | 12.2 | 10.99 | 10% | The EF 3.1 dataset does not specify the yarn dtex used, but comparing electricity consumption across the count-specific datasets indicates that the values correspond most closely to yarns around 100 dtex. Therefore, Carbonfact applies 100 dtex as a consistent reference for all loom-type datasets. |
| 13 | weaving, generic water-jet service | 8.41 | 3.88 | 54% | Prassana et al. report that water-jet weaving requires approximately 3.5 times less energy than air-jet weaving, but the EF 3.1 dataset applies only a 35% reduction, which significantly understates this difference. In contrast, the Carbonfact LCI currently applies the full ratio reported by Prassana et al., aligning water-jet energy consumption with the values supported in the literature. |
| 14 | weaving, jacquard service | 11.57 | 9.82 | 15% | On average, the Carbonfact LCI applies electricity consumption values that are about 10–11% lower than those used in the EF 3.1 dataset, and this difference carries through to the loom-specific results as well. In addition, although EF 3.1 references the energy ratio reported by Prassana et al. in its documentation, this ratio is not consistently or rigorously applied within the EF dataset, contributing to discrepancies between the two sources. |
| 15 | weaving, rapier service | 9.50 | 8.96 | 6% |  |
| 16 | weaving, shuttle service | 9.39 | 7.25 | 23% |  |
| 17 | weaving, others service | 10.21 | 8.18 | 20% | Average of EF 3.1 datasets focused on loom type (13-16) |
| 18 | weaving, water jet loom, 83 dtex, SpinDye service | 13.09 | 4.53 | 65% | There is considerable uncertainty in the EF 3.1 yarn-dyed water-jet weaving dataset because the documentation does not explain how its energy values were determined or why they deviate so strongly from the generic water-jet process. The 83 dtex yarn-dyed dataset shows roughly 37% higher energy consumption, yet this increase is unjustified, especially since yarn dyeing occurs upstream and does not materially change the mechanical energy required for loom operation. Carbonfact therefore applies the validated lower energy ratio for water-jet weaving from Prassana et al. and models yarn-dyed weaving in line with standard mechanical energy behaviour. |
| 19 | weaving, (150 dtex), cotton (twill fabric) service | 9.48 | 8.24 | 13% | Twill fabrics typically require more weaving energy than plain fabrics because their longer floats and more complex interlacing patterns demand higher beat-up force. Since no robust published data quantify this difference, the Carbonfact LCI adopts the same relative increase observed in EF 3.1—approximately **4.7% higher energy use for twill compared with plain weave.** |
| 20 | weaving, silk service | 9.62 | 11.08 | -15% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 21 | weaving of carpet production | 3.67 | 6.09 | -66% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 22 | weaving of primary backing service | 1.23 | 1.65 | -34% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 23 | sizing, natural fibers; single-end sizing; production mix, at plant; service | 0.607 | 0.775 | -28% | No specific dtex value or size chemical composition has been mentioned by EF. Carbonfact LCI can compute for various size compositions and yarn counts. Here the value is mentioned for 200 dtex (Carbonfact LCI) |
| 24 | sizing, synthetic fibers; single-end sizing; production mix, at plant; service | 0.561 | 0.643 | -15% | No specific dtex value or size chemical composition has been mentioned by EF. Carbonfact LCI can compute for various size compositions and yarn counts. Here the value is mentioned for 200 dtex (Carbonfact LCI) |

### Data quality rating

The PEF (Product Environmental Footprint) framework utilizes the DQR (Data Quality Rating) guideline to assess the quality of data employed in Life Cycle Assessment (LCA) studies.

This guideline assigns a score between 1 and 5 to each data point, considering four criteria:

- Precision (P), reflecting the accuracy of data;
- Time Representativeness (TiR), evaluating the data's age and relevance to the study period;
- Technological Representativeness (TeR), assessing how well the data reflects the actual production technology; and
- Geographical Representativeness (GR), determining whether the data is representative of the geographical location of the studied product system.

The DQR is calculated by averaging the weighted scores of all individual criteria (DQR = (P + TiR + TeR + GR) / 4).

Table 1 Data Quality Rating according to PEF

| **Overall data quality rating (DQR)** | **Overall data quality level** |
| --- | --- |
| DQR < 1.5 | Excellent quality |
| 1.5 < DQR < 2.0 | Very good quality |
| 2.0 < DQR < 3.0 | Good quality |
| 3.0 < DQR < 4.0 | Fair quality |
| DQR > 4.0 | Poor quality |

This scoring system allows for a standardized and transparent approach to data quality evaluation, ensuring the robustness and reliability of LCA studies within the PEF framework.

According to PEFCR, relevant process related datasets are those that contribute cumulatively to 80% of the single weighted LCIA score/ climate change impact. Once identified the datasets are individually scored for their DQR (expert judgement) and then a weighted average is taken to identify the DQR for the overall product.

| **Dataset group** | **Data quality rating** | **Comment** |
| --- | --- | --- |
| Weaving as a service \| Different fabric counts | 2.75 | We now have possibility to perform LCA for any yarn count and also alter sizing composition and thermal energy based on input data. |
| Weaving as a service \| Different loom types | 2.99 | Loom based energy consumption can be significantly improved based on primary data. Currently one journal source dictates the various energy consumptions (Prassana et al.) |
| Weaving as a service \| Carpet | 3.99 | Minimal data availability. Priority for primary data capture. |
| Weaving as a service \| Silk | 3.98 | Minimal data availability. Priority for primary data capture. |
| Weaving as a service \| Primary Backing Fabric | 3.45 |  |
| Sizing as a service \| Natural and Synthetic Fibre | 2.79 | We now have parameterised various sizing variables like size add up %, size composition, water pick up rate, thermal energy consumption etc. |

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
