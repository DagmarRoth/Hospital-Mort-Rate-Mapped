# The South is Suffering: Hospital Mortality Across America's Bible Belt

## Overview

This project visualizes the geographic distribution of hospital mortality rates across the United States, with particular focus on disparities in America's Bible Belt region. Using publicly available data from the Centers for Medicare & Medicaid Services (CMS), the analysis reveals stark regional patterns in patient outcomes and highlights where healthcare challenges are most severe.

## Key Findings

**Geographic Concentration**: Of the ten ZIP codes with the highest hospital mortality rates in the United States, four are located in Mississippi alone. All ten are concentrated in the South, indicating a systemic regional healthcare crisis rather than random variation.

**State-Level Disparities**: Mississippi, Louisiana, and Alabama lead in mortality rates at 4.86%, 4.53%, and 4.52% respectively—all significantly above the national average of 4.22%. These disparities persist across different hospital types.

**Within-State Variation**: Southern and western regions within Bible Belt states consistently demonstrate higher mortality rates than their northern counterparts, suggesting uneven distribution of healthcare resources even within state borders.

**Structural Drivers**: The concentration reflects deeper structural conditions—economic inequality, under-resourced medical facilities, rural hospital closures, staffing shortages, and barriers to preventive care—that shape health outcomes long before hospitalization.

## Data Collection Process

This analysis utilizes the **Hybrid Hospital-Wide All-Cause Risk Standardized Mortality Rate** from the CMS Complications and Deaths Dataset:

- **Source**: [Centers for Medicare & Medicaid Services (CMS) Complications and Deaths Dataset](https://www.cms.gov/)
- **Coverage**: 4,791 hospitals across 3,752 ZIP codes and 55 states/territories
- **Measure**: Hybrid Hospital-Wide All-Cause Risk Standardized Mortality Rate (Measure ID: Hybrid_HWM)
- **Population**: Medicare patients—reflecting populations that already face elevated health risks
- **Data Processing**: County-level data aggregated into state-level regions (North, South, East, West, Central, and corner regions) for granular geographic analysis

The dataset captures real mortality variation across the nation's medical system, though it does not represent the full privately insured population or every hospitalization.

## Data Analysis Process

### 1. Data Loading and Filtering
- Loaded the CMS Complications and Deaths dataset (95,820 rows)
- Filtered for the Hybrid Hospital-Wide All-Cause Risk Standardized Mortality Rate measure
- Removed null values and incomplete records
- Aggregated hospital-level data to ZIP code and state levels

### 2. Geographic Aggregation
- Aggregated hospital mortality rates by state
- Extracted county centroids from GeoJSON polygon coordinates
- Calculated state-level min/max latitude/longitude boundaries
- Normalized county positions as geographic quartiles

### 3. Regional Classification Algorithm
- Divided each state into regions (North, South, East, West, Central) based on geographic coordinates
- Used a coordinate-based quartile positioning system to classify counties without requiring external FIPS code matching
- Aggregated mortality metrics by region within each state

### 4. Visualization Generation
- Created interactive Plotly choropleth maps showing state-regions by mortality rate
- Generated county-level bubble maps highlighting top mortality areas
- Built bar charts ranking counties by mortality rate with 15+ county threshold
- Embedded visualizations as interactive HTML iframes in the main site

## Skills and Growth

### New Technical Skills Developed
- **Geospatial Data Analysis**: Learned to work with GeoJSON polygons, extract centroids, and calculate geographic position metrics
- **Advanced Pandas Operations**: Mastered complex groupby aggregations, multi-level data pivoting, and conditional filtering for large healthcare datasets
- **Interactive Visualization Design**: Transitioned from static maps (Folium) to dynamic, interactive visualizations (Plotly) with hover annotations and customizable color scales
- **Geographic Coordinate Mathematics**: Implemented quartile-based region classification without external dependencies—solving coordinate normalization and regional boundary definition challenges
- **Web Design & Deployment**: Created a professional, data-journalism-style website and deployed it to GitHub Pages with responsive design principles
- **Git Workflow for Data Projects**: Managed version control for large media files, consolidated commits, and maintained clean deployment history

### Problem-Solving Approaches
- **Pivoted data scope**: Recognized that state-level aggregation was more practical than ZIP-code geocoding when facing API rate limiting
- **Chose appropriate tools**: Evaluated multiple visualization libraries (Folium, Plotly) and selected tools based on technical constraints
- **Designed algorithmic solutions**: Built a coordinate-based region classification system when external data sources proved unreliable
- **Iterative design refinement**: Worked through multiple website layout and styling iterations based on user feedback to achieve professional, serious presentation

## Limitations and Future Work

### Challenges Encountered
- **Geocoding Limitations**: Nominatim geocoding API rate limits prevented ZIP-code-level density mapping; required pivot to state-level analysis
- **FIPS Code Matching**: Attempted county FIPS code matching through external sources (GitHub, Census.gov) but encountered HTTP errors and data inconsistencies; solved through geographic coordinate-based classification instead
- **Large Media Files**: Initial 293MB video file caused Git push timeouts; resolved by sourcing a smaller 27MB version
- **Medicare-Only Data**: CMS dataset represents Medicare population (older, typically sicker) and does not capture full privately insured population or complete national picture

### Future Enhancements (With Additional Time/Skills)
1. **Full Population Coverage**: Integrate commercial insurance data and Medicaid datasets to create a more comprehensive national picture beyond Medicare-only analysis
2. **Temporal Analysis**: Add time-series visualizations showing mortality trend changes over multiple years to identify improving/worsening regions
3. **Causality Analysis**: Correlate mortality data with socioeconomic indicators (poverty rates, education levels, insurance coverage, hospital funding) to quantify drivers of regional disparities
4. **Predictive Modeling**: Build machine learning models to predict mortality outcomes and identify high-risk populations requiring intervention
5. **Individual Hospital Profiles**: Create detailed hospital-by-hospital comparison tools while maintaining appropriate statistical context to avoid inappropriate ranking
6. **Interactive Filtering**: Add dynamic filters by hospital type, population served, ownership status, and other characteristics
7. **Data API**: Develop a backend API for programmatic data access, enabling other researchers to build on this analysis
8. **Mobile Optimization**: Further refine responsive design for mobile viewing and touch interactions

---

**Analysis Date**: February 2026
**Data Source**: Centers for Medicare & Medicaid Services (CMS) Complications and Deaths Dataset
**Visualization Tool**: Python (Pandas, Plotly) with HTML/CSS deployment
