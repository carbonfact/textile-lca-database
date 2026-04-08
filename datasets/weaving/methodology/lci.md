# Life Cycle Inventory

> Part of [Weaving Methodology](README.md)

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
