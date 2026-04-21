# Use Phase (Laundry)

> Lifecycle assessment datasets for the garment use phase — dry cleaning, hand washing, machine washing, tumble drying, ironing, and detergents.

**15 datasets** | Functional units: 1 kg textile (wash/dry/clean), 1 min (ironing), 1 kg detergent | All 16 EF 3.1 impact indicators

## Overview

This process category covers the laundry use phase of textile products. The system boundary includes electricity to heat water and run machines, tap water, detergent, and wastewater treatment. Two detergent formulations (liquid and powder) are also provided as separate foreground datasets so their contribution can be inspected and swapped.

Parameter values are representative of European consumer behaviour. Electricity is modelled with the ecoinvent "Europe without Switzerland" low-voltage market group; detergent dosage follows Kruschwitz et al. (2014) for medium-soiled laundry; washing machine electricity and water intake follow Laitala et al. (2020); dry cleaning assumes perchloroethylene (PERC) per Keoleian et al. (1997), Laitala, Klepp & Henry (2018), and Troynikov et al. (2016).

## Credits

Datasets prepared by **Emelie Westall Lundqvist**.

## Datasets

| Activity | Functional unit | GHG (kgCO2eq / FU) |
|----------|-----------------|-------------------:|
| Hand wash (liquid) | 1 kg textile | 0.080 |
| Hand wash (powder) | 1 kg textile | 0.118 |
| Machine 30° (liquid) | 1 kg textile | 0.116 |
| Machine 30° (powder) | 1 kg textile | 0.154 |
| Machine 40° (liquid) | 1 kg textile | 0.145 |
| Machine 40° (powder) | 1 kg textile | 0.184 |
| Machine 60° (liquid) | 1 kg textile | 0.135 |
| Machine 60° (powder) | 1 kg textile | 0.174 |
| Dry cleaning | 1 kg textile | 0.260 |
| Tumble dry (cotton, closet dry) | 1 kg textile | 0.156 |
| Tumble dry (cotton, iron dry) | 1 kg textile | 0.126 |
| Tumble dry (synthetics, closet dry) | 1 kg textile | 0.132 |
| Ironing (1 min) | 1 min ironing | 0.010 |
| Liquid detergent (1 kg) | 1 kg detergent | 1.345 |
| Powder detergent (1 kg) | 1 kg detergent | 3.104 |

> Full results across all 16 EF 3.1 impact indicators: [impact-scores.csv](impact-scores.csv)

## Methodology

Detailed methodology documentation: [methodology/](methodology/)

## Data Files

| File | Description |
|------|-------------|
| [impact-scores.csv](impact-scores.csv) | Emission factors (LCIA results) for 16 EF 3.1 indicators, with per-activity functional unit |
| [ghg-contributions.csv](ghg-contributions.csv) | Per-exchange GHG contribution analysis |
| [inventory-brightway.xlsx](inventory-brightway.xlsx) | Brightway/Activity Browser compatible inventory (parameter values, formulas, exchanges) |
