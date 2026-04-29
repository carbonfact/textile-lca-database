# Roadmap

This document tracks planned improvements to the Carbonfact Textile LCA Database beyond new datasets. The list of upcoming process datasets lives in the [README](README.md#whats-included). Items below are grouped by theme, not prioritized. See [CHANGELOG.md](CHANGELOG.md) for what has already shipped.

If you'd like to help with any of these, or think something is missing, open an [issue](https://github.com/carbonfact/textile-lca-database/issues) or [discussion](https://github.com/carbonfact/textile-lca-database/discussions).

## Data formats & exports

- [ ] **EcoSpold 1 export** — provide inventories in EcoSpold 1 format alongside the current Brightway/Activity Browser xlsx, for compatibility with SimaPro and other tools.
- [ ] **Consolidated inventory workbook** — a single Excel file bundling every process's foreground inventory and DQR breakdown across all processes, so users can browse the full database without opening one xlsx per process.

## Methodology

- [ ] **DQR refresh** — re-compute Data Quality Ratings across datasets using the current framework, and document any scoring changes in the changelog.

## External verification

- [ ] **Independent critical review** — submit selected process datasets and the cross-cutting methodology to an independent ISO 14040/14044-aligned critical review, and publish the reviewer's statement alongside the affected datasets.
- [x] **Community feedback channel** — [GitHub Discussions](https://github.com/carbonfact/textile-lca-database/discussions) is open continuously for LCA practitioners to comment on assumptions, proxies, impact-category coverage, or anything else. No fixed review windows at this stage; feedback is welcome at any time.

## Aii benchmark refresh

- [ ] Refresh dyeing and wet-processing datasets that rely on the [Apparel Impact Institute Facility Benchmark](https://apparelimpact.org/) as new Aii releases become available.
