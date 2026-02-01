# Technical Architecture and Pipeline Overview

## System Overview

This project implements a lightweight, batch-oriented ETL and analysis pipeline for cryptocurrency market data. The system is designed to be reproducible, transparent, and easy to validate, with a clear separation between data ingestion, transformation, analysis, and presentation layers.

The pipeline is implemented using Python within a Jupyter Notebook and processes a historical cryptocurrency dataset sourced from Kaggle.

## Architecture and Data Flow

The pipeline follows a linear and deterministic flow:

Raw Data (CSV)
→ Data Loading
→ Data Cleaning and Transformation
→ Analytical Computation
→ Visualization and Interpretation
→ Persisted Processed Dataset

Each stage is executed explicitly and independently to ensure traceability and reproducibility.

## ETL Pipeline Design

### Extract
Raw data is extracted from a CSV file without modification. The raw dataset is treated as immutable input to preserve data provenance.

### Transform
Transformation logic includes:
- Data type normalization (date parsing)
- Time-series sorting by asset and date
- Feature engineering, including:
  - Daily returns
  - Rolling moving averages (7-day, 30-day)
  - Rolling volatility (7-day standard deviation)

Transformations are deterministic and applied consistently across all assets.

### Load
The transformed dataset is written to a processed CSV file. This enables reuse of cleaned data for downstream analysis without re-running the entire pipeline.

## Analysis Layer

Analytical computations are performed using Python and Pandas and include:
- Summary statistics for key metrics
- Correlation analysis between returns and volatility
- Aggregations used to support visualization and interpretation

All analytical results are derived programmatically.

## Visualization Layer

Visualizations are generated using Matplotlib and include:
- Price trends over time
- Distribution of daily returns
- Relationship between market capitalization and volatility

The visualization layer is strictly separated from data transformation logic.

## Quality Assurance

Basic quality checks are implemented to validate critical metrics:
- Verification that extreme daily returns are rare and not dominant
- Validation that computed volatility values are non-negative

These checks ensure analytical integrity while accounting for realistic market behavior.

## LLM Integration

A large language model was used only to assist with hypothesis generation and narrative framing. The LLM did not perform any data processing, calculations, or statistical analysis. All LLM-generated suggestions were validated against ground-truth outputs produced by the pipeline.

## Dependencies

Primary dependencies include:
- Python
- Pandas
- NumPy
- Matplotlib

The pipeline is executed by running the Jupyter notebook from start to finish.

## Current Status

The pipeline is feature-complete for Phase 3. All planned transformations, analyses, validations, and visualizations have been implemented and verified. No major technical blockers remain.
