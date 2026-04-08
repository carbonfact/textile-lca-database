# Life Cycle Impact Assessment

> Part of [Weaving Methodology](README.md)

## 4. Life Cycle Impact Assessment

Below are the comparison of climate change (kg CO2eq) values between available EF 3.1 datasets and LCI weaving model developed by Carbonfact.

| **S.No** | **Process Name** | **EF 3.1 (kg CO2eq)** | **Carbonfact LCI (kg CO2eq)** | **Percentage reduction in impacts from EF datasets %** | **Analysis** |
| --- | --- | --- | --- | --- | --- |
| 1 | weaving, 45 dtex-41 denier- 130/1 ne-222 nm service | 28.9 | 22.2 | 23% |  |
| 2 | weaving, 70 dtex-63 denier-84/1 ne-143 nm service | 18.8 | 14.95 | 20% |  |
| 3 | weaving, 120 dtex-108 denier-49/1 ne-83 nm service | 11.22 | 9.43 | 16% |  |
| 4 | weaving, 150 dtex-135 denier-40/1 ne-67 nm service | 9.09 | 7.86 | 14% |  |
| 5 | weaving, 170 dtex-153 denier-34/1 ne-59 nm service | 8.08 | 7.11 | 12% |  |
| 6 | weaving, 200 dtex-180 denier-30/1 ne-50 nm service | 6.96 | 6.26 | 10% |  |
| 7 | weaving, 250 dtex-225 denier-24/1 ne-40 nm service | 5.68 | 5.27 | 7% |  |
| 8 | weaving, 300 dtex-270 denier-20/1 ne-33 nm service | 4.82 | 4.57 | 5% | On average, the Carbonfact LCI shows about a 10-11% on average lower electricity demand than the EF 3.1 dataset, partly because the two systems use different electricity suppliers and grid emission factors. In addition, Carbonfact LCI adjusts sizing energy consumption based on yarn count, whereas EF 3.1 applies a single, fixed sizing impact across all counts, further contributing to the difference between the two results. |
| 9 | weaving, 330 dtex-297 denier-18/1 ne-30 nm service | 4.44 | 4.25 | 4% |  |
| 10 | weaving, 370 dtex-333 denier-16/1 ne-27 nm service | 4.02 | 3.87 | 4% |  |
| 11 | weaving (different fabric counts) service, Mix of different counts | 10.21 | 8.58 | 16% | This dataset from EF 3.1 is an average of the previous 10 datasets of yarn count ranging from 45 dtex to 370 dtex |
| 12 | weaving, air-jet service | 12.2 | 10.99 | 10% | The EF 3.1 dataset does not specify the yarn dtex used, but comparing electricity consumption across the count-specific datasets indicates that the values correspond most closely to yarns around 100 dtex. Therefore, Carbonfact applies 100 dtex as a consistent reference for all loom-type datasets. |
| 13 | weaving, generic water-jet service | 8.41 | 3.88 | 54% | Prassana et al. report that water-jet weaving requires approximately 3.5 times less energy than air-jet weaving, but the EF 3.1 dataset applies only a 35% reduction, which significantly understates this difference. In contrast, the Carbonfact LCI currently applies the full ratio reported by Prassana et al., aligning water-jet energy consumption with the values supported in the literature. |
| 14 | weaving, jacquard service | 11.57 | 9.82 | 15% | On average, the Carbonfact LCI applies electricity consumption values that are about 10–11% lower than those used in the EF 3.1 dataset, and this difference carries through to the loom-specific results as well. In addition, although EF 3.1 references the energy ratio reported by Prassana et al. in its documentation, this ratio is not consistently or rigorously applied within the EF dataset, contributing to discrepancies between the two sources. |
| 15 | weaving, rapier service | 9.50 | 8.96 | 6% |  |
| 16 | weaving, shuttle service | 9.39 | 7.25 | 23% |  |
| 17 | weaving, others service | 10.21 | 8.18 | 20% | Average of EF 3.1 datasets focused on loom type (13-16) |
| 18 | weaving, water jet loom, 83 dtex, SpinDye service | 13.09 | 4.53 | 65% | There is considerable uncertainty in the EF 3.1 yarn-dyed water-jet weaving dataset because the documentation does not explain how its energy values were determined or why they deviate so strongly from the generic water-jet process. The 83 dtex yarn-dyed dataset shows roughly 37% higher energy consumption, yet this increase is unjustified, especially since yarn dyeing occurs upstream and does not materially change the mechanical energy required for loom operation. Carbonfact therefore applies the validated lower energy ratio for water-jet weaving from Prassana et al. and models yarn-dyed weaving in line with standard mechanical energy behaviour. |
| 19 | weaving, (150 dtex), cotton (twill fabric) service | 9.48 | 8.24 | 13% | Twill fabrics typically require more weaving energy than plain fabrics because their longer floats and more complex interlacing patterns demand higher beat-up force. Since no robust published data quantify this difference, the Carbonfact LCI adopts the same relative increase observed in EF 3.1—approximately **4.7% higher energy use for twill compared with plain weave.** |
| 20 | weaving, silk service | 9.62 | 11.08 | -15% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 21 | weaving of carpet production | 3.67 | 6.09 | -66% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 22 | weaving of primary backing service | 1.23 | 1.65 | -34% | Currently used electricity consumption from EF 3.1 dataset, need to improve this model with more primary data. |
| 23 | sizing, natural fibers; single-end sizing; production mix, at plant; service | 0.607 | 0.775 | -28% | No specific dtex value or size chemical composition has been mentioned by EF. Carbonfact LCI can compute for various size compositions and yarn counts. Here the value is mentioned for 200 dtex (Carbonfact LCI) |
| 24 | sizing, synthetic fibers; single-end sizing; production mix, at plant; service | 0.561 | 0.643 | -15% | No specific dtex value or size chemical composition has been mentioned by EF. Carbonfact LCI can compute for various size compositions and yarn counts. Here the value is mentioned for 200 dtex (Carbonfact LCI) |

