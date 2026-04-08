# Dyeing

## 1. Purpose of the study

The Life Cycle Inventory (LCI) review and modelling in this study has been undertaken with the objective of replacing the existing Environmental Footprint (EF) 3.1 datasets, which currently suffer from very low transparency, limited methodological documentation, and restricted access to underlying inventory data. In contrast, this study adopts a transparent, literature-supported, and verifiable LCI approach

### 1.1 Context

### 1.2 Classification of dyeing processes

An initial classification was proposed based on literature review and can be benchmarked based on ranges provided by Apparel Impact Institute.

### 1.3 System boundaries

Included in boundaries:

- (2) Core Dyeing
- (3) Washing and Rinsing
- (4) Drying, Tumble drying and Padding

Excluded from boundaries:

- (1) Pre-treatment stages (upstream): already included in preparation step in the EFS `PREPARATION#ANY`
- (5) Sanforization (pre-shrinking fabric to avoid shape changes in further laundry stages): already included as a finishing step in the EFS `FINISHING/SANFORIZATION`
- (6) Compact finishing (fixing shrinkage values of fabric in a stenter post-dyeing): already included as a finishing step in the EFS `FINISHING/COMPACTING/MECHANICAL`

### 1.4 Scope

## 2. Literature review and observations

### 2.1 Facility benchmark from Apparel Impact Institute

The benchmark of wet processes from facilities is classified using the following parameters:

- Process group (Dyeing only - without pre-treatment, Dyeing - full process, Printing Only, Washing Only...)
- Substrate type (Fibre, Yarn, Fabric, Garment)
- Fabric type (Woven, Knit, Denim)
- Fibre/blend processed (Acrylic, Cotton, Lyocell, Polyester, Wool, Blend...)
- Process description (Exhaust dye without pre-treatment, Continuous dye without pre-treatment)
- Dye type (Acid, Disperse, Reactive, Indigo...)

An extract of the benchmark was done to obtain all dataset values (214 datasets) with the specific dyeing properties:
Process group = `Dyeing Only (without Pre-treatment)` (85 datasets) and Process group = `Dyeing (full process)` (129 datasets).

Only the energy consumption of the following steps will be included for comparison:

- Dye/Print
- Wash-off/Wash
- Fin1: *corresponds to drying and padding steps in the file*
- Fin2: *depends on what type of process is included in this column:*
  - If padding, it is included in the boundaries for dyeing
  - If sanforizing, it is excluded from the boundaries, as already covered in finishing

The energy consumption of these steps will be excluded:

- Pre-Prep1
- Pre-Prep2
- Prep
- Post-prep dry
- Fin3: Compacting already covered as a finishing step in the EFS

Allocations

- For yarn package dyeing, on an average of 24 datasets, 20% of energy demand comes from pre-processing (21% of heat and 18% of electricity).

### 2.2 Building and cleaning the data source

#### Data treatment

The following sources were used to determine the energy consumption of dyeing processes (Total energy demand [MJ], Electricity consumption [kWh] and Heat consumption [MJ]):

- Apparel Impact Institute, Benchmarking Tool (214 datasets)
- Supplier primary data collected by Carbonfact and on-site (20 datasets)
- Emission factor databases; EF3.1, ecoinvent and Ecobalyse (15 datasets)
- Scientific literature articles (14 datasets)

These sources were first compiled in a `Data_Sources` database, keeping as much as possible the naming conventions used in the raw files

*(figure)*

Then, the data was cleaned, harmonised in standardised columns with similar naming conventions, to obtain the `Energy_Database` that will be queried in the following stage.

### 2.3 Analysing the sensitivity of each parameter on energy consumption

#### Data exploration

*(figure)*

- Using the `Database_Classified`, we are going to analyse the sensitivity of each of the following parameters to the variation of the `Total energy demand [MJ]`:
  - Substrate type (Fibre, Yarn, Fabric, Garment)
  - Fabric type (Woven, Knitted, Denim, Unspecified)
  - Fibre group (Animal fibres, Cellulosic Fibres, Synthetics, Blends, Unspecified)
  - Process type (Exhaust, Continuous, Semi-continuous)
  - Process technology (Jet, Package, CPB, Airflow jet, Range, Front Loader, Softflow, Hank, Jigger, Beam, Pad Steam, Overflow, Slasher, Rope, Unspecified)
  - Dye type (Disperse, Reactive, Basic, Pigment, Acid, Vat, Mix, Unspecified)

- To do so, an analysis will be conducted in Python, sequentially fixing all parameters and varying one, and printing the standard variation for each line of fixed parameters.
  - *Example: the screenshot below shows the test performed on the parameter `Fibre group`: This parameter varies while all other parameters are fixed, the output providing results in 2 columns:*
    - *`energy_demand_std` displays the standard deviation of energy demand in MJ for all variations of the same dyeing scenario, but for different fibre groups (Animal fibres, Cellulosic Fibres, Synthetics, Blends, Unspecified)*
    - *`n_values_used` displays the number of datasets compiled to generate the standard deviation for each scenario, providing a measure of robustness.*

*(figure)*

- These tests were performed individually for each parameter. All blank values in `energy_demand_std` (corresponding to scenarios with only one possible entry for a specific parameter) were filtered out of the table.
- An average of all standard deviation for all scenarios ran for a specific parameter was built, along with a distribution profile.
  - *Example: comparing the distribution profile of Sdev(sigma) of different scenarios when testing the `Fabric type` parameter vs when testing the `Process technology`*

*(figure)*

*(figure)*

- Finally, a table was built to compare the sensitivity of each parameter, including:
  - Average Sdev (sigma) per parameter: the mean of all scenarios' standard deviations built for the parameter variation
    - *Example: for the `Fibre group` parameter, Average Sdev (sigma) = 3.8*
  - Nb scenarios considered: the number of scenarios computed to obtain the Average Sdev (sigma)
    - *Example: for the `Fibre group` parameter, Nb_scenarios = 15*
  - sigma_max, corresponding to the scenario with the highest standard deviation
    - *Example: for the `Fibre group` parameter, sigma_max = 13.5*
  - sigma_max Scenario, name of the scenario with the highest standard deviation
    - *Example: for the `Fibre group` parameter, sigma_max Scenario = Yarn, Exhaust, Hank, Acid*

*(figure)*

*(figure)*

