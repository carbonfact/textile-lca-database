# Impact Indicators

The methodology behind the foreground inventories in the Carbonfact Textile LCA Database targets the 16 impact indicators defined in the **Environmental Footprint (EF) 3.1** method, as recommended by the European Commission for Product Environmental Footprint (PEF) studies.

> ℹ️ **Reference only — no pre-calculated scores are published in this repository.** This page documents the methodological framework. To compute the indicators, import an `inventory-brightway.xlsx` foreground inventory into your LCA tool with a valid [ecoinvent v3.12 license](https://ecoinvent.org/offerings/) and apply EF 3.1 characterization factors. See [README §Background data](../README.md#background-data).

## Indicator table

| Code | Full name | Unit | EF 3.1 method |
|------|-----------|------|----------------|
| ACD | Acidification | mol H+ eq/kg | Accumulated Exceedance |
| ETF | Ecotoxicity, freshwater | CTUe/kg | USEtox 2.1 |
| FRU | Fossil resource use | MJ/kg | CML 2002 |
| FWE | Eutrophication, freshwater | kg P eq/kg | EUTREND |
| GHG | Climate change | kg CO2 eq/kg | IPCC 2013 (GWP100) |
| HTC | Human toxicity, cancer | CTUh/kg | USEtox 2.1 |
| HTN | Human toxicity, non-cancer | CTUh/kg | USEtox 2.1 |
| IOR | Ionising radiation | kBq U-235 eq/kg | Human health effect model |
| LDU | Land use | Pt/kg | LANCA |
| MRU | Mineral and metal resource use | kg Sb eq/kg | CML 2002 |
| OZD | Ozone depletion | kg CFC-11 eq/kg | WMO 1999 |
| PCO | Photochemical ozone formation | kg NMVOC eq/kg | LOTOS-EUROS |
| PMA | Particulate matter | disease incidence/kg | UNEP 2016 |
| SWE | Eutrophication, marine | kg N eq/kg | EUTREND |
| TRE | Eutrophication, terrestrial | mol N eq/kg | Accumulated Exceedance |
| WTU | Water use | m3 world eq/kg | AWARE |

## Notes

- Indicator units are reported per **1 kg** of output product (yarn, fabric, or dyed textile), matching the functional unit of each process — adapt to your product's functional unit when computing scores in your LCA tool.
- The GHG indicator uses the IPCC 2013 Global Warming Potential with a 100-year time horizon (GWP100), excluding biogenic carbon.
- Characterization factors are sourced from the EF 3.1 method as implemented in ecoinvent 3.12 — you need your own ecoinvent license to apply them.
- The codes used in this database (e.g., GHG, ACD) are short-form aliases used by the Carbonfact Emission Factor System (EFS). They map one-to-one to the official EF 3.1 indicator names listed above.
