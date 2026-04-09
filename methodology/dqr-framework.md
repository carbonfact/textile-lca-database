# Data Quality Rating (DQR) Framework

This document describes the Data Quality Rating (DQR) methodology applied to all process datasets in the Carbonfact Textile LCA Database. The approach follows the **Product Environmental Footprint (PEF)** guidance for data quality assessment.

## Method

Each process dataset is assessed using the PEF DQR method. Exchanges that contribute cumulatively to the **top 80% of the GHG impact** are rated individually across four criteria. All remaining exchanges receive a default score of 3.

The four criteria are:

| Criterion | Abbreviation | Description |
|-----------|:------------:|-------------|
| Precision | P | Degree of measurement/estimation accuracy |
| Time representativeness | TiR | Age and currency of the data |
| Technological representativeness | TeR | Match between modelled and actual technology |
| Geographical representativeness | GR | Match between modelled and actual geography |

Each criterion is scored from 1 (best) to 5 (worst). The overall DQR for an exchange is calculated as:

$$
\text{DQR} = \frac{P + TiR + TeR + GR}{4}
$$

## Quality levels

| Overall DQR | Quality level |
|---|---|
| DQR < 1.5 | Excellent quality |
| 1.5 < DQR < 2.0 | Very good quality |
| 2.0 < DQR < 3.0 | Good quality |
| 3.0 < DQR < 4.0 | Fair quality |
| DQR > 4.0 | Poor quality |

## Calculation steps

The following procedure is applied to each process dataset, following the PEFCR approach:

1. **Identify contributions to climate change** — For each activity, compute the percentage contribution of every exchange to the total GHG impact.

2. **Select relevant exchanges** — Choose exchanges that cumulatively contribute to more than 80% of the climate change impact. These are the exchanges that will be individually scored.

3. **Rescale contributions to 100%** — Normalize the selected exchanges so their contributions sum to 100%.

4. **Assign data quality scores through expert judgment** — Rate each selected exchange on the four dimensions (P, TiR, TeR, GR) using a data source hierarchy: primary data > peer-reviewed journals > industry reports > machinery data.

5. **Compute weighted average DQR** — Calculate the overall process DQR as a weighted average across the selected exchanges, where the weights are the rescaled GHG contribution percentages.

All exchanges below the 80% cumulative threshold receive a default score of 3 on all four dimensions.

---

## Dyeing

### DQR scoring table

| Exchange category | P | TiR | TeR | GR | DQR |
|---|:---:|:---:|:---:|:---:|:---:|
| Electricity -- ecoinvent 3.12 GLO market group | 2 | 2 | 2 | 3 | 2.25 |
| Heat for dyeing -- Carbonfact mix (50% NG / 20% coal / 30% fuel oil) | 2 | 2 | 2 | 3 | 2.25 |
| Dye precursors -- specific ecoinvent datasets | 2 | 2 | 2 | 3 | 2.25 |
| Standard inorganic auxiliaries -- single-chemical ecoinvent markets | 2 | 2 | 2 | 3 | 2.25 |
| Wastewater -- textile production, ecoinvent 3.12 RoW | 2 | 2 | 2 | 3 | 2.25 |
| Water -- tap water, ecoinvent 3.12 GLO | 3 | 2 | 3 | 3 | 2.75 |
| Generic chemical auxiliaries | 3 | 2 | 3 | 3 | 2.75 |
| Proxy chemicals -- glycine (proxy for phenyl glycine), sodium amide | 3 | 2 | 3 | 3 | 2.75 |
| Dyes -- Carbonfact-built (Azo acid / Azo disperse / Azo reactive / Anthraquinone vat) | 3 | 3 | 3 | 3 | 3.00 |

### Rationale

- **Electricity**: ecoinvent 3.12 GLO market group for medium voltage. Recent data (2023) but aggregated global technology and geography mix, hence GR = 3.
- **Heat for dyeing**: Carbonfact-built heat mix from ecoinvent 3.12 datasets. Proportions derived from "steam production in chemical industry". GLO geography limitation drives GR = 3.
- **Dye precursors**: Individual organic and inorganic chemicals with dedicated ecoinvent 3.12 datasets. Good precision and technological match.
- **Standard inorganic auxiliaries**: Single-chemical ecoinvent 3.12 markets (e.g., sodium hydroxide, sodium chloride). Well-characterised processes.
- **Wastewater**: ecoinvent 3.12 textile-specific wastewater treatment (RoW). Dedicated textile production dataset.
- **Water**: ecoinvent 3.12 generic tap water (GLO). No regional water stress differentiation, lowering P and TeR to 3.
- **Generic chemical auxiliaries**: ecoinvent 3.12 aggregated market datasets. Aggregation reduces precision and technological specificity.
- **Proxy chemicals**: Glycine used as structural proxy for phenyl glycine; sodium amide used directly. Proxy approach lowers P and TeR to 3.
- **Dyes**: Built from Indian environmental clearance applications. Novel datasets with limited peer review, high uncertainty across all criteria.

---

## Spinning

### Method

For most spinning activities, **electricity alone exceeds 80%** of the GHG impact and is therefore the only individually scored exchange. Two exceptions exist:

- **Melt spinning**: Heat also enters the top 80% and is individually scored.
- **Woollen Wool 370 dtex** (edge case): Electricity contributes only 78.9% of GHG impact. Waste mineral oil also enters the top 80% threshold and is individually scored.

All other exchanges fall below the 80% cumulative threshold and receive the default score of 3.

### DQR scoring table

