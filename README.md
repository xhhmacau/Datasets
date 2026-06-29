# DSTF-Bench Datasets

This repository provides the public datasets used in **DSTF-Bench**, a shift-aware benchmark for time series forecasting in non-stationary environments.

The benchmark covers multiple real-world domains, including economics, transportation, energy, air quality, agriculture, public safety, and hydrology. Each dataset is provided as a CSV file with a `date` column and one or more time-dependent variables. The forecasting target for each dataset is listed below.

## Data Availability

Due to its large file size, the **Electricity** dataset is hosted on Zenodo instead of being stored directly in this GitHub repository:

- Electricity dataset: https://zenodo.org/records/21016755

All other datasets are included in this repository.

After downloading the Electricity dataset, please place it under:

```text
Energy/electricity.csv
```

## Repository Structure

```text
.
├── Agriculture/
│   ├── beijing.csv
│   ├── guangzhou.csv
│   └── shenyang.csv
├── Airquality/
│   ├── Aoti.csv
│   ├── Daxing.csv
│   ├── Guanyuan.csv
│   ├── Tiantan.csv
│   └── Wanliu.csv
├── Economics/
│   └── stock.csv
├── Energy/
│   ├── wind.csv
│   └── electricity.csv        # Download from Zenodo
├── Hydrology/
│   ├── mooloolaba_waves.csv
│   └── saugeen_river.csv
├── PublicSafety/
│   └── CHI_Crime.csv
└── Transportation/
    └── NYC_Taxi.csv
```

## Dataset Summary

| Domain | Dataset | File | Length | Features | Frequency | Target Variable | Region |
|---|---|---:|---:|---:|---|---|---|
| Economics | Stock | `Economics/stock.csv` | 5,538 | 8 | Daily | `DailyPrice` | United States |
| Transportation | NYC_Taxi | `Transportation/NYC_Taxi.csv` | 10,320 | 1 | 30-min | `Value` | New York, USA |
| Energy | Electricity | `Energy/electricity.csv` | 2,049,280 | 7 | 1-min | `Sub_metering_3` | Sceaux, France |
| Energy | Wind | `Energy/wind.csv` | 48,673 | 1 | 15-min | `windspeed` | China |
| Air Quality | BeijingAQ_Aoti | `Airquality/Aoti.csv` | 71,209 | 7 | Hourly | `AQI` | Beijing, China |
| Air Quality | BeijingAQ_Wanliu | `Airquality/Wanliu.csv` | 71,529 | 7 | Hourly | `AQI` | Beijing, China |
| Air Quality | BeijingAQ_Daxing | `Airquality/Daxing.csv` | 73,066 | 7 | Hourly | `AQI` | Beijing, China |
| Air Quality | BeijingAQ_Tiantan | `Airquality/Tiantan.csv` | 69,930 | 7 | Hourly | `AQI` | Beijing, China |
| Air Quality | BeijingAQ_Guanyuan | `Airquality/Guanyuan.csv` | 72,403 | 7 | Hourly | `AQI` | Beijing, China |
| Agriculture | Beijing | `Agriculture/beijing.csv` | 8,602 | 2 | Hourly | `shidu` | Beijing, China |
| Agriculture | Guangzhou | `Agriculture/guangzhou.csv` | 8,760 | 2 | Hourly | `shidu` | Guangzhou, China |
| Agriculture | Shenyang | `Agriculture/shenyang.csv` | 8,760 | 2 | Hourly | `shidu` | Shenyang, China |
| Public Safety | CHI_Crime | `PublicSafety/CHI_Crime.csv` | 17,536 | 4 | Hourly | `THEFT` | Chicago, USA |
| Hydrology | Mooloolaba_Waves | `Hydrology/mooloolaba_waves.csv` | 43,454 | 6 | 30-min | `Hs` | Queensland, Australia |
| Hydrology | Saugeen_River | `Hydrology/saugeen_river.csv` | 23,741 | 1 | Daily | `flow` | Ontario, Canada |

## Dataset Descriptions

### Economics

- **Stock** contains daily financial market indicators from the United States.
- The target variable is `DailyPrice`.
- The dataset is suitable for evaluating forecasting models under market fluctuations and distribution shifts.

### Transportation

- **NYC_Taxi** contains 30-minute taxi demand records from New York City.
- The target variable is `Value`.
- This dataset reflects urban mobility patterns with temporal variations such as rush hours, weekends, holidays, and demand shifts.

### Energy

- **Electricity** contains minute-level household electricity consumption data from Sceaux, France.
- The target variable is `Sub_metering_3`.
- Because of its large size, this dataset is hosted separately on Zenodo: https://zenodo.org/records/21016755

- **Wind** contains 15-minute wind speed observations from China.
- The target variable is `windspeed`.
- This dataset is used for forecasting renewable energy-related environmental dynamics.

### Air Quality

The air quality datasets are collected from five monitoring stations in Beijing, China:

- `Aoti.csv`
- `Wanliu.csv`
- `Daxing.csv`
- `Tiantan.csv`
- `Guanyuan.csv`

Each file contains hourly air quality measurements with the following variables:

```text
PM2.5, PM10, AQI, SO2, NO2, O3, CO
```

The target variable is `AQI`. These datasets are useful for studying non-stationary patterns caused by weather, emissions, seasonal changes, and urban environmental variation.

### Agriculture

The agriculture datasets contain hourly meteorological records from three Chinese cities:

- `beijing.csv`
- `guangzhou.csv`
- `shenyang.csv`

Each file includes:

```text
temp, shidu
```

The target variable is `shidu`, which represents humidity. These datasets are designed for forecasting agricultural and environmental conditions across different regions.

### Public Safety

- **CHI_Crime** contains hourly crime count time series from Chicago, USA.
- The variables include:

```text
ASSAULT, BATTERY, CRIMINAL DAMAGE, THEFT
```

- The target variable is `THEFT`.
- This dataset captures public safety dynamics and temporal changes in urban crime patterns.

### Hydrology

- **Mooloolaba_Waves** contains 30-minute ocean wave observations from Queensland, Australia.
- The target variable is `Hs`, representing significant wave height.
- Variables include wave height, wave period, peak direction, and sea surface temperature.

- **Saugeen_River** contains daily river flow observations from Ontario, Canada.
- The target variable is `flow`.
- This dataset is used for hydrological time series forecasting under environmental variation.

## File Format

All datasets are stored in CSV format. Each file contains a `date` column as the timestamp column.

Example:

```python
import pandas as pd

df = pd.read_csv("Airquality/Aoti.csv")
df["date"] = pd.to_datetime(df["date"])

print(df.head())
```

## Notes

- The `date` column should be used as the temporal index.
- Target variables are listed in the dataset summary table.
- The number of features does not include the `date` column.
- The Electricity dataset should be downloaded separately from Zenodo and placed at `Energy/electricity.csv`.

## Citation

If you use these datasets, please cite the corresponding DSTF-Bench paper or repository.
