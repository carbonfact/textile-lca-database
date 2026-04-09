# Methodology Overview

## General approach

The Carbonfact Textile LCA Database follows a **gate-to-gate** modelling approach for each textile manufacturing process. Datasets represent the environmental impact of transforming an input material (yarn, greige fabric, etc.) into an output product (yarn, fabric, dyed textile) at the factory gate.

Each process is modelled as a standalone foreground unit process, linked to the ecoinvent 3.12 background database for upstream inputs (electricity, heat, chemicals, water, waste treatment) and characterised using the **Environmental Footprint (EF) 3.1** method across 16 impact indicators.

## Functional units

| Process | Functional unit |
|---------|----------------|
| Spinning | 1 kg of finished yarn at the spinning mill gate |
| Knitting | 1 kg of knitted fabric |
| Weaving | 1 kg of woven fabric |
| Dyeing | 1 kg of dyed textile |

## System boundaries

**Included in each process:**
- Direct electricity consumption (machine operation)
- Indirect energy (HVAC, compressors, lighting, auxiliaries)
- Process-specific inputs (lubricants, sizing agents, dyes, chemicals, water)
- Capital goods (machinery) and their end-of-life
- Building infrastructure (where applicable)
- Yarn/material losses and waste treatment

**Excluded (modelled separately):**
- Upstream fibre and yarn production
- Downstream finishing, assembly, packaging, and distribution
- Use phase and end-of-life of the final product

## Background database

All datasets use **ecoinvent 3.12** (cut-off system model) as the background database. Electricity is modelled using the global market group for medium voltage (`market group for electricity, medium voltage, GLO`) unless a region-specific market is justified.

## Impact assessment method

Life Cycle Impact Assessment (LCIA) is performed using the **EF 3.1** characterisation method, reporting results for all 16 PEF impact indicators. See [impact-indicators.md](impact-indicators.md) for the full indicator list with codes, names, and units.

## Data quality

Every dataset includes a **Data Quality Rating (DQR)** based on the PEF methodology, scored across four dimensions:

- **P** — Precision (quality of measurements and modelling)
- **TiR** — Time representativeness (temporal relevance of data)
- **TeR** — Technological representativeness (technology match)
- **GR** — Geographical representativeness (regional relevance)

The overall DQR is the arithmetic mean: DQR = (P + TiR + TeR + GR) / 4. Scores range from 1 (best) to 5 (worst). See [dqr-framework.md](dqr-framework.md) for the full DQR methodology.

## Capital goods

Machinery and building infrastructure are included as capital goods, amortised over their lifetime output using mass-based allocation. This follows EF guidelines (Fazio et al., 2020) and ecoinvent practice (Weidema et al., 2013). See:
- [capital-goods.md](capital-goods.md) — Machinery amortisation framework
- [building-infrastructure.md](building-infrastructure.md) — Building allocation framework

## Scenarios

Where applicable, datasets are provided for three operating scenarios:

| Scenario | Service life | Hours/day | Days/year | Description |
|----------|-------------|-----------|-----------|-------------|
| WCS (Worst Case) | 10 years | 8 h | 300 | Single shift, shorter lifetime |
| Average | 15 years | 16 h | 300 | Double shift — **used as default** |
| BCS (Best Case) | 20 years | 24 h | 365 | Continuous operation, longest lifetime |

## Parameterisation

Many process parameters (electricity consumption, lubricant use, yarn waste) are parameterised by **yarn fineness (dtex)** and **fibre type**. This enables the database to cover a wide range of textile products from a consistent modelling framework. The parameterisation approach is documented in each process methodology:

- [Spinning methodology](../datasets/spinning/methodology/)
- [Knitting methodology](../datasets/knitting/methodology/)
- [Weaving methodology](../datasets/weaving/methodology/)
- [Dyeing methodology](../datasets/dyeing/methodology/)

## Methodology documentation

### Cross-cutting methodology

| Document | Description |
|----------|-------------|
| [Impact indicators](impact-indicators.md) | Full table of 16 EF 3.1 indicators with codes, names, and units |
| [Data Quality Rating framework](dqr-framework.md) | PEF DQR scoring methodology and calculation steps |
| [Capital goods](capital-goods.md) | Machine amortisation approach |
| [Building infrastructure](building-infrastructure.md) | Building allocation approach |

### Process-specific methodology

| Process | Documentation |
|---------|---------------|
| Spinning | [Ring Spun](../datasets/spinning/methodology/ring-spun/) · [Melt Spinning](../datasets/spinning/methodology/melt-spinning/) · [Open End Rotor](../datasets/spinning/methodology/open-end-rotor/) |
| Knitting | [Flat](../datasets/knitting/methodology/flat-knitting/) · [Circular](../datasets/knitting/methodology/circular-knitting/) · [Seamless](../datasets/knitting/methodology/seamless-knitting/) · [Hosiery](../datasets/knitting/methodology/hosiery-knitting/) · [3D](../datasets/knitting/methodology/3d-knitting/) |
| Weaving | [Weaving](../datasets/weaving/methodology/) |
| Dyeing | [Dyeing](../datasets/dyeing/methodology/) |

## References

- Fazio, S., Castellani, V., & Sala, S. (2020). *Guide for EF-compliant data sets (Version 2.0).* European Commission, JRC.
- Weidema, B. P. et al. (2013). *Overview and methodology: Data quality guideline for the ecoinvent database version 3.* ecoinvent Centre.
- ADEME & Ministere de la Transition Ecologique (2024). *Ecobalyse methodological guide — Textiles and footwear.*
