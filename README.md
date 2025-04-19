# Refinitiv Eikon Data Retrieval for DAX 40 – Repository

This repository contains the Python scripts used to retrieve trade and quote data from Refinitiv Eikon for all DAX 40 stocks. The data collection forms the basis of the master’s thesis titled:

**"Resiliency of Fragmented Equity Markets: Evidence from Germany"**  
Authored by Tommy Norman and Daan Sustronck  
Faculty of Economics and Business, KU Leuven (Academic Year 2024–2025)

The purpose of this repository is to document and facilitate the retrieval of raw market data for academic analysis. The retrieved data is later cleaned and analyzed in R. This repository does not contain any processed datasets or econometric analysis code.

## Overview

The scripts in this repository are designed to:
- Identify all constituents of the DAX 40 index
- Determine the fragmentation of each stock across trading venues
- Retrieve time-stamped quote and trade data for each instrument

The retrieval process is structured across three Jupyter notebooks, which must be executed in a specific order due to data dependencies.

## Repository Contents

- `Get_CON_&_FRA_Data.ipynb`: Retrieves the DAX 40 constituents and all venue-specific RICs per stock. This notebook must be run first. It produces two key output files: `index_constituents.pkl` and `fragmentation.pkl`, which are used as inputs by the subsequent notebooks.
- `Get_TAQ_Data.ipynb`: Retrieves quote data (best bid and offer) at a 1-minute frequency over a specified month using the venue mappings.
- `Get_TAS_Data.ipynb`: Retrieves trade data at the TAS interval over a specified week. Includes batching and progress tracking for high-volume data retrieval.

## Execution Instructions

Before running any data retrieval scripts, ensure that:
1. The Refinitiv Eikon desktop terminal is installed, running, and logged in on your system.
2. A valid Eikon API key is available and configured in your environment.

The notebooks must be executed in the following order:

1. **`Get_CON_&_FRA_Data.ipynb`**  
   - Output: `index_constituents.pkl`, `fragmentation.pkl`
2. **`Get_TAQ_Data.ipynb`** *(for quote data by month)*
3. **`Get_TAS_Data.ipynb`** *(for trade data by week)*

These scripts will save `.csv` files containing raw time-series data, structured per stock and date.

## Requirements

The scripts require Python 3.10+ and the following Python packages:
- `pandas`
- `numpy`
- `datetime`
- `eikon`
- `refinitiv.data`
- `pathlib`
- `dateutil`
