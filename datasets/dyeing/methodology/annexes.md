# Annexes

> Part of [Dyeing Methodology](README.md)

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
