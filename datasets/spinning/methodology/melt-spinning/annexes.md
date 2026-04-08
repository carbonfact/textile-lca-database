# Annexes

> Part of [Melt Spinning Methodology](README.md)

## 10. References

### Primary literature

Altun, S. (2012). Prediction of textile waste profile and recycling opportunities in Turkey. *Fibres & Textiles in Eastern Europe*, *20*(5), 16--20.

Moazzem, S., Jones, D., Vlieg, M., & Naiker, D. (2022). Inaccurate polyester textile environmental product declarations. *Clean Technologies and Recycling*, *2*(1), 47--63. [https://doi.org/10.3934/ctr.2022004](https://doi.org/10.3934/ctr.2022004)

Pfaff, L., Horst, L., Snoeckx, H., et al. (2024). Natural diversity screening, assay development, and characterization of nylon-6 enzymatic depolymerization. *Nature Communications*, *15*, 1043. [https://doi.org/10.1038/s41467-024-45523-5](https://doi.org/10.1038/s41467-024-45523-5)

Rawal, A., & Mukhopadhyay, S. (2014). Melt spinning of synthetic polymeric filaments. In *Advances in filament yarn spinning of textiles and polymers* (pp. 75--99). Woodhead Publishing. [https://doi.org/10.1533/9780857099174.2.75](https://doi.org/10.1533/9780857099174.2.75)

Royal Society of Chemistry. (2023). Supplementary Information -- Acrylic fibre LCA inventory (Table S8: Utilities). *RSC Advances*.

Van der Velden, N. M., Patel, M. K., & Vogtlander, J. G. (2014). LCA benchmarking study on textiles made of cotton, polyester, nylon, acryl, or elastane. *The International Journal of Life Cycle Assessment*, *19*(2), 331--356. [https://doi.org/10.1007/s11367-013-0626-9](https://doi.org/10.1007/s11367-013-0626-9)

### Standards and guidelines

ISO 14044:2006. *Environmental management -- Life cycle assessment -- Requirements and guidelines*. International Organization for Standardization.

ISO 14025:2006. *Environmental labels and declarations -- Type III environmental declarations*. International Organization for Standardization.

### Databases

ADEME, & Ministere de la Transition Ecologique. (2024). *Ecobalyse methodological guide -- Textiles and footwear* (Version 1.0). Paris, France.

Beta. (2023). *Wet spinning's water problem meets its closed-loop comeback*. Retrieved from [https://beta.co.id/en/blog/wet-spinnings-water-problem](https://beta.co.id/en/blog/wet-spinnings-water-problem)

Ecoinvent Association. (2024). *ecoinvent database* (Version 3.10). Zurich, Switzerland. [https://ecoinvent.org](https://ecoinvent.org/)

European Commission Joint Research Centre. (2024). *Environmental Footprint reference package* (EF 3.1). Brussels, Belgium.

### Technical references

Khoo, H. H. (2019). LCA of plastic waste recovery into recycled materials, energy and fuels. *Resources, Conservation and Recycling*, *145*, 67--77. [https://doi.org/10.1016/j.resconrec.2019.02.016](https://doi.org/10.1016/j.resconrec.2019.02.016)

Radin Maya Saphira Radin Mohamed, Che Ku Eddy Nizwan Che Ku Husin, Mohd Arif Anuar Mohd Salleh, Muhammad Zameri Mat Saman. (2014). Energy recovery from polyethylene terephthalate (PET) recycling process. *Journal of Applied Sciences*, *14*(15), 1781--1785. [https://doi.org/10.3923/jas.2014.1781.1785](https://doi.org/10.3923/jas.2014.1781.1785)

---

## Appendix A: Polymer production energy (optional upstream module)

**Purpose:** For users requiring **cradle-to-gate** analysis (monomers -> polymer -> yarn), this appendix provides polymerization energy data.

**System boundary:** Monomers -> Polymer granules (polymerization process only, does NOT include spinning).

**Critical note:** These energies are for **POLYMER production only**. To get full yarn cradle-to-gate:

$$
\text{Yarn (cradle-to-gate)} = \text{Polymer production (below)} + \text{Spinning (Section 4)}
$$

**Example for PET FDY:**

$$
83 \text{ MJ/kg (PET polymerization)} + 9.08 \text{ MJ/kg (FDY spinning)} = 92.08 \text{ MJ/kg total}
$$

### Polymer production energy table

| Material | Polymerization Energy (MJ/kg) | GWP (kg CO2e/kg) | Data Quality | Source |
|---|---|---|---|---|
| **PET (virgin)** | 80--88 | 3.5--4.0 | High | Radin 2014 |
| **PET (recycled, mechanical)** | 20--30 | 0.9--1.3 | High | Khoo 2019 |
| **PA6 (virgin)** | ~197 | 10.4 | High | Pfaff et al. 2024 |
| **PA66 (virgin)** | ~200 | 10.5 | High | Estimated from PA6 |
| **PP (virgin)** | 70--80 | 3.0--3.5 | Moderate | Radin 2014 |
| **Acrylic (PAN)** | 110--130 | 5.5--6.5 | Moderate | Estimated |
| **Acetate** | 40--60 | 2.0--3.0 | Moderate | Estimated |
| **Viscose (regenerated cellulose)** | 30--50 | 1.5--2.5 | Moderate | Van der Velden 2014 |

**Usage note:** Most values are **cradle-to-gate** (include raw material embodied energy). "Process only" data (polymerization energy without monomer embodied energy) rarely reported in literature.

---

## Appendix B: Glossary of terms

| Term | Definition |
|---|---|
| **AII Factor** | Average Incremental Intensity: material-specific adjustment factor for energy consumption relative to baseline (PET = 1.00) |
| **CED** | Cumulative Energy Demand: total primary energy including upstream processes (MJ) |
| **Dtex** | Decitex: mass in grams per 10,000 meters of yarn (direct yarn count system) |
| **FDY** | Fully Drawn Yarn: high molecular orientation, ready for weaving/knitting |
| **Gate-to-gate** | System boundary: polymer granules -> yarn (spinning process only) |
| **Cradle-to-gate** | System boundary: monomers -> polymer -> yarn (full upstream) |
| **POY** | Partially Oriented Yarn: low molecular orientation, requires further drawing or direct use in DTY production |
| **SEC** | Specific Energy Consumption: energy per unit mass (kWh/kg or MJ/kg) |
| **DTY** | Draw Textured Yarn: texturized yarn for stretch and bulk applications |
| **Nm** | Numero Metrique: length in meters per gram of yarn (indirect yarn count system) |
| **Spinneret** | Die with many small holes for extruding polymer into filaments |

---

*Version 1.0 | February 2026*
*Methodological specification for synthetic filament yarn spinning inventory model*
