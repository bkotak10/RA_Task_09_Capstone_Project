# Methodology and Analytical Approach

## Data Source

The analysis uses a 365-day cryptocurrency historical dataset obtained from Kaggle on December 15, 2025. The dataset contains daily market data for multiple cryptocurrency assets, including pricing, volume, and market capitalization metrics.

## Data Processing Methodology

Raw data was loaded directly from the source file and preserved without modification. All processing steps were applied to derived copies to maintain data provenance.

Data processing included:
- Parsing date fields into a standardized datetime format
- Sorting records by asset and time to support time-series operations
- Computing derived features such as daily returns, rolling moving averages, and short-term volatility

Missing values introduced by rolling-window calculations were expected and retained.

## Analytical Approach

Exploratory and descriptive analysis was performed to understand market behavior across assets. Summary statistics were generated to characterize distributions, and correlation analysis was used to evaluate relationships between key metrics such as returns and volatility.

Visual analysis was used to complement numerical findings and identify trends, outliers, and structural patterns.

## Validation Strategy

Validation focused on ensuring analytical correctness and realism:
- Volatility metrics were verified to be non-negative
- Daily return behavior was examined to confirm that extreme values were present but rare, reflecting legitimate cryptocurrency market dynamics rather than data corruption

No arbitrary truncation or removal of extreme values was performed.

## Use of LLMs

A large language model was used in a limited and controlled capacity to assist with hypothesis generation and narrative framing. The LLM was not used for:
- Data cleaning
- Feature engineering
- Statistical computation
- Result generation

All hypotheses suggested by the LLM were evaluated against computed statistics and correlations before being incorporated into the analysis.

## Bias and Limitations

The dataset reflects daily aggregate market data and does not include intraday prices, geographic participation, or investor demographics. Because the data was sourced from Kaggle, preprocessing decisions made by the dataset author may introduce implicit bias or limit transparency into original raw signals.

Survivorship bias may be present, as only actively traded assets appear in the dataset. Conclusions are therefore limited to descriptive and exploratory insights rather than causal claims.

## Reproducibility

All results presented in this project can be reproduced by executing the pipeline notebook from start to finish. No external services or non-deterministic processes are required.
