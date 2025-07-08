# EV-GridModel

A simulation framework for modeling electric vehicle (EV) charging stations at scale, analyzing charger utilization, queueing dynamics, and financial performance across various charger configurations and parking slot allocations.


## Features

- Configurable simulation period, region, and traffic load parameters.
- Multiple charger types (Level B and Level C) with customizable fleet mixes.
- Stochastic arrival and service processes based on real-world electricity prices and EV usage data.
- Queueing model with loss metrics, delays, and utilization tracking.
- Scenario analysis for charger counts and parking slot sizes.
- Financial metrics: revenue, costs (chargers, upgrades, parking), profit, ROI.
- Outputs as pandas DataFrame and optional CSV file.

## Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/your-username/E-GridModel.git
   cd E-GridModel
   ```

2. **Create a virtual environment** (recommended)

   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. **Install dependencies**

   ```bash
   pip install -r requirements.txt
   ```

## Configuration

All simulation parameters are defined in `config/param.py` via the `Settings` class:

- `sim_region`: Country for electricity price data (e.g., `'Italy'`).
- `sim_time`: Number of days to simulate (integer).
- Traffic load parameters: `min_traff_load`, `first_peak_range`, `second_peak_range`.
- `parking_slots`: List of queue sizes to evaluate.
- `charger_modes`: Tuples of (number\_of\_LevelB, number\_of\_LevelC) charger configurations.
- Cost settings: `charger_cost`, `upgrade_cost`, `maintenance_cost`, `parking_slot_cost`, `parking_fee`.
- Output flags: `save_df`, `print_df`.

## Usage

1. **Run the simulation**

   ```bash
   python main.py
   ```

2. **Results**

   - By default, the final results DataFrame is printed to the console.
   - If `save_df=True` in `config/param.py`, a CSV file `Simulation_results.csv` is written to the project root.

3. **Customize Scenarios**

   - Modify `config/param.py` to adjust simulation duration, charger mixes, parking slot sizes, and cost parameters.
   - Compare different outputs by reviewing the generated CSV or by loading the DataFrame in a Jupyter notebook.

## Data Sources

- **EV Descriptions** (`PEVC/src/ev_desc_data.csv`): Specifications for each EV model, such as battery capacity, range, and charging speed.
- **Electricity Prices** (`PEVC/src/european_electricity_price_data_hourly.zip`): Hourly wholesale price data for the selected country.
- **EV Market Share** (`PEVC/src/ev_market.json`): Distribution of EV brand arrivals used to sample EV types.

## Extending the Model

- Add new charger types by extending the `Charger` class in `PEVC/models.py`.
- Incorporate additional cost components or pricing strategies in `PEVC/utils.py` or the `prepare_results` function.
- Visualize results using `matplotlib` or export the DataFrame for analysis in external tools.


