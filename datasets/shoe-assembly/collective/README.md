# Collective Shoe Assembly

> Lifecycle assessment datasets for women's boots assembly (PU/Microfiber Upper + TPR/EVA/Rubber Outsole), covering cutting, stitching, and lasting operations across 3 electricity scenarios.

**3 datasets** | Functional unit: 1 kg assembled footwear | All 16 EF 3.1 impact indicators

## Overview

This process category covers collective shoe assembly — the process-level operations involved in assembling women's boots with PU/microfiber upper and TPR/EVA/rubber outsole. The system boundary includes cutting (with oil paint printing), stitching (with glue application), and lasting (adhesive, primer, cleaner). Three electricity scenarios are provided: China (CN, primary data origin), Global average (GLO), and Italy (IT).

The database was developed based on primary data from a shoe manufacturer in Wenzhou, China, using a modular approach by process and chemical families. Chemical sub-processes (stitching glue, primer, surface cleaner, oil paint) were modeled from MSDS/SDS documents.

Lasting dominates the GHG impact across all scenarios (82–86%), driven by PU adhesive, primer chemicals, and electricity consumption. The aggregated material loss rate (input/output ratio) is 1.049, reflecting cumulative wastage across cutting (IOR=1.0382), stitching (IOR=1.006), and lasting (IOR=1.004).

## Datasets

| Activity | GHG (kgCO2eq/kg) | Input required (kg) |
|----------|------------------:|--------------------:|
| Collective Shoe Assembly, Global average electricity | 1.20 | 1.049 |
| Collective Shoe Assembly, China electricity | 1.43 | 1.049 |
| Collective Shoe Assembly, Italy electricity | 0.86 | 1.049 |

> Full results across all 16 EF 3.1 impact indicators: [impact-scores.csv](impact-scores.csv)

## Methodology

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [impact-scores.csv](impact-scores.csv) | Emission factors (LCIA results) for 16 EF 3.1 indicators + DQR scores |
| [ghg-contributions.csv](ghg-contributions.csv) | Per-exchange GHG contribution analysis |
| [process-steps.json](process-steps.json) | Machine-readable emission factor format |
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible inventory |
