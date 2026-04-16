# Carbonfact Textile LCA Database

[![License: CC BY-SA 4.0](https://img.shields.io/badge/License-CC%20BY--SA%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-sa/4.0/)
[![Version](https://img.shields.io/badge/version-v1.1.0-blue.svg)](CHANGELOG.md)

**The open-source reference database for textile lifecycle assessment.**

## What is this?

The Carbonfact Textile LCA Database is a free, open-source collection of lifecycle assessment (LCA) datasets for core textile manufacturing processes, with impact scores calculated using EF 3.1 characterization factors across 16 PEF (Product Environmental Footprint) impact indicators. Every dataset includes GHG contribution breakdowns and data quality ratings.

## What's included

| Process | Datasets | Technologies | Functional Unit |
|---------|----------|-------------|-----------------|
| [Spinning](datasets/spinning/) | 159 | Ring spun, Melt spinning, Open end rotor | 1 kg yarn |
| [Knitting](datasets/knitting/) | 13 | Flat, Circular, Seamless, Hosiery, 3D | 1 kg fabric |
| [Weaving](datasets/weaving/) | 16 | Air jet, Rapier, Water jet, Projectile | 1 kg fabric |
| [Dyeing](datasets/dyeing/) | 38 | Exhaust, Continuous, Pad steam, Thermosol | 1 kg dyed textile |
| [Sneaker Shoe Assembly](datasets/sneaker-shoe-assembly/) | 2 | VN and GLO electricity scenarios | 1 pair of footwear |
| [Synthetic PU Leather](datasets/synthetic-pu-leather/) | 2 | DMF-free (water-borne), DMF-based (solvent-based) | 1 m² PU leather |

**Upcoming**

- [ ] Printing
- [ ] Fabric Finishing
- [ ] Nonwoven Fabric Formation
- [x] ~~Synthetic PU Leather (DMF-free & DMF-based)~~
- [ ] Bovine Leather
- [ ] Natural Rubber (STR Production)
- [x] ~~Footwear Assembly~~
- [ ] Use Phase

## Data files

Each process directory contains 4 files:

| File | Description |
|------|-------------|
| `impact-scores.csv` | Emission factors (LCIA results) across all 16 EF 3.1 impact indicators, plus Data Quality Rating (DQR) scores for each dataset. Where available, includes the **Input required (kg)** loss factor — the amount of input material needed to produce 1 kg of output (e.g., 1.18 means you need 1.18 kg of input per 1 kg of output). Multiply your upstream material impact by this factor to account for process losses. This is the primary results file. |
| `ghg-contributions.csv` | Per-exchange GHG contribution analysis showing which inputs and emissions drive the climate change impact of each dataset. |
| `process-steps.json` | Machine-readable emission factor format. Structured JSON containing process parameters, exchange amounts, and metadata suitable for programmatic use. |
| `inventory-brightway.xlsx` | Brightway/Activity Browser compatible lifecycle inventory (LCI). Can be directly imported into Brightway2 for further LCA modeling. |

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
- [Sneaker Shoe Assembly methodology](datasets/sneaker-shoe-assembly/methodology/)
- [Synthetic PU Leather methodology](datasets/synthetic-pu-leather/methodology/)

Cross-cutting methodology docs (applicable to all processes):

- [Impact indicators](methodology/impact-indicators.md) — Full table of 16 EF 3.1 indicators
- [Data Quality Rating framework](methodology/dqr-framework.md) — PEF DQR scoring methodology
- [Capital goods](methodology/capital-goods.md) — Machine amortization approach
- [Building infrastructure](methodology/building-infrastructure.md) — Building allocation approach

## Background database & pre-calculated scores

If you want to **use the emission factors or pre-calculated impact scores**, these are shared openly in this repository. The `impact-scores.csv` and `ghg-contributions.csv` files in each process directory give you ready-to-use results.

The lifecycle inventories in this repository are built on top of **ecoinvent 3.12** as the background database. If you want to run these inventories in an LCA software (e.g. Brightway, Activity Browser, SimaPro, openLCA), you will need a valid [ecoinvent license](https://ecoinvent.org/offerings/).

## Versioning & changelog

This project follows [Semantic Versioning](https://semver.org/). Major versions indicate breaking schema changes, minor versions add new datasets or processes, and patch versions fix data errors.

See [CHANGELOG.md](CHANGELOG.md) for a full history of changes.

## Contributing

We welcome contributions from the LCA community. See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines on reporting data errors, requesting new datasets, proposing methodology improvements, and contributing data.

## License

This work is licensed under a [Creative Commons Attribution-ShareAlike 4.0 International License](LICENSE).

### What you can do

- **Use** the data for any purpose, including commercial use — no permission needed.
- **Share** — copy and redistribute the data in any medium or format.
- **Adapt** — remix, transform, modify, or build upon the datasets (e.g. improve an inventory, add new exchanges, recalculate with updated characterization factors).

### What you must do

- **Give credit** — You must include the following attribution when sharing or using the data:

  > Data source: [Carbonfact Textile LCA Database](https://github.com/carbonfact/textile-lca-database), CC BY-SA 4.0

  We strongly encourage displaying this attribution on the same page or screen where emission factors or impact scores derived from this database are shown, rather than burying it in a bibliography or appendix.

- **ShareAlike** — if you modify or improve the datasets and distribute your version, you must release it under the same CC BY-SA 4.0 license (or a compatible one). This ensures improvements stay open for the community.

### What you cannot do

- **Add restrictions** — you may not apply legal terms or technological measures that restrict others from doing anything the license permits.

### Commercial licensing

For companies that need different attribution terms or cannot comply with the ShareAlike requirement, a separate commercial license is available. Contact us at science@carbonfact.com.

## Citation

If you use this database in your work, please cite it as:

```bibtex
@dataset{carbonfact_textile_lca_2026,
  title     = {Carbonfact Textile LCA Database},
  author    = {Carrières, Vincent and Ganesan, Kishore and Vandepaer, Laurent and Vieira, Gustavo},
  year      = {2026},
  version   = {1.1.0},
  url       = {https://github.com/carbonfact/textile-lca-database},
  license   = {CC-BY-SA-4.0}
}
```

## Quick start (Python)

```python
import pandas as pd

knitting = pd.read_csv("datasets/knitting/impact-scores.csv")
print(knitting[["Activity", "GHG"]].to_string(index=False))
```

