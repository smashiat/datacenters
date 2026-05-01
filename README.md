# Data Centers & Environmental Justice: A Computational Analysis

## Research Question

Are U.S. data centers disproportionately sited in communities that already bear higher environmental and socioeconomic burdens?

## Overview

Data centers are the physical backbone of the internet — and they are largely invisible to the people who live near them. A single hyperscale facility can consume 50–100 MW of electricity and millions of gallons of water per year. This analysis uses EPA EJScreen environmental justice indicators to examine whether data center locations correlate with elevated demographic and environmental burden relative to the national baseline.

## Key Findings

- Data center sites score at the **62nd national percentile** for EJ Composite Index on average — 12 points above the national median
- Communities near data centers score at the **65th percentile** for PM2.5 concentration
- **Miami, Atlanta, and New York Metro (NJ)** show the highest EJ burden among major data center clusters
- Facilities built during the **AI buildout era (2019–2024)** show higher EJ burden scores than earlier cohorts
- Hyperscale facilities (operated by major tech companies) show the widest distribution of EJ burden, appearing in both low- and high-burden tracts

## Data Sources

| Dataset | Source | Description |
|---|---|---|
| Data Center Locations | CBRE 2024 Data Center Trends, datacentermap.com | Facility locations, capacity (MW), operator type |
| EJ Indicators | EPA EJScreen | National percentile scores for demographics and environmental hazards |

> **Note:** This notebook uses modeled data based on published cluster-level statistics. See the methodology section for instructions on substituting real scraped data via the EJScreen REST API and Census Geocoder.

## Visualizations

| Figure | Description |
|---|---|
| `fig1_capacity_by_cluster.png` | Total installed capacity by metro cluster |
| `fig2_growth_by_type.png` | Capacity growth over time by operator type |
| `fig3_ej_burden_vs_baseline.png` | Mean EJ indicators at DC sites vs. national median |
| `fig4_ej_by_cluster.png` | EJ burden breakdown by metro region |
| `fig5_capacity_vs_ej.png` | Scatter: facility size vs. EJ burden |
| `fig6_ej_by_operator.png` | EJ burden distribution by operator type (violin plot) |
| `fig7_water_vs_ej.png` | Water consumption vs. EJ burden by cluster |
| `fig8_ej_by_era.png` | EJ burden of early vs. AI-era facilities |


## Methodology Notes

- **EJScreen percentiles** are national — a score of 70 means that tract has more burden than 70% of all U.S. tracts
- **Statistical test:** One-sample t-tests against null hypothesis mean = 50 (national median)
- **Water consumption** modeled from published PUE and WUE ranges (1.5–4.5 gallons/MWh)
- **Limitations:** Tract-level averages may obscure block-level variation; causality not established

## Next Steps

1. Scrape real facility data from datacentermap.com using `requests` + `BeautifulSoup`
2. Pull actual EJScreen scores via REST API for geocoded coordinates
3. Incorporate grid data to assess whether DC-driven demand raises local electricity rates
4. Build an interactive Folium/Leaflet map for public exploration


