## Methodology

### Life-Cycle Assessment Framework

The calculator applies a life-cycle assessment approach based on ISO 14040:2006 and the greenhouse gas accounting guidelines for land transportation enterprises issued by China’s National Development and Reform Commission.

The assessment covers three life-cycle stages:

* Construction (`c`): infrastructure construction, vehicle manufacturing, equipment, electricity consumption, and material transportation
* Operation (`o`): electricity consumed by vehicles, stations, control systems, and maintenance facilities, together with maintenance materials
* Recycling (`r`): emissions from dismantling and transportation, offset by avoided emissions from recovered materials

The inventory includes direct and indirect emissions of carbon dioxide (`CO₂`), methane (`CH₄`), and nitrous oxide (`N₂O`). Emissions are converted to carbon dioxide equivalents using 100-year global warming potentials.

### Total Life-Cycle Emissions

Total life-cycle greenhouse gas emissions are calculated by summing all emission sources across the three life-cycle stages:

$$
E_{\mathrm{GHG,LCA}}
=
\sum_i \sum_j E_{\mathrm{GHG}}(i,j)
=
\sum_i
\left(
E_{\mathrm{fuel},i}
+
E_{\mathrm{electricity},i}
+
E_{\mathrm{heat},i}
+
E_{\mathrm{materials},i}
+
E_{\mathrm{equipment},i}
\right)
$$

where:

* $E_{\mathrm{GHG,LCA}}$ is the total life-cycle greenhouse gas emissions in `tCO₂e` per project;
* $i$ represents construction (`c`), operation (`o`), or recycling (`r`);
* $j$ represents the emission-source category;
* $E_{\mathrm{fuel},i}$ is the emissions from fossil-fuel consumption in stage $i$;
* $E_{\mathrm{electricity},i}$ is the indirect emissions from electricity consumption;
* $E_{\mathrm{heat},i}$ is the indirect emissions from purchased heat;
* $E_{\mathrm{materials},i}$ is the embodied emissions of materials; and
* $E_{\mathrm{equipment},i}$ is the embodied emissions of specialized equipment.

No purchased heat was identified for the suspended-monorail case examined in the source report; therefore, $E_{\mathrm{heat},i}$ is set to zero in the current calculation. Recycling benefits are recorded as negative emissions and deducted from the construction and operation emissions.

### Fuel-Related Emissions

Emissions associated with fossil-fuel consumption are calculated as:

$$
E_{\mathrm{fuel}}
=
\sum_i \sum_k
AD_{\mathrm{fuel},i}^{k}
\left(
EF_{\mathrm{fuel-CO_2},i}^{k}
+
EF_{\mathrm{fuel-CH_4},i}^{k} \times GWP_{\mathrm{CH_4}}
+
EF_{\mathrm{fuel-N_2O},i}^{k} \times GWP_{\mathrm{N_2O}}
\right)
$$

where $AD_{\mathrm{fuel},i}^{k}$ is the consumption of fuel type $k$ in stage $i$, and $EF$ represents the corresponding gas-specific emission factor. This category includes fuels consumed during construction, dismantling, and material transportation.

### Electricity-Related Emissions

Indirect emissions from electricity consumption are calculated as:

$$
E_{\mathrm{electricity}}
=
\sum_i
AD_{\mathrm{electricity},i}
\left(
EF_{\mathrm{electricity-CO_2}}
+
EF_{\mathrm{electricity-CH_4}} \times GWP_{\mathrm{CH_4}}
+
EF_{\mathrm{electricity-N_2O}} \times GWP_{\mathrm{N_2O}}
\right)
$$

where $AD_{\mathrm{electricity},i}$ is the electricity consumed during stage $i$, measured in MWh, and $EF_{\mathrm{electricity}}$ represents the average grid emission factor for each greenhouse gas.

Operational electricity includes vehicle traction, station operation, control and management systems, maintenance facilities, and other auxiliary electricity use.

