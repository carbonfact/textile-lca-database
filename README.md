# Carbonfact Textile LCA Database

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Version](https://img.shields.io/badge/version-v1.0.0-blue.svg)](CHANGELOG.md)

**The open-source reference database for textile lifecycle assessment.**

## What is this?

The Carbonfact Textile LCA Database is a free, open-source collection of lifecycle assessment (LCA) datasets for core textile manufacturing processes. Carbonfact built this as a transparent, publicly auditable replacement for the closed-source datasets bundled with the EF 3.1 methodology -- enabling anyone to run rigorous textile LCA without paying for proprietary databases.

The database contains 230 datasets covering 4 textile processes. All impact scores are calculated using EF 3.1 characterization factors across 16 PEF (Product Environmental Footprint) impact indicators. Every dataset includes full lifecycle inventory data, GHG contribution breakdowns, and data quality ratings, making this the most comprehensive open textile LCA resource available.

## What's included

| Process | Datasets | Technologies | Functional Unit |
|---------|----------|-------------|-----------------|
| [Spinning](datasets/spinning/) | 159 | Ring spun, Melt spinning, Open end rotor | 1 kg yarn |
| [Knitting](datasets/knitting/) | 13 | Flat, Circular, Seamless, Hosiery, 3D | 1 kg fabric |
| [Weaving](datasets/weaving/) | 16 | Air jet, Rapier, Water jet, Projectile | 1 kg fabric |
| [Dyeing](datasets/dyeing/) | 38 | Exhaust, Continuous, Pad steam, Thermosol | 1 kg dyed textile |

## Data files

Each process directory contains 4 files:

| File | Description |
|------|-------------|
| `impact-scores.csv` | LCIA results across all 16 EF 3.1 impact indicators, plus Data Quality Rating (DQR) scores for each dataset. This is the primary results file. |
| `ghg-contributions.csv` | Per-exchange GHG contribution analysis showing which inputs and emissions drive the climate change impact of each dataset. |
| `process-steps.json` | Machine-readable emission factor format. Structured JSON containing process parameters, exchange amounts, and metadata suitable for programmatic use. |
| `inventory-brightway.xlsx` | Brightway/Activity Browser compatible lifecycle inventory (LCI). Can be directly imported into Brightway2 for further LCA modeling. |

## Quick start

```python
import pandas as pd

knitting = pd.read_csv("datasets/knitting/impact-scores.csv")
print(knitting[["Activity", "GHG"]].to_string(index=False))
```

## Impact indicators

All datasets report results for the 16 EF 3.1 impact indicators:

| Code | Indicator | Unit |
|------|-----------|------|
| ACD | Acidification | molH+e/kg |
| ETF | Ecotoxicity, freshwater | CTUe/kg |
| FRU | Fossil resource use | MJ/kg |
| FWE | Eutrophication, freshwater | kgPe/kg |
| GHG | Climate change | kgCO2eq/kg |
| HTC | Human toxicity, cancer | CTUhtc/kg |
| HTN | Human toxicity, non-cancer | CTUhtn/kg |
| IOR | Ionising radiation | kBqU235e/kg |
| LDU | Land use | Pt/kg |
| MRU | Mineral resource use | kgSbe/kg |
| OZD | Ozone depletion | kgCFC11e/kg |
| PCO | Photochemical ozone formation | kgNMVOCe/kg |
| PMA | Particulate matter | dis.inc./kg |
| SWE | Eutrophication, marine | kgNe/kg |
| TRE | Eutrophication, terrestrial | molNe/kg |
| WTU | Water use | m3Weq/kg |

## Methodology

For a general introduction to the LCA approach, see the [methodology overview](methodology/overview.md). Each process directory contains detailed methodology documentation covering system boundaries, data sources, allocation rules, and modeling choices:

- [Spinning methodology](datasets/spinning/methodology/)
- [Knitting methodology](datasets/knitting/methodology/)
- [Weaving methodology](datasets/weaving/methodology/)
- [Dyeing methodology](datasets/dyeing/methodology/)

Cross-cutting methodology docs (applicable to all processes):

- [Impact indicators](methodology/impact-indicators.md) — Full table of 16 EF 3.1 indicators
- [Data Quality Rating framework](methodology/dqr-framework.md) — PEF DQR scoring methodology
- [Capital goods](methodology/capital-goods.md) — Machine amortization approach
- [Building infrastructure](methodology/building-infrastructure.md) — Building allocation approach

## Data quality

Every dataset includes a Data Quality Rating (DQR) based on the PEF framework. DQR scores are computed across four dimensions:

- **P** -- Precision (measurement quality)
- **TiR** -- Time representativeness (temporal relevance)
- **TeR** -- Technological representativeness (technology match)
- **GR** -- Geographical representativeness (regional relevance)

Scores range from 1 (best) to 5 (worst). The overall DQR is the weighted average of these four dimensions. Datasets with a DQR below 3.0 are considered high quality under PEF guidelines.

## Versioning & changelog

This project follows [Semantic Versioning](https://semver.org/). Major versions indicate breaking schema changes, minor versions add new datasets or processes, and patch versions fix data errors.

See [CHANGELOG.md](CHANGELOG.md) for a full history of changes.

## Contributing

We welcome contributions from the LCA community. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting data errors, requesting new datasets, proposing methodology improvements, and contributing data.

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](LICENSE).

You are free to share and adapt this data for any purpose, including commercial use, as long as you give appropriate credit to Carbonfact and distribute any derivative works under the same license.

## Citation

If you use this database in your work, please cite it as:

```bibtex
@dataset{carbonfact_textile_lca_2026,
  title     = {Carbonfact Textile LCA Database},
  author    = {{Carbonfact Science Team}},
  year      = {2026},
  version   = {1.0.0},
  url       = {https://github.com/carbonfact/textile-lca-database},
  license   = {CC-BY-SA-4.0}
}
```

## Roadmap

- [x] Spinning (159 datasets)
- [x] Knitting (13 datasets)
- [x] Weaving (16 datasets)
- [x] Dyeing (38 datasets)
- [ ] Finishing
- [ ] Synthetic Leather
- [ ] Nonwoven
