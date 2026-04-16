# Collective Shoe Assembly — Documentation

## 1. Process description

This dataset models the assembly of women's boots with PU/microfiber upper and TPR/EVA/rubber outsole. The assembly process consists of three sequential operations:

### 1.1 Cutting

Fabric cutting with oil paint printing for pattern marking. The cutting step has an input/output ratio of 1.038, meaning 1.038 kg of input material is needed per 1 kg of cut output, with 0.038 kg of textile waste generated.

### 1.2 Stitching

Upper stitching with glue application. The glue used is **163N stitching glue**, a natural rubber seal dissolved in organic solvents. The stitching step has an input/output ratio of 1.006.

### 1.3 Lasting

Final assembly step including adhesive application, primer treatment, and surface cleaning. Key chemicals:

- **BW553 primer**: Ethyl acetate + acetone + PU foam + solvent blend (available in IT, CN, GLO variants)
- **Shoe surface cleaner**: Xylene + butanone (MEK proxy) + acetone
- **PU adhesive**: Polyurethane-based adhesive from ecoinvent market

The lasting step has an input/output ratio of 1.004 and is the dominant contributor to climate change impact (82–86% of total GHG across all scenarios).

## 2. System boundary

### Included

- Electricity consumption at each assembly step
- Chemical inputs: adhesives, primers, solvents, oil paint
- Waste treatment: textile waste sent to market for waste yarn and waste textile

### Excluded

- Physical materials (upper fabric, outsole components)
- Packaging materials
- Transport to customer
- Capital goods (machines, building)

## 3. Data sources

- **Primary data**: Collected from a shoe manufacturer in Wenzhou, China by Carbonfact
- **Chemical compositions**: Modeled from Material Safety Data Sheets (MSDS/SDS) provided by chemical suppliers
- **Background database**: ecoinvent 3.12 (cut-off system model)

## 4. Electricity scenarios

Three electricity scenarios are provided to enable geography-specific assessments:

| Scenario | Electricity market | Context |
|----------|-------------------|---------|
| CN | market for electricity, medium voltage (CN) | Primary data origin — Chinese manufacturer |
| GLO | market group for electricity, medium voltage (GLO) | Global average for generic assessments |
| IT | market for electricity, medium voltage (IT) | Italy scenario for European context |

All other inputs (chemicals, waste) remain identical across scenarios. The electricity market is the sole differentiating parameter.

## 5. Chemical sub-processes

Four chemical sub-processes are modeled as foreground activities based on MSDS/SDS compositions:

| Chemical | Application | Key components |
|----------|------------|----------------|
| 163N stitching glue | Upper stitching | Natural rubber seal + organic solvent |
| BW553 primer | Surface preparation | Ethyl acetate + acetone + PU foam + solvent |
| Shoe surface cleaner | Pre-lasting cleaning | Xylene + butanone (MEK) + acetone |
| Oil paint for print | Cutting pattern marking | PP resin + cyclohexanone + organic pigment + silicone |

## 6. Impact assessment

All 16 EF 3.1 impact indicators are calculated. Key findings:

- **Lasting dominates GHG** (82–86%) due to PU adhesive, primer chemicals, and electricity
- **CN shows highest GHG** (1.43 kgCO2eq/kg) due to coal-heavy electricity grid
- **IT shows lowest GHG** (0.86 kgCO2eq/kg) due to lower-carbon electricity mix
- **Material loss rate** is identical across scenarios (1.049) as wastage is physical, not geography-dependent
