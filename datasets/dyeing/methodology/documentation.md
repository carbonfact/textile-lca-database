# Documentation

> Part of [Dyeing Methodology](README.md)

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
