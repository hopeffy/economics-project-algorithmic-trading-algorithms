# Implementation Plan - Algorithmic Trading Testing

# Goal Description
Implement a testing framework for algorithmic trading strategies (Grid Search, Ichimoku + Market Structure) using Binance data (BTC/ETH) and Macro/On-chain indicators. The output will be a Jupyter Notebook and a PDF report.

## User Review Required
> [!IMPORTANT]
> - **Data Source**: I will use `ccxt` for Binance data and `yfinance` for Macro data (DXY). For On-Chain data (NVT), I will try to fetch from free sources or approximate it if direct API access requires a key.
> - **Timeframe**: The user specified "Jan 1, 2022 – Present (End of Nov 2025)". Since today is Nov 27, 2025, I will fetch up to the current date.

## Proposed Changes

### Environment & Data
#### [NEW] [requirements.txt](file:///d:/economics/requirements.txt)
- List dependencies: `pandas`, `numpy`, `ccxt`, `pandas-ta`, `matplotlib`, `plotly`, `yfinance`, `scipy`.

#### [NEW] [data_loader.py](file:///d:/economics/data_loader.py)
- Functions to fetch historical data from Binance via `ccxt`.
- Functions to fetch Macro data via `yfinance`.
- Data cleaning and merging routines.

### Strategy Implementation & Backtesting
#### [NEW] [analysis.ipynb](file:///d:/economics/analysis.ipynb)
- **Phase 1: Data Acquisition**:
    - Migrate logic from `data_loader.py` to notebook cells.
    - Fetch and clean data directly in the notebook.
- **Phase 2: Execution Core**:
    - Implement indicators (RSI, BB, KAMA, SuperTrend, Ichimoku).
    - Implement Grid Search (Test Case 1).
    - Implement Ichimoku + Market Structure (Test Case 2).
    - Run Backtests and Forward Tests.
- **Phase 3: Reporting**:
    - Visualize results.
    - Generate analysis text.

#### [DELETE] [data_loader.py](file:///d:/economics/data_loader.py)
- Logic moved to notebook.

#### [DELETE] [strategies.py](file:///d:/economics/strategies.py)
- Logic moved to notebook.

#### [DELETE] [backtester.py](file:///d:/economics/backtester.py)
- Logic moved to notebook.

## Verification Plan
### Automated Tests
- Run `data_loader.py` to ensure data is fetched correctly.
- Run simple unit tests for indicator calculations in `strategies.py`.

### Manual Verification
- Inspect the generated plots in `analysis.ipynb` to verify buy/sell signals align with logic.
- Check the "Forward Test" results for Oct-Nov 2025.