- Comment: linked parameters were also defined to avoid grouping by one parameter when the linked one was tested (e.g: if a `Process Technology` is "Jet", then the `Process Type` is always "Exhaust", it would not make sense to study energy variations between "Exhaust" and "Continuous" `Process Type` on a "Jet" `Process Technology`.
  - Contingency `Process Technology` <-> `Process Type`: 100% contingency for all technologies (excluding unspecified).

| **Process technology** | **Continuous** | **Exhaust** | **Semi-continuous** |
| --- | --- | --- | --- |
| **Airflow jet** | 0 | 1 | 0 |
| **Beam** | 0 | 2 | 0 |
| **CPB** | 0 | 0 | 5 |
| **Front Loader** | 0 | 10 | 0 |
| **Hank** | 0 | 6 | 0 |
| **Jet** | 0 | 17 | 0 |
| **Jigger** | 0 | 1 | 0 |
| **Overflow** | 0 | 1 | 0 |
| **Package** | 0 | 13 | 0 |
| **Pad Steam** | 1 | 0 | 0 |
| **Range** | 11 | 0 | 0 |
| **Rope** | 1 | 0 | 0 |
| **Slasher** | 1 | 0 | 0 |
| **Softflow** | 0 | 1 | 0 |
| **Unspecified** | 5 | 3 | 0 |

  - Contingency `Dye type` <-> `Fibre group`

| **Dye type** | **Animal fibres** | **Blends** | **Cellulosic fibres** | **Synthetics** | **Unspecified** |
| --- | --- | --- | --- | --- | --- |
| **Acid** | 5 | 2 | 0 | 7 | 0 |
| **Basic** | 0 | 0 | 0 | 3 | 0 |
| **Disperse** | 0 | 0 | 2 | 13 | 0 |
| **Mix** | 0 | 8 | 0 | 0 | 0 |
| **Pigment** | 0 | 0 | 2 | 0 | 2 |
| **Reactive** | 0 | 7 | 16 | 0 | 0 |
| **Unspecified** | 0 | 0 | 2 | 4 | 2 |
| **Vat** | 0 | 0 | 4 | 0 | 0 |

    - **`Animal fibres`** <-> `Acid`: 100% contingency
    - **`Synthetics`** <-> `Disperse`: 57% contingency; `Acid`: 30% contingency; `Basic`: 13% contingency
    - **`Cellulosic fibres`**: `Disperse` actually corresponds to the specific case of dyeing acetate, classified as a cellulosic fibre but with the properties of synthetics. `Pigment` corresponds to the indigo yarn dyeing of denim. After isolating these specific cases
      - **`Cellulosic fibres`** <-> `Reactive`: 80% contingency; `Vat`: 20% contingency
    - `Blends`: a mix of dyes is applied, corresponding to the typical dye used per material group composition in the blend.

#### Results

- `Fabric Type` is the parameter with the lowest standard deviation (sigma=2.1): we can infer that it does not significantly infer the energy consumption for a similar process. It could be excluded from the EF modelling rules, and an average EF could be built based on the contingency with other parameters (specifically `Process Technology`).

#### Data treatment #2

After the first exploration insights, a few corrections were made to the data table:

- `Acetate` was determined as a specific `Fibre Group`
- `Fabric Type` was removed from the list of parameters

The new contingency matrix `Dye type` <-> `Fibre group`, also excluding blends which will be associated with a mix of dye types, is as follows:

| **Dye type** | **Acetate** | **Animal fibres** | **Cellulosic fibres** | **Synthetics** |
| --- | --- | --- | --- | --- |
| **Acid** | 0 | 5 | 0 | 5 |
| **Basic** | 0 | 0 | 0 | 3 |
| **Disperse** | 1 | 0 | 0 | 9 |
| **Mix** | 0 | 0 | 0 | 0 |
| Indigo | 0 | 0 | 2 | 0 |
| **Reactive** | 0 | 0 | 10 | 0 |
| **Vat** | 0 | 0 | 4 | 0 |

## 3. Life Cycle Inventory development for dyeing

### 3.1 Electricity consumption

### 3.2 Heat consumption

*(figure)*

A mapping with heat production datasets from ecoinvent was performed.

- Initially, a mapping of all heat production was performed with the activity **`steam production, as energy carrier, in chemical industry (RoW)`**
  - After a first LCIA analysis, it was observed that this energy dataset overestimated significantly heat production impacts compared to benchmark databases.
  - The reason was that this dataset included as background a mix of heat production sources (natural gas, hard coal and light fuel oil), but applied an energy loss rate between MJ of heat production at boilers and MJ of useable steam in the final process (22% loss assumed).
  - The LCI collected data in MJ represented the actual energy content of fuels used to generate heat in boilers. 2 corrections were made:

1. Removing energy losses from boiler energy output to useable steam in the process: `Heat, for dyeing process, production mix` has been rebuilt by Carbonfact, using following inventory from ecoinvent 3.12 (based on proportions from **`steam production, as energy carrier, in chemical industry`**:
   - 50% `heat production, natural gas, at industrial furnace >100kW (RoW)`
   - 20% `heat production, at hard coal industrial furnace 1-10MW (RoW)`
   - 30% `heat production, light fuel oil, at industrial furnace 1MW (RoW)`
2. Downscaling from boiler energy output in MJ to energy content of input fuels used MJ, by removing boiler efficiency. For each heat production process, the efficiency factors of each ecoinvent process were removed (using fuel LHV when necessary):

| Process name | Heat production efficiency (eta) |
| --- | --- |
| `heat production, natural gas, at industrial furnace >100kW (RoW)` | 0.95 |
| `heat production, at hard coal industrial furnace 1-10MW (RoW)` | 0.8 |
| `heat production, light fuel oil, at industrial furnace 1MW (RoW)` | 0.95 |

### 3.3 Auxiliary chemicals

**Rules for exhaust dyeing**

To specify the quantity of chemicals used for each dyeing process, a default liquor ratio will be assumed for exhaust dyeing processes. Liquor ratio = weight ratio of dry textile to total liquor, e.g. 1:10 = 10 L dye bath per 1 kg textile.

- This means that a fixed repartition of the chemical inventory will be applied for all exhaust dyeing datasets.
- However, the absolute quantity of chemicals used (in kg) will be adapted based on the liquor ratio of each Substrate/technology/dye type. All chemical recipes are expressed in a dosage in g/l. Therefore, the liquor ratio will specify the volume of the solution per kg of material dyed and therefore the total mass of dyes used.

**Rules for continuous and CPB dyeing**

- All chemical recipes are expressed in % on weight of fabric (OWF). This means that the quantity of fabric (or substrate in general) can be directly multiplied with the %,OWF of each chemical to generate a final inventory in kg. The parameter to monitor here is the "pick-up rate" and not the liquor ratio.

### Introduction

Wet processing stage is one of the significant processes involving chemical usage in textiles. Speciality chemicals and dyes are used across pretreatment, dyeing and post treatment stages and this continues into the finishing stages. Following is a table highlighting the various speciality chemicals that are used in dyeing processes.

| Process / chemical type | Stage | Function |
| --- | --- | --- |
| Desizing agents (enzymatic / chemical) | Pre-treatment | Removal of sizing chemicals applied during weaving |
| Scouring chemicals | Pre-treatment | Removal of natural impurities such as waxes, oils, and fats |
| Bleaching agents | Pre-treatment | Whiten fabric and remove natural colour |
| Mercerising chemicals | Pre-treatment | Increase fibre swelling, dye affinity, and strength |
| Bio-polishing enzymes | Pre-treatment | Remove surface fuzz and improve smoothness |
| Heat-setting auxiliaries | Pre-treatment | Stabilise fabric dimensions and reduce shrinkage |
| *Degumming chemicals* | *Pre-treatment* | *Remove sericin from silk* |
| *Carbonising chemicals* | *Pre-treatment* | *Remove vegetable matter from wool* |
| Wetting agents | Dyeing | Improve fabric wetting and liquor penetration |
| Levelling agents | Dyeing | Ensure uniform dye distribution |
| Dispersing agents | Dyeing | Maintain dye particles in suspension |
| pH control chemicals | Dyeing | Control acidity/alkalinity for dye-fibre bonding |
| Electrolytes (salt) | Dyeing | Promote dye exhaustion onto fibre |
| Dye carriers | Dyeing | Assist dye penetration (legacy polyester dyeing) |
| Antifoaming agents | Dyeing | Suppress foam during processing |
| Sequestering agents | Dyeing | Bind metal ions in process water |
| Textile dyes | Dyeing | Impart colour to the fabric |
| Soaping / washing agents | Post-treatment | Remove unfixed or hydrolysed dyes |
| Fixing agents | Post-treatment | Improve wash and rub fastness |
| Neutralising agents | Post-treatment | Adjust fabric pH to neutral |
| Softeners | Post-treatment | Improve fabric handle and softness |
| Resin finishing chemicals | Post-treatment | Improve wrinkle resistance and dimensional stability |
| Anti-creasing agents | Post-treatment | Prevent creases and fabric distortion |
| Enzyme washing agents | Post-treatment | Enhance softness and colour clarity |

Regarding textile dyes, the following classification has been taken from [Yousaf et al. 2023](https://journal.gnest.org/sites/default/files/Submissions/gnest_05145/gnest_05145_published.pdf).

*(figure)*

Below is a summary table

| Dye class | Fibers dyed | Fixation mechanism | Typical use |
| --- | --- | --- | --- |
| Reactive dyes | Cotton, viscose | Covalent bond with fibre | Apparel, home textiles |
| Direct dyes | Cotton | Physical adsorption | Low-cost dyeing |
| Vat dyes | Cotton | Oxidation-reduction | Denim |
| Sulfur dyes | Cotton | Precipitation in fibre | Dark shades |
| Disperse dyes | Polyester | Physical diffusion | Synthetic fabrics |
| Acid dyes | Wool, silk, nylon | Ionic bonding | PA, protein fibres |
| Basic (cationic) dyes | Acrylic | Ionic bonding | Carpets, sweaters |
| Metal-complex dyes | Wool, nylon | Coordination complex | High fastness |

### Methodology for LCI

### Goal and scope definition

The objective of this work is to develop Life Cycle Inventory (LCI) datasets for textile specialty chemicals and dyes that can serve as robust alternatives to the Environmental Footprint (EF) 3.1 datasets, which are currently widely used but limited in granularity and transparency for textile wet processing applications.

The **functional unit** is defined as:

> 1 kg of textile chemical or dye, cradle-to-gate, ready to use in textile dyeing or wet processing.

The **system boundary** covers:

- Raw material extraction and upstream chemical precursors
- Chemical synthesis and processing
- Formulation and blending
- Energy, water, and auxiliary inputs
- On-site emissions and waste treatment up to factory gate

#### Overall methodological approach

The LCI development follows:

- Secondary data from peer-reviewed literature and established LCI databases
- Dataset structure and parameterisation analysis of EF 3.1 datasets
- Public-domain primary information, including Material Safety Data Sheets (MSDS) and technical product disclosures from leading chemical and dye suppliers

The methodology is designed recognising that textile chemicals and dyes are among the most **black-boxed processes** in industrial LCA due to confidentiality, proprietary formulations, and supplier-specific synthesis routes.

#### Data sources and data capture strategy

Data collection was carried out using the following sources:

1. **Peer-reviewed journals and technical literature**
   Used to identify:
   - Typical synthesis routes for dye classes and textile auxiliaries
   - Energy and material intensity ranges
   - Reaction yields and by-products
2. **Ecoinvent database**
   Used as a background database for:
   - Upstream raw materials (e.g. basic organic chemicals, acids, alkalis)
   - Energy supply, utilities, and waste treatment

It is to be noted that ecoinvent represents most textile dyes and auxiliaries using **generic organic chemical datasets**, often derived from an average of approximately 20 commonly used organic chemicals. This approach masks chemical-specific differences and introduces uncertainty when applied to textile wet processing.

*(figure)*

3. **Environmental Footprint (EF) 3.1 datasets**
   EF datasets were analysed to:
   - Understand dataset boundaries, assumptions, and allocation rules
   - Identify underlying background datasets and proxies
   - Assess limitations that this work aims to address through alternative LCIs
4. **Publicly available supplier information**
   Special emphasis was placed on:
   - MSDS sheets
   - Technical datasheets

Websites of major global textile chemical and dye suppliers (e.g. Archroma and similar top-tier suppliers) were systematically reviewed. MSDS documents were analysed to identify **chemical composition ranges**, hazardous constituents, solvents, and stabilisers disclosed under regulatory requirements.

#### Two-part data collection framework

LCI development for textile chemicals and dyes was structured into two complementary components:

#### Chemical and dye production (foreground supply)

This component focuses on the production of 1 kg of chemical or dye, including:

- Identification of dominant raw materials and intermediates
- Mapping of typical synthesis pathways (where available)
- Estimation of energy and utility requirements
- Allocation of emissions and wastes at the production stage

Where exact synthesis routes are unavailable due to confidentiality, chemically similar proxy substances were selected based on molecular structure, functional groups, and reaction complexity.

This step ensures comparability with EF-style datasets while improving chemical specificity wherever possible.

#### Use-phase relevance: dosage, concentration, and pick-up

To ensure usability in textile LCAs, production LCIs were complemented with process-relevant parameters, including:

- Typical dosage ranges (e.g. g/kg fabric or % owf)
- Concentration levels in dye baths or finishing liquors
- Pick-up ratios and fixation efficiencies
- Fate of chemicals (fixed to fabric vs discharged to wastewater)

This allows the developed LCIs to be scaled from "per kg chemical" to "per kg fabric processed", bridging the gap between chemical production inventories and textile process inventories.

Where applicable, differences between fibre types (e.g. cotton, polyester, wool) and dyeing technologies (batch, continuous, semi-continuous) were considered.

#### Addressing data gaps and "black-box" challenges

Textile specialty chemicals and dyes present several structural challenges for LCI development:

- **Lack of transparent production data** due to proprietary synthesis routes
- **Multiplicity of chemicals for the same function**, where several chemically distinct substances can perform identical roles (e.g. levelling agents, dispersing agents)
- **Aggregation in existing databases**, where dyes, auxiliaries, and finishing agents are represented by generic organic chemical averages

To address these issues, the following measures were applied:

- Only chemicals and dyes for which minimum composition or structural information is available in the public domain were included in the initial dataset development.
- Chemicals were classified by function, not by brand, allowing aggregation where appropriate while retaining functional relevance.
- Where multiple chemicals serve the same function, the methodology allows for future differentiation rather than forcing a single representative value.

---

#### Handling functional alternatives and variability

Following approaches similar to those described by **Roos et al.**, chemicals serving the same function can be grouped into:

- **Best-case** (lower-impact formulations)
- **Average-case** (industry-representative)
- **Worst-case** (higher-impact formulations)

This enables:

- Sensitivity analysis
- Substitution scenario modelling
- Transparent communication of uncertainty and variability

### Speciality chemicals LCIA

Detailed tabulation of speciality chemicals used in dyeing process can be found here: [Google Sheets](https://docs.google.com/spreadsheets/d/1kV3rGcBCFm6jTbT-Nz5edo18FONK1LzL/edit?usp=sharing&ouid=109658983613223573958&rtpof=true&sd=true)

Below analysis has been given for Climate change impact per kg of chemicals

#### 1. Wetting Agents

Improve initial wet-out of fibres/fabric so that water and chemicals penetrate uniformly, especially critical before scouring, bleaching, and dyeing.

**Climate impact (kg CO2eq per kg of chemical):**

- Non-ionic surfactant (alcohol ethoxylate + fatty acid) -> **4.16**
- Non-ionic surfactant mix (bleaching) -> **4.52**
- Ethoxylated alcohol (AE7) -> **2.68**

#### 2. Scouring Agents

Remove natural impurities, oils, waxes, and processing aids to prepare fabric for uniform bleaching and dyeing.

**Climate impact (kg CO2eq per kg of chemical):**

- Non-ionic surfactant (alcohol ethoxylate) -> **4.16**
- Polysiloxane-based scouring agent -> **8.55**

#### 3. Scouring & Soaping Agents

Simultaneously clean fabric and remove loosely held impurities or unfixed dyes during intermediate washing steps.

**Climate impact (kg CO2eq per kg of chemical):**

- Ethoxylated alcohol-based soaping agent -> **0.80**
- Polyacrylate-based soaping agent -> **1.08**

#### 4. Bleaching Agents (Oxidising)

Destroy natural colour bodies to increase fabric whiteness prior to dyeing or finishing.

**Climate impact (kg CO2eq per kg of chemical):**

- Hydrogen peroxide -> **1.75**

#### 5. Bleach Stabiliser

Control peroxide decomposition during bleaching, preventing fibre damage and shade variation.

**Climate impact (kg CO2eq per kg of chemical):**

- Magnesium sulphate -> **0.19**

#### 6. Chelating / Sequestering Agents

Bind metal ions (Ca2+, Mg2+, Fe2+) to prevent peroxide breakdown and dye precipitation.

**Climate impact (kg CO2eq per kg of chemical):**

- EDTA -> **4.83**

#### 7. Electrolytes / Salts

Increase dye exhaustion by reducing dye solubility and controlling ionic strength in the dye bath.

**Climate impact (kg CO2eq per kg of chemical):**

- Sodium chloride / sodium sulphate / potassium chloride mix -> **0.57**
- Sodium chloride (exhausting agent) -> **0.27**
- Sodium sulphate -> **0.76**

#### 8. Dispersing Agents

Keep disperse dyes finely suspended, preventing agglomeration and ensuring even dye uptake.

**Climate impact (kg CO2eq per kg of chemical):**

- Naphthalene sulfonic acid -> **1.51**
- Alcohol ether sulphate -> **2.64**
- Acrylic dispersion -> **3.50**

#### 9. Levelling Agents

Control the rate of dye uptake to ensure uniform shade and prevent patchiness.

**Climate impact (kg CO2eq per kg of chemical):**

- Non-ionic surfactant (EO derivative) -> **4.16**
- Non-ionic surfactant (fatty acid derivative) -> **4.88**
- Enzyme-based leveller -> **0.49**
- Diphenyl ether leveller -> **8.94**
- Mixed non-ionic surfactant system -> **0.49**

#### 10. Exhausting Agents

Promote transfer of dye from the bath to the fibre by increasing dye-fibre affinity.

**Climate impact (kg CO2eq per kg of chemical):**

- Sodium chloride -> **0.27**

#### 11. Anti-Migrating Agents

Prevent dye movement during drying or fixation, especially important for pad-dry-cure processes.

**Climate impact (kg CO2eq per kg of chemical):**

- Polyacrylate-based agent -> **3.61**

#### 12. Fixing Agents

Improve dye fixation and wet fastness by binding dye molecules to the fibre.

**Climate impact (kg CO2eq per kg of chemical):**

- Benzisothiazolinone based -> **4.86**
- Acetic acid (pH-based fixation aid) -> **2.60**

#### 13. pH Control & Neutralisation Agents

Adjust or stabilise bath pH for optimal reaction conditions during scouring, bleaching, dyeing, and fixation.

**Climate impact (kg CO2eq per kg of chemical):**

- Acetic acid -> **2.60**
- Citric acid -> **2.44**
- Acetic acid + ammonium sulphate mix -> **0.88**
- Caustic soda (NaOH) -> **0.77**
- Sodium hydroxide -> **0.77**
- Soda ash / sodium carbonate -> **0.35**

#### 14. Peroxide Killers

Destroy residual peroxide after bleaching to prevent dye degradation.

**Climate impact (kg CO2eq per kg of chemical):**

- Catalase enzyme -> **0.49**

#### 15. Reduction Agents / Reduction Clearing

Remove unfixed disperse dye from polyester surface after dyeing to improve fastness.

**Climate impact (kg CO2eq per kg of chemical):**

- Sodium dithionite -> **2.78**
- Sodium dithionite + formaldehyde blend -> **1.62**
- Sodium hydrosulphide -> **1.81**

#### 16. Lubricants

Reduce fibre-to-fibre and fibre-to-metal friction during wet processing.

**Climate impact (kg CO2eq per kg of chemical):**

- Polyacrylamide -> **3.61**
- Organophosphorus compounds -> **7.86**

#### 17. Refiners

Improve fabric handle and surface smoothness during dyeing or washing stages.

**Climate impact (kg CO2eq per kg of chemical):**

- Ethoxylated alcohol -> **2.68**

#### 18. Oligomer Removers

Remove polyester oligomers to prevent machine fouling and fabric deposits.

**Climate impact (kg CO2eq per kg of chemical):**

- Silicone emulsion -> **2.97**

#### 19. Soaping Agents (Aftertreatment)

Remove unfixed surface dye to improve rubbing and wash fastness.

**Climate impact (kg CO2eq per kg of chemical):**

- Non-ionic surfactant -> **4.16**
- Polyacrylate-based agent -> **3.61**
- Glycerol ester-based agent -> **0.87**

#### 20. Softeners

Improve fabric hand feel, drape, and tactile comfort during finishing.

**Climate impact (kg CO2eq per kg of chemical):**

- Polysiloxane softener -> **8.55**
- Soybean meal-based softener -> **0.91**
- Ethoxylated alcohol softener -> **2.68**

#### 21. Moisture Management Finishes

Enhance moisture absorption, wicking, and drying properties of finished fabric.

**Climate impact (kg CO2eq per kg of chemical):**

- Acrylic dispersion -> **3.50**
- Polyester resin (diluted) -> **0.76**

#### 22. Anti-Slippage Agents

Increase surface grip and reduce fabric slippage during use.

**Climate impact (kg CO2eq per kg of chemical):**

- Non-ionic surfactant (fatty acid derivative) -> **4.88**

#### 23. Polyethylene / Silicone Emulsions (Finishing)

Provide surface modification, lubrication, and durability in finishing processes.

**Climate impact (kg CO2eq per kg of chemical):**

- Silicone emulsion -> **2.97**
- Polysiloxane -> **8.55**

#### 24. Stiffeners

Increase fabric body and rigidity for specific end-use applications.

**Climate impact (kg CO2eq per kg of chemical):**

- PVOH / polyvinyl acetate-based stiffener -> **6.42**

### Overall observation

- **Highest per-kg climate impact functions:** Softeners, levellers (aromatic), lubricants, stiffeners
- **Lowest per-kg climate impact functions:** Salts, enzymes, alkalis, peroxide killers

### 3.4 Dyestuff types and quantities

Since detailed dye composition data and production process information are not available in peer-reviewed literature or public databases, the Life Cycle Inventory (LCI) for dyes will be developed using a **bottom-up, industry-informed approach**. Based on established industrial dye manufacturing knowledge, the likely production route and chemistry class (e.g. disperse, reactive, vat; azo- or anthraquinone-based) will first be identified.

Energy inputs and utilities will then be approximated by mimicking comparable production processes, either through engineering judgement or by selecting ecoinvent datasets that represent similar synthesis pathways, unit operations, and energy intensity. Where specific dye intermediates are not disclosed, a functionally equivalent dye base available in ecoinvent will be used as a proxy, and the inventory will be constructed by adjusting inputs to reflect the expected formulation and processing steps. This approach ensures methodological consistency, transparency, and alignment with ISO-compliant LCA practice, while reflecting realistic industrial dye production conditions despite data gaps.

### Disperse dyes

The disperse dye is produced via a conventional batch azo dye route involving diazotization of a substituted aromatic amine followed by low-temperature coupling with an activated aromatic component. In the first stage, the amine (CN-Br-PNA) is dissolved in concentrated sulfuric acid and cooled to 0-2 degrees C using a large quantity of ice. Sodium nitrite is then added to generate nitrous acid in situ, converting the amine into the corresponding diazonium salt. Maintaining very low temperature and strongly acidic conditions is critical to stabilize the diazonium intermediate and prevent decomposition or side reactions. The resulting diazotized slurry is subsequently transferred to the coupling stage.

In the coupling step, the diazonium solution reacts with the coupling component (M-9) in aqueous hydrochloric acid medium at 0-5 degrees C to form the insoluble azo dye. The dye precipitates as a fine suspension, which is separated by filtration and extensively washed to remove residual acids, inorganic salts, and unreacted organics. The combined mother liquor and wash water are sent to effluent treatment. The filter cake (wet dye) contains high moisture and is dried thermally (e.g., spray drying or tray drying), during which a large quantity of water is evaporated to obtain the final dry disperse dye powder.

Source: Disperse Blue 183 - Annex 1 - Environmental clearance application by [Parishi chemicals, India](https://drive.google.com/file/d/1i2o6ZtU3fR2b7fy-L9-FKoGR9WWezXTH/view?usp=sharing)

*(figure)*

#### Life cycle inventory

| **Input Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| --- | --- | --- | --- | --- |
| 2-nitroaniline | 0.525 | kg | 2-nitroaniline production \| 2-nitroaniline \| Cutoff, U - RER | The coupling intermediate was modeled using nitro-aniline production as a proxy, as both represent aromatic amine intermediates used in azo dye synthesis with comparable nitration-based manufacturing chemistry. |
| cooling energy | 3.29 | MJ | market for cooling energy \| cooling energy \| Cutoff, U - GLO | The cooling energy required to convert 7.5 kg of liquid water at an assumed initial temperature of 25 degrees C into ice at 0 degrees C was estimated by summing sensible and latent heat removal. The total thermodynamic cooling load is 3.29 MJ. |
| electricity, medium voltage | 0.41596 | kWh | market group for electricity, medium voltage \| electricity, medium voltage \| Cutoff, U - RER | Agitation electricity for diazotization, coupling, was estimated using a plaster mixing energy proxy (0.08 kWh/kg per stage). Also electricity consumption for spray drying was included. For filtration - ultrafiltration electricity consumption was used |
| heat, district or industrial, natural gas | 15.72 | MJ | market for heat, district or industrial, natural gas \| Cutoff, U - RER without CH | Spray drying energy was modeled using an industrial milk spray-drying dataset scaled by the process-specific moisture removal (3 kg water per kg dye). |
| hydrochloric acid, without water, in 30% solution state | 0.25 | kg | market for hydrochloric acid \| Cutoff, U - RER |  |
| o-phenylene diamine | 0.057 | kg | o-phenylene diamine production \| Cutoff, U - GLO | The MUA aromatic amine intermediate was modeled using o-phenylenediamine production as a proxy. |
| sodium nitrite | 0.0175 | kg | market for sodium nitrite \| Cutoff, U - RER |  |
| sulfuric acid | 3 | kg | market for sulfuric acid \| Cutoff, U - RER |  |
| tap water | 11 | kg | market for tap water \| Cutoff, U - RER without CH | 7.5 kg for ice conversion and 3.5 kg as water |
| **Output Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| Disperse dye | 1 | kg |  |  |
| wastewater, average | 11.7625 | l | market for wastewater, average \| Cutoff, U - RER without CH |  |
| Water | 3 | l |  |  |

### Reactive dye

Reactive Golden Yellow HER is manufactured through a multistep aqueous batch process involving diazotization, azo coupling, cyanuration (reactive group introduction), condensation, and final drying. In the first stage, K-Acid (an aromatic amine intermediate) is dissolved in hydrochloric acid and water, then cooled using ice to maintain low temperatures suitable for diazotization. Sodium nitrite is added to generate nitrous acid in situ, converting the amine group into a diazonium salt under controlled acidic conditions. The resulting diazonium solution is subsequently transferred to the coupling stage, where it reacts with the coupling component (MUA) in the presence of sodium bicarbonate (SBC) while maintaining low temperature with additional ice. This step forms the azo chromophore, producing a colored intermediate slurry.

The coupled product then undergoes cyanuration, in which cyanuric chloride is introduced to attach the reactive triazine group that enables covalent bonding with fibers during dyeing. Sodium bicarbonate is used to control pH and neutralize released acid, while ice maintains the required low reaction temperature. In the subsequent condensation stage, DASDA (a diamine sulfonic acid intermediate) reacts with the activated triazine moiety to complete the molecular structure of the reactive dye. The final reaction mass is spray dried to remove water and obtain the finished powder dye.

Source: Reactive Golden Yellow HER - Environmental clearance application by [Aditayam Industries](https://drive.google.com/file/d/1uicS1LhnXIXZV76G95Dj0FdcErakg7p4/view?usp=sharing)

*(figure)*

#### Life Cycle Inventory

| **Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| --- | --- | --- | --- | --- |
| cyanuric chloride | 0.1 | kg | cyanuric chloride production \| Cutoff, U - GLO |  |
| cooling energy | 1.14 | MJ | market for cooling energy \| Cutoff, U - GLO | Cooling energy to convert 2.6 kg of water into ice at 0 degrees C, equivalent to 1.14 MJ. |
| heat, district or industrial, natural gas | 21.4054 | MJ | market for heat, district or industrial, natural gas \| Cutoff, U - RER without CH | Spray drying energy scaled by moisture removal (4.085 kg water per kg dye). |
| hydrochloric acid, without water, in 30% solution state | 0.5 | kg | market for hydrochloric acid \| Cutoff, U - RER |  |
| sodium bicarbonate | 0.4 | kg | market for sodium bicarbonate \| Cutoff, U - RER |  |
| sodium nitrite | 0.07 | kg | market for sodium nitrite \| Cutoff, U - RER |  |
| tap water | 3.6 | kg | market for tap water \| Cutoff, U - RER without CH | 2.6 kg for ice conversion and 1 kg as water |
| electricity, medium voltage | 0.6668165 | kWh | market group for electricity, medium voltage \| Cutoff, U - RER | Agitation electricity for diazotization, coupling, cyanuration, and condensation estimated using a plaster mixing energy proxy (0.08 kWh/kg per stage). |
| naphthalene sulfonic acid | 0.1 | kg | naphthalene sulfonic acid production \| Cutoff, U - RER | DASDA was modeled using naphthalene sulfonic acid production as a proxy. |
| naphthalene sulfonic acid | 0.225 | kg | naphthalene sulfonic acid production \| Cutoff, U - RER | K acid was modeled using naphthalene sulfonic acid production as a proxy. |
| o-phenylene diamine | 0.09 | kg | o-phenylene diamine production \| Cutoff, U - GLO | MUA aromatic amine intermediate modeled using o-phenylenediamine. |
| **Output Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| Water | 4.085 | l |  |  |
| **Reactive dye powder** | **1** | **kg** |  |  |

### Vat dyes

Pigment Violet 23 (a vat pigment) is produced through a high-temperature organic synthesis carried out in an inert aromatic solvent, predominantly ortho-dichlorobenzene (ODCB), which serves as both reaction medium and heat transfer fluid. In the reaction stage, amino ethyl carbazole reacts with chloranil in the presence of benzene sulfonyl chloride and sodium acetate, which acts as an acid scavenger to neutralize hydrogen chloride generated during condensation. The process forms a highly conjugated carbazole-based pigment molecule through substitution and condensation reactions under controlled conditions. After completion, the reaction mass undergoes primary filtration, during which a large portion of ODCB is separated and recovered for reuse.

The filtrate is then subjected to distillation to recover additional solvent, followed by filtration and washing of the crude pigment with water to remove residual salts, unreacted reagents, and soluble impurities. The washed pigment cake is dried to remove retained moisture and traces of solvent. Finally, the dry material is pulverized to obtain the desired particle size and color strength, yielding Pigment Violet 23 as a fine powder.

Source: Pigment violet 23 - Environmental clearance application by [Agrasem colours](https://drive.google.com/file/d/17Wo0ICYiiKKJlxEy8XhR8HwHsamM6FOa/view?usp=sharing)

*(figure)*

#### Life Cycle Inventory

| Flow | Amount | Unit | Provider | Description |
| --- | --- | --- | --- | --- |
| electricity, medium voltage | 0.12245 | kWh | market group for electricity, medium voltage \| Cutoff, U - RER | Agitation electricity estimated using a plaster mixing energy proxy. |
| electricity, medium voltage | 0.3990631451 | kWh | market group for electricity, medium voltage \| Cutoff, U - GLO | Alkaline fusion high temp process - proxy from sodium aluminate production - ecoinvent |
| glycine | 0.82 | kg |  | Closest proxy for phenyl glycine |
| heat, district or industrial, natural gas | 2.62 | MJ | market for heat, district or industrial, natural gas \| Cutoff, U - RER without CH | Spray drying energy scaled by moisture removal (0.5 kg water per kg dye). |
| heat, from steam, in chemical industry | 10 | MJ | market for heat, from steam, in chemical industry \| Cutoff, U - RER | Alkaline fusion high temp process - proxy from sodium aluminate production - ecoinvent |
| sodium amide | 0.08 | kg |  |  |
| sodium hydroxide, without water, in 50% solution state | 0.1 | kg | market for sodium hydroxide \| Cutoff, U - RER |  |
| tap water | 0.5 | kg | market for tap water \| Cutoff, U - RER without CH |  |
| **Output Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| Vat dye | 1 | kg |  |  |
| Water | 0.5 | l |  |  |

### Acid dye

Acid Red 87 is produced through a bromination-based chemical modification of an existing dye intermediate (Solvent Yellow 94) followed by purification and formulation steps. In the initial stage, the substrate is reacted with bromine in an acidic methanolic medium in the presence of sodium chlorate and hydrochloric acid, with water acting as solvent. The bromination introduces bromine substituents into the aromatic structure, enhancing color properties and dye performance. Off-gases containing bromine vapors are treated in an alkali scrubbing system to convert them into sodium bromide solution, preventing atmospheric emissions. The reaction mass is then filtered and subsequently dried.

The dried intermediate is reprocessed through a mixing stage with methanol, water, and sodium hydroxide to adjust pH and dissolve impurities. This slurry undergoes a second filtration, followed by final drying to obtain the powdered Acid Red 87 dye.

Source: Solvent Yellow 94 - Environmental clearance report by [Agrasem industries](https://drive.google.com/file/d/1XIP_qIJEUQ4vPopK0hgt3a0TzLAT5oGJ/view?usp=sharing)

*(figure)*

#### Life Cycle Inventory

| Flow | Amount | Unit | Provider | Description |
| --- | --- | --- | --- | --- |
| 2-nitroaniline | 0.84 | kg | 2-nitroaniline production \| Cutoff, U - RER | Aromatic amine intermediate modeled using nitro-aniline production as a proxy. |
| bromine | 0.74 | kg | market for bromine \| Cutoff, U - GLO |  |
| electricity, medium voltage | 0.3236992 | kWh | market group for electricity, medium voltage \| Cutoff, U - RER | Agitation electricity estimated using a plaster mixing energy proxy plus spray drying and ultrafiltration. |
| heat, district or industrial, natural gas | 10.0608 | MJ | market for heat, district or industrial, natural gas \| Cutoff, U - RER without CH | Spray drying energy scaled by moisture removal (1.92 kg water per kg dye). |
| hydrochloric acid, without water, in 30% solution state | 0.088 | kg | market for hydrochloric acid \| Cutoff, U - RER |  |
| methanol | 0.4 | kg | market for methanol \| Cutoff, U - RER without RU |  |
| sodium chlorate, powder | 0.252 | kg | market for sodium chlorate, powder \| Cutoff, U - RER |  |
| sodium hydroxide, without water, in 50% solution state | 0.22 | kg | market for sodium hydroxide \| Cutoff, U - RER |  |
| tap water | 1.6 | kg | market for tap water \| Cutoff, U - RER without CH |  |
| **Output Flow** | **Amount** | **Unit** | **Provider** | **Description** |
| Acid dye | 1 | kg |  |  |
| wastewater, average | 1.6 | l | market for wastewater, average \| Cutoff, U - RER without CH |  |
| Bromine | 0.08 | kg |  |  |
| Water | 1.92 | l |  |  |

> The indigo pigments used for rope dyeing in denim production have not been modeled from primary data in this version of the database. A proxy with Anthraquinone based vat dyes was assumed.

### 3.5 Water consumption and wastewater management

Water consumption in textile dyeing is primarily governed by liquor ratio (bath volume relative to material weight), dye chemistry, machine design, and the number of washing and rinsing steps required after dye fixation. Traditional exhaust dyeing processes immerse the substrate in large dye baths to ensure uniform penetration and circulation, resulting in high water use. In contrast, modern low-liquor systems and continuous application technologies reduce bath volume by applying dye through padding, spraying, or air-assisted transport, thereby lowering water demand. Post-dye washing often dominates total consumption, particularly for dye classes that require removal of unfixed dye, salts, or by-products. Consequently, technologies that minimize rinsing or enable dry fixation tend to have substantially lower water footprints.

| Process route | Water (litre per kg) | Source |
| --- | --- | --- |
| COLORATION/DYEING/FABRIC/AIRFLOW/ACID#ANIMAL_FIBERS | 33 | 80% reduction from conventional dyeing assumed |
| COLORATION/DYEING/FABRIC/AIRFLOW/ACID#SYNTHETIC_FIBERS | 27 | 80% reduction from conventional dyeing assumed |
| COLORATION/DYEING/FABRIC/AIRFLOW/DISPERSE | 20 | Including washing as provided in BAT document table 4.71 |
| COLORATION/DYEING/FABRIC/AIRFLOW/REACTIVE | 80 | Including washing as provided in BAT document table 4.71 |
| COLORATION/DYEING/FABRIC/SOFTFLOW/ACID#ANIMAL_FIBERS | 83 | [50% water saving from conventional jet dyeing](https://www.fibre2fashion.com/industry-article/7111/soft-flow-dyeing-machine) |
| COLORATION/DYEING/FABRIC/SOFTFLOW/ACID#SYNTHETIC_FIBERS | 67 | 50% water saving from conventional jet dyeing |
| COLORATION/DYEING/FABRIC/SOFTFLOW/DISPERSE | 50 | 50% water saving from conventional jet dyeing |
| COLORATION/DYEING/FABRIC/SOFTFLOW/REACTIVE | 75 | 50% water saving from conventional jet dyeing |
| COLORATION/DYEING/FABRIC/JET/ACID#ANIMAL_FIBERS | 167 | All values extrapolated based on liquor ratio |
| COLORATION/DYEING/FABRIC/JET/ACID#SYNTHETIC_FIBERS | 133 | All values extrapolated based on liquor ratio |
| COLORATION/DYEING/FABRIC/JET/DISPERSE | 100 | Including rinsing as provided in BAT document table 4.71 |
| COLORATION/DYEING/FABRIC/JET/REACTIVE | 150 | Including rinsing as provided in BAT document table 4.71 |
| COLORATION/DYEING/FABRIC/BEAM/ACID#ANIMAL_FIBERS | 109 | Scaled from "Beam - Disperse" using the Liquor ratio |
| COLORATION/DYEING/FABRIC/BEAM/ACID#SYNTHETIC_FIBERS | 98 | Scaled from "Beam - Disperse" using the Liquor ratio |
| COLORATION/DYEING/FABRIC/BEAM/DISPERSE | 87 | Average value taken from BAT document page 280 |
| COLORATION/DYEING/FABRIC/BEAM/REACTIVE | 109 | Scaled from "Beam - Disperse" using the Liquor ratio |
| COLORATION/DYEING/FABRIC/CPB/REACTIVE | 20 | Including washing and reduction clearing |
| COLORATION/DYEING/FABRIC/PAD_STEAM/ACID#ANIMAL_FIBERS | 20 | Including washing and reduction clearing |
| COLORATION/DYEING/FABRIC/PAD_STEAM/REACTIVE | 36 | Includes cold wash, hot wash and extensive washing for salt removal |
| COLORATION/DYEING/FABRIC/PAD_STEAM/VAT | 30 | Includes oxidation washing in addition to post-dye rinsing |
| COLORATION/DYEING/FABRIC/THERMOSOL/DISPERSE | 20 | Including washing and reduction clearing |
| COLORATION/DYEING/YARN/PACKAGE/ACID#ANIMAL_FIBERS | 36 | [Source](https://files01.core.ac.uk/download/pdf/143413631.pdf) |
| COLORATION/DYEING/YARN/PACKAGE/ACID#SYNTHETIC_FIBERS | 29 |  |
| COLORATION/DYEING/YARN/PACKAGE/DISPERSE | 40 |  |
| COLORATION/DYEING/YARN/PACKAGE/REACTIVE | 60 | [Source](https://d-nb.info/1337167584/34) |
| COLORATION/DYEING/YARN/PACKAGE/VAT | 60 | Extrapolation |
| COLORATION/DYEING/YARN/HANK/ACID#ANIMAL_FIBERS | 60 | Extrapolation |
| COLORATION/DYEING/YARN/HANK/ACID#SYNTHETIC_FIBERS | 48 | Extrapolation |
| COLORATION/DYEING/YARN/HANK/DISPERSE | 29 | Extrapolation |
| COLORATION/DYEING/YARN/HANK/REACTIVE | 36 | Extrapolation |
| COLORATION/DYEING/YARN/HANK/VAT | 100 | Extrapolation |
| COLORATION/DYEING/YARN/ROPE/INDIGO | 150 | [Effective Process Optimization Of Indigo Rope Dyeing: A Case Study](https://www.researchgate.net/publication/313750678_Effective_Process_Optimization_Of_Indigo_Rope_Dyeing_A_Case_Study) |
| COLORATION/DYEING/GARMENT/FRONT_LOADER/REACTIVE | 136 | [Source](http://www.ijmer.com/papers/Vol3_Issue4/DU3424342441.pdf) |
| COLORATION/DYEING/FIBER/PACKAGE/ACID#ANIMAL_FIBERS | 17.3 | [ENco mill data for wool loose fibre](http://wiki.zero-emissions.at/index.php?title=Dyeing_in_textile_industry) |
| COLORATION/DYEING/FIBER/PACKAGE/ACID#SYNTHETIC_FIBERS | 11.533 | Extrapolation |
| COLORATION/DYEING/FIBER/PACKAGE/DISPERSE | 52 | Currently assumed proportional to liquor ratio |
| COLORATION/DYEING/FIBER/PACKAGE/REACTIVE | 104 | From ecoinvent batch dyeing, fibre, cotton dataset |
| COLORATION/DYEING/FIBER/PACKAGE/VAT | 104 | From ecoinvent batch dyeing, fibre, cotton dataset |

The compiled data shows a clear gradient across fabric dyeing technologies. Conventional jet dyeing exhibits the highest water consumption (approximately 100-167 L/kg), reflecting high liquor ratios and extensive rinsing requirements. Reactive dyeing within this category is especially water intensive due to the need to remove hydrolyzed dye and large quantities of salt, while acid dyeing on animal fibers also shows high values because of deeper penetration requirements and after-treatments. Softflow machines demonstrate moderate reductions (approximately 50-83 L/kg), consistent with literature indicating roughly 50% savings compared with conventional jets through improved circulation and lower bath volumes. Airflow systems achieve the lowest water use among exhaust machines (approximately 20-80 L/kg) because fabric transport relies on air rather than liquid, significantly reducing liquor requirements; however, reactive dyeing remains comparatively high even in airflow systems due to unavoidable washing steps.

Beam dyeing values fall in the intermediate range (approximately 87-109 L/kg), as pressurized flow through wound fabric packages requires moderate liquor volumes but still involves substantial rinsing. Semi-continuous and continuous processes -- such as CPB, pad-steam, and thermosol -- show markedly lower water use (approximately 20-36 L/kg). These methods apply dye by padding with minimal liquor pickup followed by fixation via steaming or dry heat, so water consumption is largely confined to washing stages. Thermosol disperse dyeing and CPB reactive dyeing are among the most water-efficient routes because fixation occurs without immersion dye baths.

For yarn dyeing, package processes generally exhibit moderate water consumption (approximately 29-60 L/kg) because liquor is pumped through yarn packages, allowing lower ratios than loose immersion methods. Hank dyeing shows wider variability (approximately 29-100 L/kg), reflecting differences in fiber accessibility and liquor retention within loosely arranged skeins. Indigo rope dyeing stands out with very high consumption (~150 L/kg), as the process involves repeated dipping, oxidation, and washing cycles intrinsic to indigo chemistry rather than a single fixation step. Garment dyeing in front-loader machines also shows high water use (~136 L/kg) because complete garments trap liquor, require high bath volumes for mechanical movement, and undergo multiple wet processing steps.

Fibre dyeing displays some of the lowest values for acid dyes on loose wool (approximately 17 L/kg), since open fibre structure allows efficient penetration at lower liquor ratios. However, reactive and vat dyeing of fibre can reach high levels (~104 L/kg), reflecting intensive washing and chemical treatments. Across these categories, many values were extrapolated using liquor ratios or scaled from related datasets, introducing uncertainty. Nonetheless, the overall pattern remains consistent: processes involving immersion of formed textile structures (fabric, garments, rope yarn) consume substantially more water than those treating loose fibre or using controlled application methods.

Overall inventory can be found here: [Google Sheets](https://docs.google.com/spreadsheets/d/1kV3rGcBCFm6jTbT-Nz5edo18FONK1LzL/edit?usp=sharing&ouid=109658983613223573958&rtpof=true&sd=true)

#### Wastewater modeling assumptions

For wastewater estimation, it was assumed that 10% of the process water is lost through evaporation during heating and drying operations, while the remaining 90% is discharged as wastewater. At this stage, wastewater has been modeled using the generic "average wastewater" dataset from ecoinvent. This simplification was adopted because the current assessment prioritizes carbon footprint, and variations in pollutant load (e.g., COD, salinity, dye concentration) have relatively limited influence on greenhouse gas emissions compared with energy use. Therefore, using a representative average dataset provides a reasonable approximation for climate-focused analysis.

However, textile wastewater is known to vary significantly in composition depending on dye class, auxiliaries, salt use, and process conditions. For future assessments covering additional midpoint impact categories -- such as eutrophication, ecotoxicity, or water scarcity -- more detailed characterization will be necessary. This would involve developing textile-specific wastewater datasets reflecting actual pollutant loads and treatment pathways. Scenario analyses could also include advanced treatment configurations such as zero liquid discharge (ZLD), which would substantially alter environmental impacts across multiple categories.

## 4. Life Cycle Impact Assessment

Across all routes (1 kg dyeing service, pretreatment excluded), energy use dominates the carbon footprint, typically contributing 80-95% of total CO2e.

Continuous processes especially thermosol disperse (3.91 kg CO2e/kg) and pad-steam routes (~4.05-4.41) show relatively low impacts because they operate at low liquor ratios, rely on short residence times, and apply dye by padding rather than immersion.

The high energy share in these routes reflects steam generation for fixation and drying rather than bath heating. Dye contributions are generally small (approximately 1-5%) except for vat pad-steam, where higher dye loadings and auxiliary requirements increase the dye share (~12%). Overall, these contributions are reasonable because continuous dyeing minimizes water handling, pumping, and repeated heating cycles.

*(figure)*

Among exhaust processes, airflow jet technologies exhibit comparatively low impacts (approximately 2.39-3.85 kg CO2e/kg) due to reduced liquor ratios and the use of air to transport fabric, lowering both heating demand and auxiliary chemicals. Synthetic acid dyeing in airflow jets shows the lowest footprint (2.39 kg CO2e/kg), consistent with easier dye uptake on synthetic fibers and reduced washing needs. Beam dyeing and conventional jet dyeing produce substantially higher emissions (approximately 5-8 kg CO2e/kg), driven by large bath volumes, longer cycle times, and repeated heating and rinsing. Reactive dyeing on cellulosics in conventional jets is particularly carbon intensive (6.60 kg CO2e/kg) because unfixed hydrolyzed dye and salts necessitate extensive washing, increasing both energy and chemical contributions.

Softflow jets display an interesting shift: total emissions are moderate (approximately 3.81-5.77 kg CO2e/kg), but the energy share drops (approximately 50-68%) while chemical contributions rise sharply (up to ~41%). Having more primary data would help to further improve and validate softflow dyeing data.

| Dyeing Route | Total CO2e (kg/kg fabric) | Energy (%) | Dye (%) | Chemicals (%) | Others (%) |
| --- | --- | --- | --- | --- | --- |
| Continuous - Pad steam - Acid - Animal | 3.454 | 91.36 | 5.06 | 3.10 | 0.48 |
| Continuous - Pad steam - Reactive - Cellulosic | 3.549 | 91.48 | 2.40 | 5.09 | 1.03 |
| Continuous - Pad steam - Vat - Cellulosic | 3.792 | 83.21 | 13.46 | 2.33 | 1.00 |
| Continuous - Thermosol - Disperse - Synthetic | 3.262 | 94.70 | 1.84 | 3.21 | 0.87 |
| Exhaust - Airflow jet - Acid - Animal | 3.383 | 83.97 | 8.93 | 6.89 | 0.82 |
| Exhaust - Airflow jet - Acid - Synthetic | 2.112 | 78.64 | 11.29 | 8.33 | 1.74 |
| Exhaust - Airflow jet - Disperse - Synthetic | 2.451 | 88.11 | 5.65 | 5.10 | 1.03 |
| Exhaust - Airflow jet - Reactive - Cellulosic | 2.603 | 81.18 | 5.45 | 11.90 | 1.46 |
| Exhaust - Beam - Acid - Animal | 5.286 | 82.33 | 3.76 | 12.87 | 1.04 |
| Exhaust - Beam - Acid - Synthetic | 3.383 | 75.73 | 5.40 | 16.77 | 2.10 |
| Exhaust - Beam - Disperse - Synthetic | 4.340 | 83.66 | 2.77 | 12.55 | 1.02 |
| Exhaust - Beam - Reactive - Cellulosic | 4.328 | 79.72 | 3.28 | 15.71 | 1.29 |
| Exhaust - Conventional jet - Acid - Animal | 7.045 | 71.15 | 8.46 | 18.39 | 2.00 |
| Exhaust - Conventional jet - Acid - Synthetic | 4.483 | 63.77 | 10.63 | 22.38 | 3.22 |
| Exhaust - Conventional jet - Disperse - Synthetic | 4.988 | 77.33 | 5.43 | 15.54 | 1.70 |
| Exhaust - Conventional jet - Reactive - Cellulosic | 5.767 | 65.26 | 4.92 | 27.63 | 2.19 |
| Exhaust - Softflow jet - Acid - Animal | 4.908 | 57.32 | 6.15 | 34.42 | 2.11 |
| Exhaust - Softflow jet - Acid - Synthetic | 3.311 | 49.46 | 7.20 | 40.08 | 3.26 |
| Exhaust - Softflow jet - Disperse - Synthetic | 3.648 | 66.68 | 3.79 | 27.97 | 1.56 |
| Exhaust - Softflow jet - Reactive - Cellulosic | 4.178 | 56.20 | 3.40 | 38.87 | 1.53 |
| Semi-continuous - CPB - Reactive - Cellulosic | 2.940 | 87.91 | 2.90 | 7.90 | 1.29 |

### Comparison with EF 3.1 datasets

EF 3.1 datasets have the following results for carbon footprint.

| **EF 3.1 Dataset** | **Impact (kg CO2e / kg fabric)** |
| --- | --- |
| Dyeing, batch (incl. piece, jet, jig, kier [fiber], paddle, pad-batch, yarn), direct, sulfur, vat or reactive dyes {GLO} | 2.393 |
| Dyeing, batch (incl. piece, jet, jig, kier, yarn), acid dyes {GLO} | 5.155 |
| Dyeing, batch (incl. piece, jet, jig, kier, yarn), disperse or cationic dyes {GLO} | 2.113 |
| Dyeing, batch, warp-beam {GLO} | 0.759 |
| Dyeing, continuous, acid dyes {GLO} | 1.532 |
| Dyeing, continuous, direct, sulfur, vat or reactive dyes {GLO} | 1.552 |
| Dyeing, continuous, disperse or cationic dyes {GLO} | 1.248 |
| Dyeing, solution (dope) {GLO} | 2.247 |
| Dyeing, waterless {GLO} | 0.567 |

| Dyeing route | Our result (kg CO2e/kg) | EF 3.1 value | EF 3.1 dataset (exact name) | % difference |
| --- | --- | --- | --- | --- |
| Continuous - Pad steam - Acid - Animal | 3.454 | 1.532 | Dyeing, continuous, acid dyes {GLO} | 56% |
| Continuous - Pad steam - Reactive - Cellulosic | 3.549 | 1.552 | Dyeing, continuous, direct, sulfur, vat or reactive dyes {GLO} | 56% |
| Continuous - Pad steam - Vat - Cellulosic | 3.792 | 1.552 | Dyeing, continuous, direct, sulfur, vat or reactive dyes {GLO} | 59% |
| Continuous - Thermosol - Disperse - Synthetic | 3.262 | 1.248 | Dyeing, continuous, disperse or cationic dyes {GLO} | 62% |
| Exhaust - Airflow jet - Acid - Animal | 3.383 | 5.155 | Dyeing, batch, acid dyes {GLO} | -52% |
| Exhaust - Airflow jet - Acid - Synthetic | 2.112 | 5.155 | Dyeing, batch, acid dyes {GLO} | -144% |
| Exhaust - Airflow jet - Disperse - Synthetic | 2.451 | 2.113 | Dyeing, batch, disperse or cationic dyes {GLO} | 14% |
| Exhaust - Airflow jet - Reactive - Cellulosic | 2.603 | 2.393 | Dyeing, batch, direct, sulfur, vat or reactive dyes {GLO} | 8% |
| Exhaust - Beam - Acid - Animal | 5.286 | 0.759 | Dyeing, batch, warp-beam {GLO} | 86% |
| Exhaust - Beam - Acid - Synthetic | 3.383 | 0.759 | Dyeing, batch, warp-beam {GLO} | 78% |
| Exhaust - Beam - Disperse - Synthetic | 4.340 | 0.759 | Dyeing, batch, warp-beam {GLO} | 83% |
| Exhaust - Beam - Reactive - Cellulosic | 4.328 | 0.759 | Dyeing, batch, warp-beam {GLO} | 82% |
| Exhaust - Conventional jet - Acid - Animal | 7.045 | 5.155 | Dyeing, batch, acid dyes {GLO} | 27% |
| Exhaust - Conventional jet - Acid - Synthetic | 4.483 | 5.155 | Dyeing, batch, acid dyes {GLO} | -15% |
| Exhaust - Conventional jet - Disperse - Synthetic | 4.988 | 2.113 | Dyeing, batch, disperse or cationic dyes {GLO} | 58% |
| Exhaust - Conventional jet - Reactive - Cellulosic | 5.767 | 2.393 | Dyeing, batch, direct, sulfur, vat or reactive dyes {GLO} | 59% |
| Exhaust - Softflow jet - Acid - Animal | 4.908 | 5.155 | Dyeing, batch, acid dyes {GLO} | -5% |
| Exhaust - Softflow jet - Acid - Synthetic | 3.311 | 5.155 | Dyeing, batch, acid dyes {GLO} | -56% |
| Exhaust - Softflow jet - Disperse - Synthetic | 3.648 | 2.113 | Dyeing, batch, disperse or cationic dyes {GLO} | 42% |
| Exhaust - Softflow jet - Reactive - Cellulosic | 4.178 | 2.393 | Dyeing, batch, direct, sulfur, vat or reactive dyes {GLO} | 43% |
| Semi-continuous - CPB - Reactive - Cellulosic | 2.940 | 1.552 | Dyeing, continuous, direct, sulfur, vat or reactive dyes {GLO} | 47% |

The comparison highlights a fundamental limitation of the EF 3.1 datasets: **they do not provide sufficient technological granularity to distinguish between the wide range of dyeing routes assessed in this study.**

The EF datasets aggregate multiple machine types and operating conditions into broad categories such as "batch" or "continuous," without differentiating between specific technologies (e.g., airflow jet vs. conventional jet vs. softflow jet, pad-steam vs. thermosol vs. CPB).

As a result, important drivers of environmental performance particularly liquor ratio are averaged out. This explains why technologies known to have substantially different water and energy requirements show similar EF values, whereas the present analysis captures significant variation across routes.

Furthermore, based on the primary operational data compiled for water use, energy demand, and chemical inputs, the results obtained here align more closely with Carbonfact model than with EF production-mix values.

The EF documentation notes that energy figures were derived from secondary sources (e.g., thinkstep databases) and assumes a standardized shade depth of 1.28% with uniform chemical consumption across technologies. In practice, however, chemical dosing, auxiliary use, and washing requirements vary significantly by dye class, fiber type, and machine design. By incorporating technology-specific parameters and primary data where available, the present model captures these differences, leading to results that diverge from EF averages but are consistent with real industrial variability.

### Comparison with Roos et al.

As seen below, the total carbon footprint contribution from energy usage is around 80% on average. This is in line with the contribution % of Carbonfact dyeing datasets.

| **Roos et al.** | Carbon footprint (kg COeq) | MiFuFa electricity mix (kWh) | Carbon footprint from electricity (% contribution) | Heat, light fuel oil, at boiler 10kW (MJ) | Carbon footprint from thermal energy used (% contribution) | Total energy contribution % |
| --- | --- | --- | --- | --- | --- | --- |
| Pad-steam denim dyeing, average (mix) | 1.97 | 0.7 | 40.69% | 30 | 29.87% | 70.56% |
| Dyeing PES tricot black in jet dyeing machine, average (mix) | 1.32 | 0.7 | 52.75% | 30 | 38.73% | 91.47% |
| Dyeing PA6 weave black in beam dyeing machine, average (mix) | 1.76 | 0.7 | 45.59% | 30 | 33.47% | 79.07% |
| Dyeing PES weave orange in beam dyeing machine, average (mix) | 1.58 | 0.7 | 50.65% | 30 | 37.18% | 87.83% |
| Dyeing CO/EL tricot green in jet dyeing machine, average (mix) | 1.57 | 0.7 | 51.02% | 30 | 37.46% | 88.47% |
| Dyeing cotton/PES weave, average (mix) | 1.89 | 0.7 | 42.49% | 30 | 31.20% | 73.69% |

### Comparison table

Roos et al has same electricity and heat energy assumed across dyeing technologies as mentioned above amounting to 0.8 kWh of electricity and 30 MJ of thermal energy = Total: 32.88 MJ

| **Route** | **Roos et al. CF (kg CO2e/kg)** | **Carbonfact CF (kg CO2e/kg)** | **Electricity (kWh) -- Carbonfact** | **Heat (MJ) -- Carbonfact** | **Total energy utilized (MJ)** | **Energy contribution -- Roos** | **Energy contribution -- Carbonfact** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Pad-steam denim dyeing (avg mix) | 1.97 | 4.133 | 2.3 | 17.8 | 26.08 | 70.56% | 92% |
| Jet dyeing -- PES tricot black | 1.52 | 5.842 | 2.1 | 25.8 | 33.36 | 91.47% | 81% |
| Beam dyeing -- PA6 weave black | 1.76 | 5.317 | 1.2 | 30 | 34.32 | 79.07% | 87% |
| Beam dyeing -- PES weave orange | 1.58 | 5.317 | 1.2 | 30 | 34.32 | 87.83% | 87% |
| Jet dyeing -- CO/EL tricot green | 1.57 | 6.6 | 2.1 | 24.8 | 32.36 | 88.47% | 69.13% |
| Cotton/PES weave (avg mix) | 1.89 | 5.959 | 1.65 | 27.4 | 33.34 | 73.69% | 78% |

It can be observed that the total energy demand assumed by Roos et al. and the Carbonfact model is broadly comparable, particularly when thermal energy is expressed in MJ and electricity is converted to equivalent energy units. This indicates that both models are representing similar underlying process physics namely the heating of dye baths, fixation, and drying operations that dominate textile dyeing.

The percentage contribution of energy to total carbon footprint is also of a similar magnitude (generally 70-90% in both cases), reinforcing the conclusion that energy is the primary driver of emissions irrespective of the modeling framework. Therefore, the divergence in absolute carbon footprint values is not due to fundamentally different process energy assumptions, but rather to how that energy is supplied and characterized in each model.

The major difference arises from the energy carrier mix and emission factors associated with those carriers, as well as the allocation between electricity and thermal energy. In the Carbonfact model, electricity is represented by *market for electricity, low voltage -- global*, while thermal energy is modeled using *market for heat, from steam, in chemical industry*, which reflects an industrial steam mix produced from natural gas, fuel oil, and hard coal.

This represents a relatively carbon-intensive and generalized global industrial scenario. In contrast, Roos et al. models heat as coming from a specific non-modulating 10 kW boiler using light fuel oil, and electricity from a tailored mix representative of textile-producing countries (China, Bangladesh, and Turkey). These choices significantly influence the resulting emission factors even when the underlying energy quantities are similar.

Consequently, the primary driver of differences between the Carbonfact, Roos et al., and EF 3.1 models is the combination of energy source type, regional electricity mix, and provider datasets, rather than process energy demand itself. EF 3.1 datasets likewise rely on production-mix assumptions derived from secondary databases (e.g., thinkstep/GaBi), which embed their own regional and technological averages.

Because textile dyeing emissions scale almost linearly with the carbon intensity of heat and electricity, variations in fuel type (fuel oil vs. mixed fossil steam), boiler efficiency assumptions, and grid carbon intensity can easily produce two- to four-fold differences in total footprint while representing essentially the same physical process. This highlights the importance of using region- and technology-specific energy datasets when conducting decision-grade assessments or decarbonisation studies for textile wet processing.

### Sensitivity analysis

A sensitivity analysis was conducted to evaluate how variations in energy sources influence the total carbon footprint of reactive exhaust dyeing using a conventional jet dyeing machine, which showed the highest carbon impact among the dyeing technologies assessed.

The analysis focused on two key energy inputs in the life cycle inventory (LCI): electricity and thermal energy (steam/heat supply). The approach followed a one-parameter-at-a-time sensitivity method, where all other process parameters (chemicals, water, auxiliaries, and process conditions) were kept constant while only the energy source dataset was changed.

In the first step, thermal energy supply was kept constant while different electricity grid mixes and renewable electricity sources were substituted to assess their influence on the total carbon footprint.

In the second step, electricity was kept constant (baseline electricity mix) while different thermal energy sources and heat production technologies were tested.

The resulting total carbon footprint values were compared against the baseline scenario, and the sensitivity was expressed as both absolute difference (kg CO2e) and percentage change relative to the baseline.

#### Electricity sources

Sensitivity analysis of electricity sources shows that the total carbon footprint of the dyeing process varies between **5.33 and 7.22 kg CO2e per kg of dyed fabric**, corresponding to a **-19% to +9% variation relative to the global electricity mix baseline**. Low-carbon electricity sources such as solar PV and wind reduce the footprint by **17-19%**, while carbon-intensive grids increase emissions by up to **9%**.

| **Electricity source** | **Carbon footprint (kg CO2eq per kWh)** | **CF due to electricity (kg CO2 per kg fabric)** | **Total CF for dyeing (kg CO2eq)** | **Difference vs Baseline** | **Sensitivity %** |
| --- | --- | --- | --- | --- | --- |
| Electricity, low voltage {GLO} market group | 0.687 | 1.444 | 6.601 | 0.00 | 0.00% |
| Electricity, low voltage {BD} market | 0.984 | 2.066 | 7.223 | 0.62 | 9.43% |
| **Electricity, low voltage {FR} photovoltaic** | **0.083** | **0.174** | **5.331** | **-1.27** | **-19.24%** |
| Electricity, low voltage {CN} market group | 0.854 | 1.794 | 6.951 | 0.35 | 5.31% |
| **Electricity, low voltage {FR} market** | **0.088** | **0.185** | **5.342** | **-1.26** | **-19.07%** |
| **Electricity, low voltage {Europe without CH} market group** | **0.336** | **0.705** | **5.862** | **-0.74** | **-11.19%** |
| **Electricity, low voltage {RER} market group** | **0.331** | **0.694** | **5.851** | **-0.75** | **-11.35%** |
| Electricity, low voltage {RAF} market group | 0.849 | 1.782 | 6.939 | 0.34 | 5.13% |
| Electricity, low voltage {RAS} market group | 0.877 | 1.841 | 6.998 | 0.40 | 6.02% |
| **Electricity, low voltage {RLA} market group** | **0.350** | **0.736** | **5.893** | **-0.71** | **-10.72%** |
| Electricity, low voltage {RME} market group | 0.907 | 1.906 | 7.063 | 0.46 | 7.00% |
| **Electricity, low voltage {RNA} market group** | **0.454** | **0.954** | **6.111** | **-0.49** | **-7.42%** |
| **Electricity, low voltage {DE} wind, 6kW turbine** | **0.159** | **0.334** | **5.491** | **-1.11** | **-16.81%** |

*(figure)*

#### Thermal energy sources

| Thermal source | Carbon footprint (kg CO2eq per MJ) | CF due to heat supply (kg CO2 per kg fabric) | Total CF for dyeing (kg CO2eq) | Difference vs Baseline | Sensitivity % |
| --- | --- | --- | --- | --- | --- |
| Heat, from steam {RoW} | 0.126 | 3.119 | 6.601 | 0.00 | 0.00% |
| **Heat, from steam {RER}** | **0.111** | **2.743** | **6.225** | **-0.38** | **-5.70%** |
| **Heat, district or industrial, natural gas {GLO}** | **0.044** | **1.080** | **4.562** | **-2.04** | **-30.89%** |
| **Heat, district or industrial, natural gas {RoW}** | **0.039** | **0.963** | **4.444** | **-2.16** | **-32.67%** |
| **Heat, district or industrial, natural gas {RER}** | **0.055** | **1.365** | **4.847** | **-1.75** | **-26.57%** |
| **Heat, district or industrial, natural gas {Europe without CH}** | **0.055** | **1.366** | **4.847** | **-1.75** | **-26.56%** |
| **Heat, central or small-scale, natural gas {GLO}** | **0.080** | **1.986** | **5.468** | **-1.13** | **-17.17%** |
| **Heat, central or small-scale, natural gas {RER}** | **0.076** | **1.888** | **5.369** | **-1.23** | **-18.66%** |
| **Heat, central or small-scale, natural gas {RoW}** | **0.080** | **1.986** | **5.468** | **-1.13** | **-17.17%** |
| **Heat, district or industrial, other than natural gas {GLO}** | **0.105** | **2.607** | **6.088** | **-0.51** | **-7.77%** |
| Heat production, coal tar, at industrial furnace 1MW {GLO} | 0.135 | 3.344 | 6.826 | 0.22 | 3.41% |
| Heat production, at coal coke industrial furnace 1-10MW {RoW} | 0.160 | 3.972 | 7.453 | 0.85 | 12.91% |
| Heat production, at coal coke industrial furnace 1-10MW {CA-QC} | 0.155 | 3.850 | 7.331 | 0.73 | 11.07% |
| **Heat production, natural gas, at boiler condensing modulating >100kW {RoW}** | **0.071** | **1.751** | **5.232** | **-1.37** | **-20.73%** |
| **Heat production, natural gas, at boiler modulating >100kW {RoW}** | **0.075** | **1.860** | **5.342** | **-1.26** | **-19.07%** |
| **Heat production, natural gas, at industrial furnace >100kW {RoW}** | **0.076** | **1.877** | **5.358** | **-1.24** | **-18.82%** |
| **Heat production, natural gas, at industrial furnace low-NOx >100kW {RoW}** | **0.082** | **2.044** | **5.526** | **-1.08** | **-16.29%** |
| **Heat production, natural gas, at industrial furnace low-NOx >100kW {Europe without CH}** | **0.081** | **2.002** | **5.484** | **-1.12** | **-16.93%** |
| **Heat production, natural gas, at industrial furnace >100kW {Europe without CH}** | **0.075** | **1.870** | **5.351** | **-1.25** | **-18.93%** |
| **Heat production, natural gas, at boiler modulating >100kW {Europe without CH}** | **0.075** | **1.853** | **5.335** | **-1.27** | **-19.18%** |
| **Heat production, natural gas, at boiler condensing modulating >100kW {Europe without CH}** | **0.070** | **1.744** | **5.226** | **-1.38** | **-20.83%** |
| **Heat and power co-generation, wood chips, 2000 kW {RoW}** | **0.004** | **0.087** | **3.569** | **-3.03** | **-45.94%** |
| **Heat and power co-generation, wood chips, 6667 kW {RoW}** | **0.003** | **0.071** | **3.553** | **-3.05** | **-46.18%** |
| **Heat production, light fuel oil, at boiler 10kW {CH}** | **0.102** | **2.539** | **6.020** | **-0.58** | **-8.79%** |

*(figure)*

The sensitivity analysis shows that **thermal energy supply has a strong influence on the total carbon footprint of dyeing**.

The baseline scenario, using **steam supply from the chemical industry (RoW)**, resulted in a total carbon footprint of **6.60 kg CO2e per kg of dyed fabric**.

Substituting the heat source with **natural gas-based heat production** significantly reduced emissions, with total impacts ranging between **4.44 and 5.47 kg CO2e/kg fabric**, corresponding to reductions of approximately **17-33% compared to the baseline** depending on the technology and region.

In contrast, **coal- and coke-based heat production systems increased emissions**, resulting in total carbon footprints of up to **7.45 kg CO2e/kg fabric**, representing a **13% increase relative to the baseline**.

The largest emission reductions were observed for **biomass-based heat and power co-generation systems (wood chips)**, which reduced the total carbon footprint to approximately **3.55-3.57 kg CO2e/kg fabric**, corresponding to a **~46% reduction relative to the baseline scenario**.

Overall, the analysis indicates that the **choice of thermal energy source can alter the total carbon footprint of dyeing by nearly +/-45%**, highlighting its strong influence on environmental performance.

#### Conclusion

The sensitivity analysis clearly demonstrates that **energy sources particularly thermal energy are critical drivers of the carbon footprint of textile dyeing technologies**. While variations in electricity sources also influence the results, the magnitude of change is generally smaller compared to thermal energy.

### Summary of carbon footprint by dye production route (per kg dye)

| Dye type & production route | Total GHG impact (kg CO2e/kg dye) | Dominant contributors | Key driver of emissions |
| --- | --- | --- | --- |
| Anthraquinone vat dyes -- alkali fusion | **7.214** | Glycine (64%), steam (22%) | N-phenylglycine dominates vat dye LCI because it is a high-mass, fossil-derived aromatic precursor |
| Azo acid dyes -- bromisation | **8.271** | 2-Nitroaniline (52%), bromine (19%), steam (15%) | Nitro-aromatic intermediate made via energy-intensive nitration and reduction of benzene derivatives |
| Azo disperse dyes -- diazotization-coupling | **6.525** | 2-Nitroaniline (41%), steam (30%) | Azo disperse and azo reactive dyes typically require high-temperature steps that consume large amounts of steam/heat, especially for powder products. |
| Azo reactive dyes -- monochlorotriazine | **6.369** | Steam (42%), multiple intermediates (each ~7-14%) |  |

Across the dye classes assessed, carbon footprints range from about 6.4 to 8.3 kg CO2e per kg dye, with azo acid dyes produced via bromisation showing the highest impact and azo reactive dyes the lowest among the four routes considered.

A consistent pattern emerges in which upstream production of aromatic intermediates and thermal energy consumption dominate emissions, while water, wastewater, and minor auxiliaries contribute negligibly.

Anthraquinone vat dyes are driven primarily by N-phenylglycine production, reflecting the high mass and fossil origin of this precursor, whereas azo acid dyes are strongly influenced by 2-nitroaniline and bromine manufacture, both of which involve energy-intensive nitration or halogenation chemistry.

Disperse dyes show a more balanced split between intermediates and steam demand due to high-temperature processing steps, while reactive dyes are uniquely dominated by steam consumption associated with introducing reactive groups (e.g., cyanuric chloride chemistry) and multi-step synthesis.

Overall, the comparison indicates that dye manufacturing impacts are governed less by utilities such as water and electricity and more by the carbon intensity of key chemical precursors and process heat requirements, with differences between dye classes reflecting the complexity and energy intensity of their respective synthesis pathways.

Source: Li X, Zhu L, Ding X, Wu X, Wang L. Climate Change and the Textile Industry: The Carbon Footprint of Dyes. *AATCC Journal of Research*. 2023;11(2):109-123. doi:[10.1177/24723444231212954](https://doi.org/10.1177/24723444231212954)

## 5. Gaps with current EFS data and limitations

```yaml
- COLORATION/DYEING
- COLORATION/DYEING/ACID
- COLORATION/DYEING/ACID/BATCH
- COLORATION/DYEING/ACID/CONTINUOUS
- COLORATION/DYEING/BIOLOGICAL
- COLORATION/DYEING/DISPERSE_CATIONIC
- COLORATION/DYEING/DISPERSE_CATIONIC/BATCH
- COLORATION/DYEING/DISPERSE_CATIONIC/CONTINUOUS
- COLORATION/DYEING/DOPE
- COLORATION/DYEING/ECRU_EFD
- COLORATION/DYEING/EVERDYE
- COLORATION/DYEING/EXHAUST
- COLORATION/DYEING/EXHAUST/DARK_SHADE
- COLORATION/DYEING/EXHAUST/LIGHT_SHADE
- COLORATION/DYEING/EXHAUST/MEDIUM_SHADE
- COLORATION/DYEING/NATURAL_FIBERS
- COLORATION/DYEING/POLYAMIDE
- COLORATION/DYEING/RANGE
- COLORATION/DYEING/RANGE/DARK_SHADE
- COLORATION/DYEING/RANGE/LIGHT_SHADE
- COLORATION/DYEING/RANGE/MEDIUM_SHADE
- COLORATION/DYEING/SPACE
- COLORATION/DYEING/SYNTHETIC_FIBERS
- COLORATION/DYEING/TOP
- COLORATION/DYEING/VAT_REACTIVE
- COLORATION/DYEING/VAT_REACTIVE/BATCH
- COLORATION/DYEING/VAT_REACTIVE/CONTINUOUS
- COLORATION/DYEING/VEGETABLE
- COLORATION/DYEING/WATERLESS/SUPERCRITICAL_CO2
- COLORATION/DYEING/WOOL_AND_SILK
```

### 5.2 Proposition for a new disaggregated process structure

We propose building process inventories with disaggregated energy consumption information within the json structure: this will further allow:

- Energy regionalisation at scale, multiplying quantities under each dataset with country-specific emission factors
- Energy specification at supplier level: seamlessly multiplying supplier specific EFs with the reported quantity per dataset
- Querying the energy quantities and ranges per type of process, further enabling granular decarbonisation modeling and monitoring of energy efficiency.

```json
"COMPONENT_PROCESS_STEP:COLORATION/DYEING/DISPERSE_CATIONIC/BATCH#ANY@WORLD":
{Impacts},
  "energyShare": {
    "electricity": 0.097,
    "heat": 0.852
  "energyConsumption": {
    "total energy demand - MJ": 33.4
    "electricity - kWh": 2.1,
    "heat - MJ": 14.8
  },
```

## 6. Dataset hierarchy and construction

Dataset descriptors have been built based on 7 levels, representing key process parameters.

| **Parameter type** | **Parameter example** | **Level** |
| --- | --- | --- |
| Process category 1 | COLORATION | 1 |
| Process category 2 | DYEING | 2 |
| Fiber group | SYNTHETIC_FIBERS | 3 |
| Dye type | DISPERSE | 4 |
| Substrate type | FABRIC | 5 |
| Process type | BATCH | 6 |
| Process technology | AIRFLOW_JET | 7 |

Example of a full level 7 descriptor: COLORATION/DYEING/SYNTHETIC_FIBERS/DISPERSE/FABRIC/BATCH/AIRFLOW_JET

All level 7 datasets have been calculated using a custom Life Cycle Inventory and computed with Brightway. All inferior levels have been calculated either using a range or a fallback in the case where the n+1 level node is unique (meaning a range cannot be computed). The logic to build the different datasets for descriptors is presented in the tree diagram below.

*(figure)*
