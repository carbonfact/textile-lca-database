# Collective Shoe Assembly — Lifecycle Inventory

## 1. Foreground database

- **Database name**: shoe assembly collective
- **Activities**: 20 foreground activities (12 process activities + 8 product activities)
- **Exchanges**: 113 total (93 technosphere + 20 production)
- **Background links**: 72 exchanges to ecoinvent-3.12-cutoff, 41 internal exchanges

## 2. Assembly structure

The top-level activity "Shoe Assembly (PU/Microfiber Upper + TPR/EVA/Rubber Outsole) – Women's Boots" aggregates three sub-processes with cumulative loss rates:

```
Shoe Assembly (top-level, per location)
├── Cutting (IOR = 1.0382)  ×  1.010024  [= 1.0382 × (1.006 × 1.004) / (1.006 × 1.004) ... cumulative upstream]
├── Stitching (IOR = 1.006)  ×  1.004000
├── Lasting (IOR = 1.004)  ×  1.000000
└── Waste: market for waste yarn and waste textile  ×  -0.048607 kg
```

The aggregated input/output ratio is 1.0382 × 1.006 × 1.004 = **1.048607**.

## 3. Key exchanges (top-level activity)

| Exchange | Amount | Unit | Type |
|----------|--------|------|------|
| Lasting – Shoe Assembly | 1.000 | unit | technosphere |
| Stitching – Shoe Assembly | 1.004 | unit | technosphere |
| Cutting – Shoe Assembly | 1.010 | unit | technosphere |
| market for waste yarn and waste textile | -0.049 | kg | technosphere |

## 4. Location variants

Each assembly step exists in three location variants (CN, GLO, IT). The top-level activity references the location-matched variant of each sub-process, ensuring consistent electricity markets throughout the supply chain.

## 5. Brightway import

The inventory file (`inventory-brightway.xlsx`) contains the full foreground database in Brightway2-compatible format. To import:

```python
import bw2data as bd
import bw2io as bi

bd.projects.set_current("shoe-assembly-collective")
# Requires ecoinvent 3.12 cutoff as background
lci = bi.ExcelImporter("inventory-brightway.xlsx")
lci.apply_strategies()
lci.match_database("ecoinvent-3.12-cutoff", fields=["name", "location", "unit"])
lci.write_database()
```
