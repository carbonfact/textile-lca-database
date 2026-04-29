# Knitting

> Lifecycle assessment datasets for knitted fabric production across flat, circular, seamless, hosiery, and 3D knitting technologies.

**13 datasets** | Functional unit: 1 kg fabric | Methodology covers all 16 EF 3.1 impact indicators

## Overview

This process category covers knitting — the interlocking of yarn loops to form fabric. The system boundary includes direct electricity (knitting machines), indirect energy (HVAC, compressors, lighting), lubricants, yarn losses, textile waste, and capital goods (machine amortisation). Circular knitting datasets are parameterised by yarn fineness (dtex), while other technologies use average-case inventories.

## Datasets

**Input required (kg)** is the kg of input yarn required per 1 kg of finished knitted fabric, accounting for technology- and fineness-specific yarn losses. Callers scale the upstream yarn input by this factor and add a yarn-waste flow for the lost fraction — see the repo-level [Handling material losses](../../README.md#handling-material-losses) note. See [methodology](methodology/) for per-technology derivation.

| Activity | Input required (kg) |
|----------|------------------:|
| 3D Knitting, Average | 1.020408163 |
| Circular Knitting, 120 dtex | 1.041666667 |
| Circular Knitting, 150 dtex | 1.041666667 |
| Circular Knitting, 170 dtex | 1.041666667 |
| Circular Knitting, 200 dtex | 1.030927835 |
| Circular Knitting, 300 dtex | 1.030927835 |
| Circular Knitting, 330 dtex | 1.030927835 |
| Circular Knitting, 370 dtex | 1.030927835 |
| Circular Knitting, 45 dtex | 1.052631579 |
| Circular Knitting, 70 dtex | 1.052631579 |
| Flat Knitting, Average | 1.030927835 |
| Hosiery Knitting, Average | 1.020408163 |
| Seamless Knitting, Average | 1.025641026 |

## Methodology

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible foreground inventory |
