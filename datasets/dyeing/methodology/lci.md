# Life Cycle Inventory

> Part of [Dyeing Methodology](README.md)

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
