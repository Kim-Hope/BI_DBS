# Business Dynamics Statistics (BDS) Executive Dashboard

##  Project Overview
This Power BI project delivers an interactive executive dashboard using the **Business Dynamics Statistics (BDS)** datasets from the U.S. Census Bureau. The dashboard provides insights into business dynamics at national and state levels, segmented by sector, firm size, and firm age. It is designed to support decision-making by visualizing key metrics such as firm counts, employment, job creation/destruction, and establishment entry/exit rates.

## Dataset Description
The Business Dynamics Statistics (BDS) is a public-use data set that provides annual aggregate measures of employer business dynamics, including establishment openings and closings, firm startups and shutdowns, and job creation and destruction. The data describe the evolution of the U.S. economy at the national, state, county, and metropolitan area levels.

##  Data Sources
U.S. Census Bureau. (2026). Business Dynamics Statistics (BDS) Explorer. BDS Explorer. Retrieved from https://bds.explorer.ces.census.gov

| File Name | Grain | Key Fields |
|-----------|-------|------------|
| `state_by_sector.csv` | State + Sector | `year`, `st`, `sector` |
| `state.csv` | State only | `year`, `st` |
| `sector.csv` | National by sector | `year`, `sector` |
| `firm_size.csv` | National by firm size | `year`, `fsize` |
| `firm_age.csv` | National by firm age | `year`, `fage` |

Each file contains metrics on firms, establishments, employment, job creation/destruction, and establishment entry/exit.

##  Data Model
A star schema was implemented in Power BI to ensure efficient querying and intuitive filtering:

- **Fact Tables**:
  - `Fact_StateSector` – most granular, combines state and sector dimensions.
  - `Fact_State` – state-level aggregates.
  - `Fact_Sector` – national-level sector aggregates.
  - `Fact_FirmSize` – aggregates by firm size.
  - `Fact_FirmAge` – aggregates by firm age.

- **Dimension Tables**:
  - `DimDate` – unique years.
  - `DimState` – unique state codes.
  - `DimSector` – unique sector codes.
  - `DimFirmSize` – unique firm size categories.
  - `DimFirmAge` – unique firm age categories.

Relationships are one-to-many from dimensions to fact tables with single-direction cross-filtering, ensuring a clean and performant model.

##  Dashboard Pages

### 1. Executive Overview
- **KPIs**: Total Firms, Total Employment, Net Job Creation, Job Creation Rate, Job Destruction Rate (card visuals).
- **Trend Analysis**: Line chart of Job Creation vs Destruction over time.
- **Sector Distribution**: Donut chart of firms by sector.
- **Slicers**: Year, Sector, State for interactive filtering.

### 2. Sector & State Deep Dive
- **Top Sectors Bar Chart**: Employment by sector.
- **Sector Trends**: Line chart of employment trends by sector over time.
- **State Metrics Table**: State-level KPIs.

### 3. Firm Demographics
- **Firms by Size**: Bar chart of firm counts by size category.
- **Firms by Age**: Bar chart of firm counts by age category.
- **Job Creation by Size**: Line chart of job creation rate over time by firm size.
- **Drill-down into Employment** – Decomposition tree; total employment per sector.


##  Publishing & Access
 **Public Dashboard Link**:  
https://app.powerbi.com/view?r=eyJrIjoiMmY4YWNkN2ItYzUyNy00ZWQ3LTk2YWQtYWM0ZmUzOGE3N2ViIiwidCI6IjE2ZDgzZWU2LTI1NGEtNDY5ZC1hNmNjLTU0ZTJjYTIzMTNlNyIsImMiOjh9 


##  Screenshots
Screenshots of the data model, relationship configuration, each dashboard page, and publishing steps are included in the `Screenshots.pdf`.
