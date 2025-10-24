# Nepal Hydropower Forecasting Dashboard

[![Streamlit App](https://img.shields.io/badge/Streamlit-App-brightgreen)](https://streamlit.io/) [![Python](https://img.shields.io/badge/Python-3.12%2B-blue)](https://www.python.org/) [![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

A Bayesian AR(1) time series dashboard for forecasting Nepal's hydropower generation (MW). Processes NEA log sheets, fits MCMC models, and visualizes plant-specific forecasts with climate scenario analysis. Built in Jupyter with embedded Streamlit.

## Features
- **Data Pipeline**: Aggregates daily Excel logs (2081–2082, 236–250 plants).
- **Bayesian AR(1)**: Custom MH sampler; priors tuned for MW scale; PPC validation.
- **Dashboard**: Plant selector, 90-day forecasts with 95% CI (Plotly), rainfall scenario slider.
- **Outputs**: Posterior traces, probabilistic forecasts (e.g., next-day mean ~743M MW).

## Installation
1. Clone: `git clone https://github.com/yourusername/nepal-hydropower-forecasting.git && cd nepal-hydropower-forecasting`
2. Env: `python -m venv venv && source venv/bin/activate` (Windows: `venv\Scripts\activate`)
3. Deps: `pip install -r requirements.txt` (numpy, pandas, streamlit, plotly, statsmodels, openpyxl)
4. Data: Place Excel files in `data/`; update paths in notebook.

`requirements.txt`:
```
numpy>=1.24.0
matplotlib>=3.7.0
scipy>=1.10.0
statsmodels>=0.14.0
pandas>=2.0.0
streamlit>=1.28.0
plotly>=5.15.0
jupyter>=1.0.0
openpyxl>=3.1.0
```

## Usage
- **Notebook**: `jupyter notebook NepalElectricityTSA.ipynb` → Run cells for processing, fitting, PPC plot.
- **Dashboard**: Extract Streamlit code to `app.py`; run `streamlit run app.py`. Select plant, view forecast, adjust scenarios.

**Tips**: Tune `proposal_sd` for MCMC (acceptance 0.2–0.5). Warnings in Jupyter? Run as `.py`.

## Structure
```
├── NepalElectricityTSA.ipynb  # Core notebook
└── README.md
```

## Known Issues
- AR(1) assumes no seasonality; extend with ARIMA/Prophet.
- Scale MCMC for large data.

## License
MIT - see [LICENSE](LICENSE).

*Updated: Oct 2025* | Questions? Open an issue!