### Material Emissions

Embodied emissions from construction and maintenance materials are calculated as:

$$
E_{\mathrm{materials}}
=
\sum_i \sum_m
AD_{\mathrm{materials},i}^{m}
\left(
EF_{\mathrm{materials-CO_2},i}^{m}
+
EF_{\mathrm{materials-CH_4},i}^{m} \times GWP_{\mathrm{CH_4}}
+
EF_{\mathrm{materials-N_2O},i}^{m} \times GWP_{\mathrm{N_2O}}
\right)
$$

where $AD_{\mathrm{materials},i}^{m}$ is the quantity of material $m$ used in stage $i$, and $EF_{\mathrm{materials},i}^{m}$ is its gas-specific life-cycle emission factor.

Materials include steel, concrete, cement, aluminum, copper, glass, cables, and other materials used in the guideway, supporting structures, stations, vehicles, power systems, control systems, and maintenance base.

### Equipment Emissions

Where equipment-specific emission factors are available, equipment emissions are calculated as:

$$
E_{\mathrm{equipment}}
=
\sum_i \sum_w
AD_{\mathrm{equipment},i}^{w}
\left(
EF_{\mathrm{equipment-CO_2},i}^{w}
+
EF_{\mathrm{equipment-CH_4},i}^{w} \times GWP_{\mathrm{CH_4}}
+
EF_{\mathrm{equipment-N_2O},i}^{w} \times GWP_{\mathrm{N_2O}}
\right)
$$

where $AD_{\mathrm{equipment},i}^{w}$ is the quantity or mass of equipment type $w$. When an equipment-specific factor is unavailable, emissions are estimated from the quantities and emission factors of its principal constituent materials.

### End-of-Life Material Recovery

The recycling stage accounts for the recovery of materials such as steel, aluminum, and copper. Avoided emissions from recovered materials are treated as negative values, while emissions from dismantling, waste processing, and transportation remain positive.

Therefore:

$$
E_{\mathrm{net,LCA}}
=
E_{\mathrm{construction}}
+
E_{\mathrm{operation}}
+
E_{\mathrm{recycling}}
$$

where $E_{\mathrm{recycling}}$ may be negative when avoided production emissions exceed dismantling and transportation emissions.

### Passenger-Kilometre Emissions

The principal functional unit is total emissions over the project life cycle, reported in `tCO₂e per project`. To compare the suspended monorail with buses and metro systems, the calculator also reports emissions per passenger-kilometre:

$$
CI_{\mathrm{passenger-km}}
=
\frac{E_{\mathrm{net,LCA}} \times 10^6}
{P_{\mathrm{annual}} \times D_{\mathrm{trip}} \times Y}
$$

where:

* $CI_{\mathrm{passenger-km}}$ is the carbon intensity in `gCO₂e/passenger-km`;
* $E_{\mathrm{net,LCA}}$ is the net life-cycle emissions in `tCO₂e`;
* $P_{\mathrm{annual}}$ is the annual number of passenger trips;
* $D_{\mathrm{trip}}$ is the average passenger-trip distance in kilometres; and
* $Y$ is the operating lifetime in years.

Using a common passenger-kilometre functional unit allows the results to be compared with diesel buses, electric buses, conventional metro systems, and other public transportation modes.

### Emission Factors and Global Warming Potentials

The source reports use emission factors from Ecoinvent 3.0 and the European Life Cycle Database. China-specific factors are prioritized where available, followed by global or other representative regional averages.

The original calculations apply IPCC 2013 GWP 100-year values:

* `CO₂`: 1
* `CH₄`: 30.5
* `N₂O`: 265

These values are provided as defaults in the workbook and may be updated when newer, geographically representative, or project-specific emission factors are available. All calculation results depend on the selected activity data, emission factors, recovery rates, electricity mix, passenger demand, trip distance, and operating lifetime.