| Exchange category | Individually scored? | P | TiR | TeR | GR | DQR |
|---|---|:---:|:---:|:---:|:---:|:---:|
| Electricity -- ecoinvent 3.12 market group, medium voltage | Yes -- all activities | 2 | 2 | 2 | 3 | 2.25 |
| Heat -- industrial, natural gas, ecoinvent 3.12 market group | Yes -- melt spinning only | 2 | 2 | 2 | 3 | 2.25 |
| Waste mineral oil -- ecoinvent 3.12 market (RoW) | Yes -- Woollen Wool 370 dtex only | 3 | 2 | 3 | 3 | 2.75 |
| All other exchanges | No -- below 80% threshold, default 3 | 3 | 3 | 3 | 3 | 3.00 |

### Rationale

- **Electricity**: Same rationale as dyeing. ecoinvent 3.12 GLO market group, recent data, aggregated global mix.
- **Heat (melt spinning)**: Industrial natural gas heat from ecoinvent 3.12 market group. Good precision, but global geography aggregation.
- **Waste mineral oil**: ecoinvent 3.12 market (RoW). Generic waste treatment dataset; lower precision and technological representativeness than process-specific exchanges.
- **All other exchanges**: Below the 80% cumulative GHG threshold. Default scores assigned per PEF guidance.

---

## Knitting

### Method

For **all knitting activities**, electricity alone exceeds 80% of the GHG impact. It is the only individually scored exchange. All other exchanges (lubricating oil, capital goods, infrastructure, waste treatment) receive the default score of 3.

### DQR scoring table

| Exchange category | P | TiR | TeR | GR | DQR |
|---|:---:|:---:|:---:|:---:|:---:|
| Electricity -- ecoinvent 3.12 market group, medium voltage | 2 | 2 | 2 | 3 | 2.25 |
| Lubricating oil -- ecoinvent 3.12 (default) | 3 | 3 | 3 | 3 | 3.00 |
| Building machine -- ecoinvent 3.12 capital goods proxy (default) | 3 | 3 | 3 | 3 | 3.00 |
| Building, hall -- ecoinvent 3.12 infrastructure proxy (default) | 3 | 3 | 3 | 3 | 3.00 |
| Waste mineral oil -- ecoinvent 3.12 market (default) | 3 | 3 | 3 | 3 | 3.00 |
| Waste steel -- ecoinvent 3.12 market (default) | 3 | 3 | 3 | 3 | 3.00 |
| WEEE treatment, shredding -- ecoinvent 3.12 (default) | 3 | 3 | 3 | 3 | 3.00 |

### Rationale

- **Electricity**: ecoinvent 3.12 GLO market group for medium voltage. Dominates the GHG profile across all knitting technologies (circular, seamless, hosiery, flat, WHOLEGARMENT).
- **All other exchanges**: Individually contribute well below the 80% cumulative threshold. Default DQR of 3.00 assigned per PEF guidance.

---

## Weaving

### Method

Only exchanges contributing to the top 80% of GHG impact are rated individually. For weaving, electricity and heat sources are the dominant contributors.

### DQR scoring table

| Exchange category | P | TiR | TeR | GR | DQR |
|---|:---:|:---:|:---:|:---:|:---:|
| Electricity (ecoinvent 3.12 GLO market group, medium voltage) | 2 | 2 | 2 | 3 | 2.25 |
| Heat mix -- Carbonfact-built (NG 47.5% / LFO 28.5% / Coal 16%) | 2 | 2 | 2 | 3 | 2.25 |
| Heat -- natural gas, industrial furnace >100kW (ecoinvent RoW) | 2 | 2 | 2 | 3 | 2.25 |
| Heat -- light fuel oil, industrial furnace 1MW (ecoinvent RoW) | 2 | 2 | 3 | 3 | 2.50 |
| Heat -- hard coal, industrial furnace 1-10MW (ecoinvent RoW) | 2 | 2 | 3 | 3 | 2.50 |
| Maize starch (ecoinvent 3.12 GLO) | 2 | 2 | 2 | 3 | 2.25 |
| All other exchanges | 3 | 3 | 3 | 3 | 3.00 |

### Rationale

- **Electricity**: ecoinvent 3.12 GLO market group for medium voltage. Same scoring rationale as other processes.
- **Heat mix (Carbonfact-built)**: Weighted blend of natural gas (47.5%), light fuel oil (28.5%), and coal (16%). Built from ecoinvent 3.12 individual heat datasets. Good precision and time representativeness; global geography limitation.
- **Heat -- natural gas**: ecoinvent RoW dataset for industrial furnace >100kW. Good technological match for large-scale weaving operations.
- **Heat -- light fuel oil**: ecoinvent RoW dataset for industrial furnace 1MW. TeR = 3 because the specific furnace size may not match all weaving plant configurations.
- **Heat -- hard coal**: ecoinvent RoW dataset for industrial furnace 1-10MW. TeR = 3 for the same furnace-size matching limitation.
- **Maize starch**: ecoinvent 3.12 GLO market. Used as a sizing agent in weaving preparation. Good data quality with global geography limitation.
- **All other exchanges**: Below the 80% cumulative GHG threshold. Default scores assigned per PEF guidance.

---

## References

- European Commission (2013). *Commission Recommendation 2013/179/EU on the use of common methods to measure and communicate the life cycle environmental performance of products and organisations*. Official Journal of the European Union.
- Fazio, S., Castellani, V., Sala, S., Schau, E.M., Secchi, M., Zampori, L. and Diaconu, E. (2018). *Supporting information to the characterisation factors of recommended EF Life Cycle Impact Assessment method*. EUR 28888 EN, European Commission.
- Weidema, B.P. and Wesnaes, M.S. (1996). Data quality management for life cycle inventories -- an example of using data quality indicators. *Journal of Cleaner Production*, 4(3-4), pp.167-174.
