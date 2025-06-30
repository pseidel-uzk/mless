# Homework 2: Multivariate Time‐Series Forecasting & Plotting

**Student:** Patrick Seidel
**Course:** Machine Learning for Earth System Science  
**Due Date:** June 30, 2025  
----
## Assignment Overview  
In this homework, I extended the provided notebooks in the `time_series_forecasting` folder to:  
1. Plot forecasts from multiple models on a single panel.  
2. Build a multivariate forecasting model that uses both temperature and ozone as inputs to predict future ozone concentrations.  
3. (Partial) Incorporate “future” temperature forecasts as an additional input to improve ozone prediction, and compare results.
----
## Task 1: Multi‐Model Plotting  
- **What I did:**  
  - Created `compare_model_predictions()` in `multi_model_plotter.ipynb`.  
  - Takes a single `.npy` ground truth series and multiple CSV prediction files.  
  - Validates timestep alignment, infers context vs. horizon lengths, cycles through distinct colors, markers, and line styles.  
- **Reusability:**  
  - Pass any station’s `.npy` file and as many model `.csv` files as needed.  
  - Labels and legend entries update automatically.
----
## Task 2: Multivariate Forecasting  
- **What I did:**  
  - Adapted `create_sequences()` of `mless/time_series_forecasting/3_AutoRegressive_Models.ipynb` to accept `["temp", "o3"]` and output 3‑channel arrays (`station_code`, `temp`, `ozone`).  
  - Copied the single‐variable LSTM notebook.  
  - Adapted dimensionality of LSTM model to take multivariate data
  - Trained an LSTM to forecast the next 96 hours of ozone using the past 336 hours of both inputs.  
- **Results:**  
  - RMSE on test set: **0.6877**
----
## Task 3: Using Future Temperature Forecasts  
- **What I did so far:**  
  - Created `5_LSTM_multivariate copy.ipynb` by copying the multivariate notebook.  
  - Added the full temperature data (including test timeframe) to the training data
  - Added large negative values as ozone values for the timeframe of the test data
  - Integrated these into model input for ozone prediction.  