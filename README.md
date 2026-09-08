## Methodology

### Life-Cycle Assessment Framework

The calculator applies a life-cycle assessment approach based on ISO 14040:2006 and the greenhouse gas accounting guidelines for land transportation enterprises issued by China’s National Development and Reform Commission.

The assessment covers three life-cycle stages:

- **Construction (`c`):** infrastructure construction, vehicle manufacturing, equipment, construction electricity, and material transportation
- **Operation (`o`):** electricity consumed by vehicles, stations, control systems, and maintenance facilities, together with maintenance materials
- **Recycling (`r`):** emissions from dismantling, waste processing, and transportation, offset by avoided emissions from recovered materials

The inventory includes direct and indirect emissions of carbon dioxide (`CO2`), methane (`CH4`), and nitrous oxide (`N2O`). Emissions are converted to carbon dioxide equivalents using 100-year global warming potentials.

### Total Life-Cycle Emissions

Total life-cycle greenhouse gas emissions are calculated by summing all emission sources across the construction, operation, and recycling stages:

```text
E_GHG,LCA = Σ_i (E_combustion,i + E_electricity,i + E_heat,i
                + E_materials,i + E_equipment,i)
```

where:

- `E_GHG,LCA` = total life-cycle greenhouse gas emissions, in `tCO2e` per project
- `i` = life-cycle stage: construction (`c`), operation (`o`), or recycling (`r`)
- `E_combustion,i` = emissions from fossil-fuel combustion in stage `i`
- `E_electricity,i` = indirect emissions from electricity consumption in stage `i`
- `E_heat,i` = indirect emissions from purchased heat in stage `i`
- `E_materials,i` = embodied emissions from materials used in stage `i`
- `E_equipment,i` = embodied emissions from specialized equipment used in stage `i`

No purchased heat was identified for the suspended-monorail system examined in the source report. Therefore, `E_heat,i` is set to zero in the current calculation.

### Fuel-Combustion Emissions

Emissions from fossil-fuel combustion are calculated as:

```text
E_combustion =
Σ_i Σ_k AD_fuel(i,k) ×
[EF_CO2(i,k) + EF_CH4(i,k) × GWP_CH4 + EF_N2O(i,k) × GWP_N2O]
```

where:

- `AD_fuel(i,k)` = consumption of fuel type `k` during stage `i`
- `EF_CO2(i,k)` = CO2 emission factor for fuel type `k`
- `EF_CH4(i,k)` = CH4 emission factor for fuel type `k`
- `EF_N2O(i,k)` = N2O emission factor for fuel type `k`
- `GWP_CH4` and `GWP_N2O` = 100-year global warming potentials for CH4 and N2O

This category includes fuels consumed during construction, dismantling, and material transportation.

### Electricity-Related Emissions

Indirect emissions from electricity consumption are calculated as:

```text
E_electricity =
Σ_i AD_electricity(i) ×
[EF_electricity,CO2
 + EF_electricity,CH4 × GWP_CH4
 + EF_electricity,N2O × GWP_N2O]
```

where:

- `AD_electricity(i)` = electricity consumed during stage `i`, in MWh
- `EF_electricity,CO2` = grid CO2 emission factor
- `EF_electricity,CH4` = grid CH4 emission factor
- `EF_electricity,N2O` = grid N2O emission factor

Operational electricity includes vehicle traction, station operation, control and management systems, maintenance facilities, and other auxiliary electricity consumption.

### Material Emissions

Embodied emissions from construction and maintenance materials are calculated as:

```text
E_materials =
Σ_i Σ_m AD_material(i,m) ×
[EF_material,CO2(i,m)
 + EF_material,CH4(i,m) × GWP_CH4
 + EF_material,N2O(i,m) × GWP_N2O]
```

where:

- `AD_material(i,m)` = quantity of material `m` used during stage `i`
- `EF_material,CO2(i,m)` = CO2 emission factor for material `m`
- `EF_material,CH4(i,m)` = CH4 emission factor for material `m`
- `EF_material,N2O(i,m)` = N2O emission factor for material `m`

Materials include steel, concrete, cement, aluminum, copper, glass, cables, and other materials used in the guideway, supporting structures, stations, vehicles, power systems, control systems, and maintenance base.

### Equipment Emissions

When equipment-specific emission factors are available, equipment emissions are calculated as:

```text
E_equipment =
Σ_i Σ_w AD_equipment(i,w) ×
[EF_equipment,CO2(i,w)
 + EF_equipment,CH4(i,w) × GWP_CH4
 + EF_equipment,N2O(i,w) × GWP_N2O]
```

where:

- `AD_equipment(i,w)` = quantity or mass of equipment type `w` used during stage `i`
- `EF_equipment,CO2(i,w)` = CO2 emission factor for equipment type `w`
- `EF_equipment,CH4(i,w)` = CH4 emission factor for equipment type `w`
- `EF_equipment,N2O(i,w)` = N2O emission factor for equipment type `w`

When an equipment-specific emission factor is unavailable, emissions are estimated from the quantities and emission factors of the equipment’s principal constituent materials.

### End-of-Life Material Recovery

The recycling stage accounts for the recovery of materials such as steel, aluminum, and copper. Emissions from dismantling, processing, and transportation are counted as positive emissions. Avoided emissions from recovered materials are deducted as recycling credits.

```text
E_net,LCA = E_construction + E_operation
            + E_EOL,burden - E_recovery,credit
```

where:

- `E_EOL,burden` = emissions from dismantling, waste processing, and transportation
- `E_recovery,credit` = avoided emissions resulting from material recovery
- `E_net,LCA` = net life-cycle greenhouse gas emissions after recycling credits

### Passenger-Kilometre Carbon Intensity

The principal functional unit is total life-cycle emissions, reported in `tCO2e per project`. For comparison with buses, metro systems, and other transportation modes, the calculator also reports emissions per passenger-kilometre:

```text
CI_passenger-km =
(E_net,LCA × 1,000,000) ÷
(P_annual × D_trip × Y)
```

where:

- `CI_passenger-km` = carbon intensity in `gCO2e/passenger-km`
- `E_net,LCA` = net life-cycle emissions in `tCO2e`
- `P_annual` = annual number of passenger trips
- `D_trip` = average passenger-trip distance in kilometres
- `Y` = operating lifetime in years
- `1,000,000` = conversion from tonnes to grams

Using a common passenger-kilometre functional unit allows the suspended monorail results to be compared with diesel buses, electric buses, conventional metro systems, and other public transportation modes.

### Emission Factors and Global Warming Potentials

The source reports use emission factors from Ecoinvent 3.0 and the European Life Cycle Database. China-specific factors are prioritized where available, followed by global or other representative regional averages.

The original calculations use the following IPCC 2013 GWP 100-year values:

- `CO2`: 1
- `CH4`: 30.5
- `N2O`: 265

These values are provided as workbook defaults and may be updated when newer, geographically representative, or project-specific factors are available.

Results depend on the selected activity data, emission factors, material-recovery rates, electricity mix, passenger demand, average trip distance, and operating lifetime.
