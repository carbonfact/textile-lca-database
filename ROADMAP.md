# Roadmap

This document tracks planned improvements to the Carbonfact Textile LCA Database beyond new datasets. The list of upcoming process datasets lives in the [README](README.md#whats-included). Items below are grouped by theme, not prioritized. See [CHANGELOG.md](CHANGELOG.md) for what has already shipped.

If you'd like to help with any of these, or think something is missing, open an [issue](https://github.com/carbonfact/textile-lca-database/issues) or [discussion](https://github.com/carbonfact/textile-lca-database/discussions).

## Data formats & exports

- [ ] **EcoSpold 1 export** — provide inventories in EcoSpold 1 format alongside the current Brightway/Activity Browser xlsx, for compatibility with SimaPro and other tools.
- [ ] **Consolidated workbook** — a single Excel file bundling every dataset's impact scores, DQR breakdown, and key energy inputs (electricity, heat) across all processes, so users can compare processes without stitching CSVs together.

## Impact scores file

- [ ] **Energy input columns** — add electricity (kWh) and heat (MJ) per functional unit directly in each process's `impact-scores.csv`, so these key inventory values are visible without opening the Brightway inventory.
- [ ] **GHG sub-category breakdown** — split the climate change (GHG) result into fossil, biogenic, and land use change sub-totals, so users can see the composition of each dataset's carbon footprint rather than only the aggregated kgCO2eq value.

## Methodology

- [ ] **DQR refresh** — re-compute Data Quality Ratings across datasets using the current framework, and document any scoring changes in the changelog.

## Aii benchmark refresh

- [ ] Refresh dyeing and wet-processing datasets that rely on the [Apparel Impact Institute Facility Benchmark](https://apparelimpact.org/) as new Aii releases become available.
