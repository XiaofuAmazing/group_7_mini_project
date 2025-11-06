# CNGF5020 Group 7 Mini Project

## Agricultural Fire Monitoring and Impact Analysis in Heilongjiang Province

This project analyzes agricultural fire activities (primarily crop residue burning) in Heilongjiang Province, China, using satellite remote sensing data, meteorological data, and air quality measurements. The analysis spans from 2010 to 2019 and addresses multiple research questions related to fire seasonality, spatial patterns, agricultural burning identification, policy impacts, and the relationship between meteorological conditions and air pollution.

---

## Table of Contents

- [Overview](#overview)
- [Project Structure](#project-structure)
- [Data Sources](#data-sources)
- [Research Questions](#research-questions)
- [Installation](#installation)
- [Usage](#usage)
- [Key Findings](#key-findings)
- [Output Files](#output-files)
- [Dependencies](#dependencies)
- [Authors](#authors)
- [License](#license)

---

## Overview

This project investigates agricultural fire activities in Heilongjiang Province through comprehensive analysis of:

- **Satellite fire detection data** (MODIS, 2010-2019)
- **Meteorological data** (wind speed, humidity, temperature, precipitation)
- **Air quality data** (PM2.5, PM10, and other pollutants)
- **Cropland distribution and phenological data** (maize and wheat)
- **Administrative boundaries** (county-level shapefiles)

The analysis addresses core questions about fire seasonality, spatial patterns, agricultural burning identification, policy effectiveness, and the meteorological factors affecting fire detection and environmental impacts.

---

## Project Structure

The project is organized as a Jupyter Notebook (`group7MiniProject.ipynb`) with the following sections:

### 0. Data Cleaning
- Extracts Heilongjiang Province boundary from county-level shapefiles
- Filters MODIS fire data to Heilongjiang bounding box
- Processes and merges multi-year fire data (2010-2019)
- Creates temporal features (year, month, week, datetime)

### 1. Core Question 1: Fire Seasonality and Spatial Patterns
- Analyzes national and provincial fire seasonality (weekly climatology)
- Identifies fire hotspot provinces and peak weeks
- Performs county-level clustering of intra-seasonal fire patterns
- Creates spatial visualizations of fire patterns

### 2. Core Question 2: Agricultural Fire Identification
- Links fire points to cropland distribution (maize and wheat)
- Identifies agricultural fires based on spatial overlap and temporal alignment with harvest windows
- Analyzes the proportion of fires occurring on cropland during harvest periods
- Evaluates spatial and temporal alignment between fires and agricultural activities

### 3. Core Question 3: Policy Impact Evaluation
- Evaluates the impact of 2015 agricultural burning suppression policies
- Compares agricultural fire share before (2010-2014) and after (2015-2019) policy implementation
- Performs statistical tests (chi-square, bootstrap confidence intervals)
- Creates county-level difference maps showing policy effects

### 4. Core Question 4
- [Additional analysis as documented in the notebook]

### 5. Challenge 1
- [Challenge-specific analysis]

### 6. Challenge 2: Methodological Limitations and Uncertainty
- Discusses key sources of uncertainty in agricultural fire identification
- Evaluates impact on agricultural fire estimates
- Suggests additional datasets for improvement

### 7. Challenge 3: Meteorology & Pollution
- **Question 1**: How meteorological conditions (wind speed, humidity, temperature inversions) influence both the detection and environmental impact of straw burning
- **Question 2**: How to link temporal peaks in pollution (PM2.5, PM10) to the timing of straw burning events

---

## Data Sources

### Satellite Fire Data
- **Source**: MODIS (Moderate Resolution Imaging Spectroradiometer)
- **Format**: CSV files (`modis_YYYY_China.csv`)
- **Time Period**: 2010-2019
- **Key Fields**: latitude, longitude, acquisition date/time, Fire Radiative Power (FRP), confidence, satellite, instrument, brightness
- **Location**: `Satellite Fire Data/`

### Meteorological Data
- **Source**: WheatA software(小麦芽)
- **Format**: CSV (`黑龙江气象数据_合并.csv`)
- **Time Period**: 2010-2019
- **Key Variables**: Wind speed (10m), relative humidity, temperature (2m), precipitation, sea-level pressure
- **Spatial Coverage**: Multiple cities in Heilongjiang Province

### Air Quality Data
- **Source**: WheatA software（(小麦芽)）
- **Format**: CSV (`黑龙江大气六参数据_合并.csv`)
- **Time Period**: 2010-2019
- **Key Variables**: PM2.5, PM10, Ozone, SO2, NO2, CO
- **Spatial Coverage**: Multiple cities in Heilongjiang Province

### Cropland Distribution and Phenological Data
- **Source**: Remote sensing-based cropland maps
- **Format**: GeoTIFF raster files
- **Crops**: Maize and Wheat
- **Time Period**: 2010-2019
- **Key Information**: Crop maturity dates (MA - Maturity Date)
- **Location**: `Cropland distribution and phenological data/`

### Administrative Boundaries
- **Source**: County-level administrative boundaries
- **Format**: Shapefile (`CHN_County.shp`)
- **Coordinate System**: WGS 84 (EPSG:4326)
- **Key Fields**: Province name, county ID (GID_2)

---

## Research Questions

### Core Question 1: Fire Seasonality and Spatial Patterns
**What are the temporal and spatial patterns of fire activities in China, with focus on Heilongjiang Province?**

- National weekly fire seasonality (2010-2019 climatology)
- Provincial fire hotspot identification
- County-level intra-seasonal fire pattern clustering

### Core Question 2: Agricultural Fire Identification
**How can we identify agricultural fires using spatial and temporal alignment with cropland and harvest windows?**

- Spatial overlap between fire points and cropland
- Temporal alignment with crop maturity/harvest periods
- Proportion of fires on cropland during harvest windows

### Core Question 3: Policy Impact Evaluation
**What is the impact of agricultural burning suppression policies implemented in 2015?**

- Comparison of agricultural fire share before and after 2015
- Statistical significance testing
- County-level heterogeneity in policy response

### Challenge 3: Meteorology & Pollution
**Q1**: How might meteorological conditions (wind speed, humidity, temperature inversions) influence both the detection and environmental impact of straw burning?

**Q2**: If regional air pollution data (PM2.5, PM10) were available, how could you link the temporal peaks in pollution to the timing of straw burning events?

---

## Installation

### Prerequisites
- Python 3.7 or higher
- Jupyter Notebook or JupyterLab

### Required Python Packages

```bash
pip install pandas numpy geopandas matplotlib seaborn scipy shapely fiona rasterio
```

Or install from requirements file (if provided):

```bash
pip install -r requirements.txt
```

### Key Dependencies
- `pandas`: Data manipulation and analysis
- `numpy`: Numerical computing
- `geopandas`: Geospatial data operations
- `matplotlib`: Plotting and visualization
- `seaborn`: Statistical visualization
- `scipy`: Statistical tests
- `shapely`: Geometric operations
- `fiona`: Shapefile reading
- `rasterio`: Raster data reading (for cropland data)

---

## Usage

### Running the Notebook

1. **Open Jupyter Notebook**:
   ```bash
   jupyter notebook group7MiniProject.ipynb
   ```

2. **Execute cells sequentially**:
   - Start with Section 0 (Data Cleaning) to process raw data
   - Proceed through each section in order
   - Each section builds upon previous results

3. **Data Requirements**:
   - Ensure all data files are in the correct directories (see [Data Sources](#data-sources))
   - The notebook will create output directories automatically

### Output Directories

- `outputs/`: Main output directory for processed fire data and analysis results
- `outputs_q2/`: Outputs specific to Core Question 2
- `outputs_q3/`: Outputs specific to Core Question 3
- `visualizations/`: Generated figures and maps (for Challenge 3)

---

## Key Findings

### Fire Seasonality
- **Peak fire periods**: Spring (March-May) and Autumn (September-November) in Heilongjiang Province
- **National pattern**: Distinct seasonal cycles with regional variations
- **County-level patterns**: Six distinct intra-seasonal fire pattern clusters identified

### Agricultural Fire Identification
- **Spatial alignment**: ~2% of fires occur on cropland during harvest windows (overall)
- **Temporal alignment**: Spike in agricultural fires during late October-November
- **Statistical significance**: Chi-square test confirms non-random distribution (p < 0.001)

### Policy Impact (2015)
- **Agricultural fire share reduction**: -87.1% (pre- vs post-2015)
- **Bootstrap confidence interval**: Excludes zero, confirming robust policy effect
- **County heterogeneity**: 56 counties showed significant decreases, 0 showed increases

### Meteorological Impact (Challenge 3)
- **Wind speed**: Low wind speed (<2 m/s) leads to 19% higher PM2.5 concentrations
- **Humidity**: Mainly affects satellite detection (low humidity = higher detection rate)
- **Worst conditions**: Low wind speed + low humidity + strong temperature inversion → PM2.5 reaches 46.25 µg/m³

### Pollution-Fire Linkage (Challenge 3)
- **General association**: 45.3% of pollution peak days (PM2.5 ≥ 75th percentile) have same-day fires
- **Extreme events**: 80.6% of extreme pollution events (PM2.5 > 100 µg/m³) linked to same-day fires
- **Reverse association**: 46.8% of intense fire days (≥90th percentile) show immediate pollution peaks (PM2.5 +35%)

---

## Output Files

### Processed Data
- `outputs/modis_2010_2019_Heilongjiang_bbox.csv.gz`: Filtered fire data for Heilongjiang Province
- `outputs/modis_heilongjiang_bbox_counts.csv`: Yearly fire point counts
- `outputs/modis_heilongjiang_bbox_year_summary.csv`: Annual fire statistics

### Analysis Results
- `outputs_q2/q3_triple_trend_panel.png`: Policy impact trend visualization
- `outputs_q2/q3_diffmap_agri_share_post_minus_pre.png`: County-level policy impact map
- `outputs_q2/q3_break_bootstrap_ci.csv`: Bootstrap confidence intervals for policy impact
- `outputs_q2/q3_diffmap_table.csv`: County-level difference statistics

### Visualizations (Challenge 3)
- `visualizations/Figure1_Seasonal_Pattern.png`: Seasonal pollution and fire patterns
- `visualizations/Figure13_Wind_Speed_Impact.png`: Wind speed impact on PM2.5
- `visualizations/Figure16_Combined_Conditions_Impact.png`: Combined meteorological conditions
- `visualizations/Figure18_Monthly_Temporal_Pattern.png`: Monthly temporal patterns
- `visualizations/Figure19_Fire_vs_NonFire_Comparison.png`: Fire vs non-fire day comparison
- [Additional figures as generated]

---

## Dependencies

### Python Version
- Python 3.7+

### Core Libraries
```
pandas >= 1.3.0
numpy >= 1.20.0
geopandas >= 0.10.0
matplotlib >= 3.4.0
seaborn >= 0.11.0
scipy >= 1.7.0
shapely >= 1.8.0
fiona >= 1.8.0
rasterio >= 1.2.0
```

### Optional
- `jupyter` or `jupyterlab` for notebook interface
- `tqdm` for progress bars (if used)

---

## Authors

**CNGF5020 Group 7**

This project was completed as part of the CNGF5020 course requirements.

---

## License

This project is for academic purposes only. Data sources should be cited appropriately:

- **MODIS Fire Data**: NASA FIRMS (Fire Information for Resource Management System)
- **Meteorological Data**: [Source to be specified]
- **Air Quality Data**: [Source to be specified]
- **Cropland Data**: [Source to be specified]
- **Administrative Boundaries**: [Source to be specified]

---

## Acknowledgments

- NASA FIRMS for MODIS fire detection data
- Data providers for meteorological and air quality measurements
- Course instructors and teaching assistants for guidance

---

## Notes

- **Data Processing**: The notebook processes large datasets (290,268+ fire points). Ensure sufficient memory and disk space.
- **Execution Time**: Full notebook execution may take 30-60 minutes depending on hardware.
- **Coordinate System**: All spatial data uses WGS 84 (EPSG:4326).
- **Temporal Coverage**: Analysis covers 2010-2019 (10 years of data).

---

## Contact

For questions or issues related to this project, please contact the course instructor or refer to the course documentation.

---

**Last Updated**: 2025/11/6

