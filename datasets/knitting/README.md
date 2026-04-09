# Knitting

> Lifecycle assessment datasets for knitted fabric production across flat, circular, seamless, hosiery, and 3D knitting technologies.

**13 datasets** | Functional unit: 1 kg fabric | All 16 EF 3.1 impact indicators

## Overview

This process category covers knitting — the interlocking of yarn loops to form fabric. The system boundary includes direct electricity (knitting machines), indirect energy (HVAC, compressors, lighting), lubricants, yarn losses, textile waste, and capital goods (machine amortisation). Circular knitting datasets are parameterised by yarn fineness (dtex), while other technologies use average-case inventories.

## Datasets

| Activity | GHG (kgCO2eq/kg) |
|----------|------------------:|
| 3D Knitting, Average | 6.59 |
| Circular Knitting, 120 dtex | 3.33 |
| Circular Knitting, 150 dtex | 3.29 |
| Circular Knitting, 170 dtex | 3.26 |
| Circular Knitting, 200 dtex | 3.24 |
| Circular Knitting, 300 dtex | 3.20 |
| Circular Knitting, 330 dtex | 3.19 |
| Circular Knitting, 370 dtex | 3.19 |
| Circular Knitting, 45 dtex | 3.69 |
| Circular Knitting, 70 dtex | 3.48 |
| Flat Knitting, Average | 3.97 |
| Hosiery Knitting, Average | 3.96 |
| Seamless Knitting, Average | 4.14 |

> Full results across all 16 EF 3.1 impact indicators: [impact-scores.csv](impact-scores.csv)

## GHG Contribution Analysis

Representative charts showing top GHG contributors. All charts available in the [charts/](charts/) folder.

### 3D Knitting Average
![3D Knitting Average](charts/ghg-3d-knitting-average.png)

### Circular Knitting 170 Dtex
![Circular Knitting 170 Dtex](charts/ghg-circular-knitting-170-dtex.png)

### Flat Knitting Average
![Flat Knitting Average](charts/ghg-flat-knitting-average.png)

### Hosiery Knitting Average
![Hosiery Knitting Average](charts/ghg-hosiery-knitting-average.png)

### Seamless Knitting Average
![Seamless Knitting Average](charts/ghg-seamless-knitting-average.png)

> All 13 contribution charts: [charts/](charts/)

## Methodology

The datasets model electricity consumption (direct and indirect), lubricating oil, yarn losses, textile waste, and machine infrastructure amortisation. Background data comes from ecoinvent 3.12 (Cut-Off system model) and impact assessment uses the EF 3.1 characterisation method.

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [impact-scores.csv](impact-scores.csv) | LCIA results for 16 EF 3.1 indicators + DQR scores |
| [ghg-contributions.csv](ghg-contributions.csv) | Per-exchange GHG contribution analysis |
| [process-steps.json](process-steps.json) | Machine-readable emission factor format |
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible inventory |
