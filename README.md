* Last updated: 20th June, 2025
* Author: Thuy Ngo
* GitHub repo: <https://github.com/linhngo66/rent-and-security-in-melb-suburbs>

## About this analysis

**Are we paying more rent for better security in Melbourne?**

This project investigates the relationship between rental prices and crime rates across Melbourne suburbs, with the aim of answering whether we pay more for better safety. The analysis draws on publicly available datasets and transforms them to estimate suburb-level incident rates and rental prices in 2024.

---

## Data origin

This analysis uses publicly available datasets from the following sources:

| Dataset                             | Source                                | Purpose                                                  |
| ----------------------------------- | ------------------------------------- | -------------------------------------------------------- |
| 2021 Census GeoPackages - G01       | Australian Bureau of Statistics (ABS) | Population by suburb (for calculating crime rate)        |
| 2021 Census GeoPackages - G02       | ABS                                   | Median weekly rent and suburb geospatial boundaries      |
| Recorded Criminal Incidents         | Crime Statistics Agency (CSA)         | Suburb-level crime statistics                            |
| Consumer Price Index (CPI)          | ABS                                   | Used to estimate rental growth between 2021 and 2024     |
| Estimated Resident Population (ERP) | ABS                                   | Used to estimate population growth between 2021 and 2024 |
| Region-to-LGA Mapping               | The State of Victoria Department of Environment, Land, Water and Planning (DELWP)             | Categorize suburbs by Melbourne regions                  |

---

## License of data sources

- **ABS data**: Licensed under [Creative Commons Attribution 4.0 International](https://creativecommons.org/licenses/by/4.0/)
- **CSA data**: Licensed under [Creative Commons Attribution 3.0 Australia](https://creativecommons.org/licenses/by/3.0/au/)
- **DELWP map (manually digitized)**: Usage falls under fair use for analysis and education.

---

## File structure

```text
.
├── data
│   ├── raw/                                   # Original ABS and CSA source files
│   │   ├── Geopackage_2021_G01_VIC_GDA2020/   # 2021 Census GeoPackages - G01
│   │   ├── Geopackage_2021_G02_VIC_GDA2020/   # 2021 Census GeoPackages - G02
│   │   ├── abs-cpi-by-capital city.xlsx       # CPI
│   │   ├── abs-population.xlsx                # ERP
│   │   └── Data_Tables_LGA_Criminal_Incidents_Year_Ending_December_2024.xlsx  # CSA 
│   └── processed/                # Transformed and cleaned data
│       ├── census-csa-metro.gpkg              # Combined Census, CSA and geospatial
│       ├── data_dictionary.xlsx               # Data dictionary
│       ├── metro-lga.csv                      # Map LGAs to their metropolitan region
│       ├── region-boundary.gpkg               # Geospatial of metropolitan regions     
│       └── suburb-lga-dict.csv                # Dictionary of suburb and LGA
├── assignment4_35776064.qmd                   # Main report
├── Assignment 4.Rproj
└── README.md                                  # Project documentation  
```

---

## Data transformation

The analysis includes the following transformations:

- **2021 rental prices** were adjusted to 2024 values using CPI growth.
- **2021 population figures** were scaled to 2024 estimates using ERP growth.
- **Crime rate** was calculated as incidents per 100 residents.
- **Suburb names** were harmonized across Census and CSA datasets.
- **Outliers and industrial suburbs** were flagged but retained to reflect true values.

---

## Usage of this analysis 

This analysis can be used to:

- Inform **urban planning and policy** by identifying safety-affordability trade-offs
- Help **renters and buyers** understand the relative value of different suburbs

---

## Data Limitation

- Rental and population data are from 2021 and adjusted to 2024 using statewide averages.
- Crime data is only what is reported and recorded by police, excluding unreported incidents.
- Some suburbs span multiple LGAs; this was simplified to avoid duplication.
- CPI and ERP, used for 2024 adjustments, are not suburb-specific, which may introduce local inaccuracy.
- Industrial and commercial zones may have inflated crime rates due to low residential population.

---

## License of This Report

This report is licensed under the **Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)** license. You may share and adapt the work for non-commercial purposes with attribution.

---

## Future Direction

- Introduce other factors influencing rental prices, such as public transport accessibility, distance to key points of interest, housing variables (e.g., dwelling types)
- Build an app where users can weigh the importance of different factors and receive recommendations on suburbs to live in
