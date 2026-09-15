# CAP Transport Dashboard

R Shiny dashboard tracking Ireland's Climate Action Plan 2025 transport-sector
targets against observed CSO data, structured around the Avoid–Shift–Improve
(ASI) framework.

## Running it

```r
shiny::runApp("CAP_Transport_Dashboard.txt")
```

(Rename the file to `app.R` first if you want to launch it by opening the
folder in RStudio and clicking Run App.)

## Requirements

- R 4.3+ (built and tested on R 4.3.2)
- Internet access to `ws.cso.ie` — **all data is pulled live from the CSO
  PxStat API on every app start, with no hardcoded fallback.** If a table is
  temporarily unavailable or a CSO table code is retired/renamed, the app
  will fail to start rather than show stale or fabricated numbers. Check the
  table codes below against [data.cso.ie](https://data.cso.ie) if that
  happens.

| Package        | Version tested |
|----------------|----------------|
| shiny          | 1.11.1         |
| shinydashboard | 0.7.3          |
| plotly         | 4.11.0         |
| dplyr          | 1.1.4          |
| tidyr          | 1.3.1          |
| scales         | 1.4.0          |
| csodata        | 1.5.0          |

Install with:

```r
install.packages(c("shiny", "shinydashboard", "plotly", "dplyr", "tidyr", "scales", "csodata"))
```

## CSO PxStat tables used

| Code             | Table                                                         |
|------------------|----------------------------------------------------------------|
| SEI06            | Final energy consumption by sector (SEAI)                     |
| QES20            | Persons in employment — extent working at home                |
| THA10            | Road traffic volumes by type of vehicle                       |
| TFQ01            | Road freight transport activity                                |
| TFA19            | Annual road freight by type of goods (NST 2007)                |
| TFA01            | Annual road freight by main use of vehicle                     |
| TOA16            | Scheduled bus passenger services                                |
| THA24            | Passenger journeys by public transport (annual)                |
| TOA11            | Luas passenger numbers                                          |
| TOA08            | Dublin Bikes journeys                                           |
| TOA22            | Regional city bike-share journeys (Cork, Galway, Limerick, Waterford) |
| SAP2022T11T3ED   | Census 2022 — journey time to work                              |
| THA17            | Vehicle licensing statistics (vehicles, km travelled, fleet by fuel) |
| PEA08            | Population estimates                                            |
| TAA04 / TAA06    | Aviation activity at Irish airports (2016–2019 / 2020–2024)     |
| TAA05            | Passengers at Irish airports                                    |
| BIIESGE03        | National GHG emissions by sector                                 |
| SAP2022T11T1ED   | Census 2022 — means of travel to work                            |
| TEM27            | New/secondhand private cars by fuel type                         |
| TEA01            | Vehicles licensed for the first time (annual, 1997–)             |

## Known limitations

- No projections or forecasts — every chart shows observed data only; target
  lines are drawn from published CAP 2025 policy figures.
- 2020–2021 figures are materially affected by pandemic restrictions.
- THA24 only covers rail from 2020 onwards.
