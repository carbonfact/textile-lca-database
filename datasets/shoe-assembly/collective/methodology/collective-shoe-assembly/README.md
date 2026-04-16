# Collective Shoe Assembly — Methodology

## Process description

Women's boots assembly covering three sequential operations:

1. **Cutting** (IOR = 1.038): Fabric cutting with oil paint printing for pattern marking
2. **Stitching** (IOR = 1.006): Upper stitching with 163N glue application (natural rubber seal in organic solvent)
3. **Lasting** (IOR = 1.004): Final assembly using PU adhesive (BW553 primer: ethyl acetate + acetone + PU foam), surface cleaner (xylene + butanone + acetone)

## System boundary

- **Included**: Electricity, chemical inputs (adhesives, primers, solvents, paints), waste treatment (textile waste)
- **Excluded**: Physical materials (upper fabric, outsole), packaging, transport to customer
- **Background database**: ecoinvent 3.12 (cut-off)

## Key parameters

| Parameter | Value |
|-----------|-------|
| Functional unit | 1 kg assembled footwear |
| Aggregated loss rate | 1.049 (= 1.038 × 1.006 × 1.004) |
| Electricity scenarios | CN (China grid), GLO (global average), IT (Italy grid) |
| Data source | Primary data from a Wenzhou (China) shoe manufacturer |
| Chemical modeling | MSDS/SDS-based compositions |

## Electricity scenarios

The CN scenario reflects the primary data origin (Chinese manufacturer). GLO and IT scenarios substitute electricity markets while keeping all other inputs identical, enabling geography-specific assessments.

## Documentation

- [documentation.md](documentation.md) — Detailed process documentation
- [lci.md](lci.md) — Lifecycle inventory details