### Data quality rating

The PEF (Product Environmental Footprint) framework utilizes the DQR (Data Quality Rating) guideline to assess the quality of data employed in Life Cycle Assessment (LCA) studies.

This guideline assigns a score between 1 and 5 to each data point, considering four criteria:

- Precision (P), reflecting the accuracy of data;
- Time Representativeness (TiR), evaluating the data's age and relevance to the study period;
- Technological Representativeness (TeR), assessing how well the data reflects the actual production technology; and
- Geographical Representativeness (GR), determining whether the data is representative of the geographical location of the studied product system.

The DQR is calculated by averaging the weighted scores of all individual criteria (DQR = (P + TiR + TeR + GR) / 4).

Table 1 Data Quality Rating according to PEF

| **Overall data quality rating (DQR)** | **Overall data quality level** |
| --- | --- |
| DQR < 1.5 | Excellent quality |
| 1.5 < DQR < 2.0 | Very good quality |
| 2.0 < DQR < 3.0 | Good quality |
| 3.0 < DQR < 4.0 | Fair quality |
| DQR > 4.0 | Poor quality |

This scoring system allows for a standardized and transparent approach to data quality evaluation, ensuring the robustness and reliability of LCA studies within the PEF framework.

According to PEFCR, relevant process related datasets are those that contribute cumulatively to 80% of the single weighted LCIA score/ climate change impact. Once identified the datasets are individually scored for their DQR (expert judgement) and then a weighted average is taken to identify the DQR for the overall product.

| **Dataset group** | **Data quality rating** | **Comment** |
| --- | --- | --- |
| Weaving as a service \| Different fabric counts | 2.75 | We now have possibility to perform LCA for any yarn count and also alter sizing composition and thermal energy based on input data. |
| Weaving as a service \| Different loom types | 2.99 | Loom based energy consumption can be significantly improved based on primary data. Currently one journal source dictates the various energy consumptions (Prassana et al.) |
| Weaving as a service \| Carpet | 3.99 | Minimal data availability. Priority for primary data capture. |
| Weaving as a service \| Silk | 3.98 | Minimal data availability. Priority for primary data capture. |
| Weaving as a service \| Primary Backing Fabric | 3.45 |  |
| Sizing as a service \| Natural and Synthetic Fibre | 2.79 | We now have parameterised various sizing variables like size add up %, size composition, water pick up rate, thermal energy consumption etc. |
