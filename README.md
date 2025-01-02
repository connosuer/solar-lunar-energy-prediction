
# Solar-Lunar Energy Prediction

A Python-based modeling and prediction system that analyzes the impact of solar and lunar activities on renewable energy production. This model incorporates weather patterns, temperature variations, and solar intensity to predict power output and efficiency of solar installations.

## Features
- Solar panel efficiency prediction based on temperature and solar intensity
- Weather pattern simulation and its impact on energy production
- Seasonal and daily variation modeling 
- Power output prediction with real-world system variations
- Energy price modeling incorporating environmental factors
- Both hourly and daily data aggregation options

## Model Components
- Temperature Impact: y = -0.0316x + 20
- Solar Intensity Impact: y = 0.0027x + 17.955
- Weather States: Clear (60%), Cloudy (30%), Very Cloudy (10%)
- System Efficiency Range: 5-9.5%
- Price Variation: $0.110-$0.135 per kWh

## Installation

```
pip install -r requirements.txt
```

## Usage

```python
# Generate solar data
df = generate_solar_data()

# Create daily aggregations
daily_df = df.resample('D', on='datetime').agg({
    'temperature': 'mean',
    'solar_intensity': 'mean',
    'efficiency': 'mean',
    'power_output': 'sum',
    'price_per_kwh': 'mean',
    'weather_condition': 'mean'
}).reset_index()

# Export data
df.to_csv('solar_data_hourly.csv', index=False)
daily_df.to_csv('solar_data_daily.csv', index=False)
```

## Model Performance
- R² Score: 0.9872
- Root Mean Square Error: 2.89 kWh
- Mean Absolute Error: 2.29 kWh

## Data Output
The model generates two CSV files:
- `solar_data_hourly.csv`: Hourly data points (8760 rows/year)
- `solar_data_daily.csv`: Daily aggregated data (365 rows/year)

### Data Fields
- datetime: Timestamp
- temperature: Temperature in °C
- solar_intensity: Solar intensity in W/m²
- efficiency: Panel efficiency in %
- power_output: Power output in kWh
- price_per_kwh: Energy price in $/kWh
- weather_condition: Weather state (0: Clear, 1: Cloudy, 2: Very Cloudy)

## Requirements
- Python 3.x
- pandas
- numpy
- matplotlib
- scikit-learn

## Citation
If you use this model in your research, please cite:
```
@article{salama2024solar,
  title={Solar and Lunar Influences on Meteorology and Energy Production},
  author={Salama, Samuel J.},
  year={2024}
}
```
## License
[MIT License](LICENSE)

## Author
Samuel J. Salama
