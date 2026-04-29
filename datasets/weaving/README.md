# Weaving

> Lifecycle assessment datasets for woven fabric production across multiple loom technologies and yarn finenesses.

**19 datasets** | Functional unit: 1 kg fabric | Methodology covers all 16 EF 3.1 impact indicators

## Overview

This process category covers weaving — the interlacing of warp and weft yarns to form fabric. The system boundary includes warping, sizing, drawing-in, and loom operation. Datasets span air-jet looms at 9 yarn finenesses (45–370 dtex) plus rapier, shuttle, water-jet, jacquard, silk, carpet, and backing fabric variants.

## Datasets

**Input required (kg)** is the kg of input yarn required per 1 kg of finished woven fabric, accounting for loom-specific yarn losses. Callers scale the upstream yarn input by this factor and add a yarn-waste flow for the lost fraction — see the repo-level [Handling material losses](../../README.md#handling-material-losses) note. See [methodology](methodology/) §3.2.3 for derivation.

| Activity | Input required (kg) |
|----------|------------------:|
| Fabric production, nonwoven, cellulosic, wetlaid spunlace | — |
| Fabric production, nonwoven, polypropylene, meltblown | — |
| Fabric sizing, natural fibers | — |
| weaving of carpet production, at plant Carpet, Weaved | 1.136363636 |
| weaving of primary backing service, Backing fabric, weaved production mix, at plant service, Backing fabric, weaved | 1.136363636 |
| weaving, 120 dtex-108 denier-49/1 ne-83 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 150 dtex-135 denier-40/1 ne-67 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 170 dtex-153 denier-34/1 ne-59 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 200 dtex-180 denier-30/1 ne-50 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 300 dtex-270 denier-20/1 ne-33 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 330 dtex-297 denier-18/1 ne-30 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 370 dtex-333 denier-16/1 ne-27 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 45 dtex-41 denier- 130/1 ne-222 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, 70 dtex-63 denier-84/1 ne-143 nm service, Fabric, Weaved production, at plant service, Fabric, Weaved | 1.063829787 |
| weaving, generic water-jet service, Fabric,Weaved water-jet loom production mix, at plant service, Fabric,Weaved water-jet loom | 1.041666667 |
| weaving, jacquard service, Fabric, Weaved by jacquard loom production mix, at plant service, Fabric, Weaved by jacquard loom | 1.098901099 |
| weaving, rapier service, Fabric, Weaved by rapier loom production mix, at plant service, Fabric, Weaved by rapier loom | 1.075268817 |
| weaving, shuttle service, Fabric, Weaved by shuttle loom production mix, at plant service, Fabric, Weaved by shuttle loom | 1.136363636 |
| weaving, silk service, Fabric, Silk production mix, at plant service, Fabric, Silk | 1.063829787 |

## Methodology

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible foreground inventory |
