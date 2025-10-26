---
name: Forecasting ETT with Neural Network and XGBoost
tools: [Python, XGBoost, PyTorch, Time Series]
image: /assets/images/ETT_forecast_thumbnail.png
description: Forecasting transformer oil temperature using multivariate time-series regression with XGBoost and Neural Networks.
---

# Forecasting ETT with Neural Network and XGBoost
A comparative study on **multivariate time-series forecasting** using the *Electricity Transformer Temperature (ETT)* dataset.  
Implemented both ensemble-based regression (XGBoost) and deep learning models (Neural Networks) to predict transformer oil temperature (OT) based on 11 correlated sensor readings.  
By redefining the target variable as **Δy (change in temperature)** instead of the absolute value, the model captured temporal dynamics more effectively and achieved <u>top 1% accuracy among 200 participants</u>.

---

### Background
{% capture carousel_images %}
/assets/images/ETT_forecast/slides/ett_overview.png
/assets/images/ETT_forecast/slides/multivariate_timeseries.png
{% endcapture %}
{% include elements/carousel.html carousel_id="ett-background" carousel_images=carousel_images %}

The **ETT dataset** records two years of transformer operational data (2016–2018), including features such as time indices and multiple sensor readings.  
It was modified for this project to include 11 features and artificial missing values to simulate real-world data imperfections.  
The goal was to build models capable of learning **multivariate dependencies** and **temporal patterns** for accurate oil temperature prediction.

### Problem Setup
- **Task:** Multivariate time-series regression  
- **Input:** 11 features (including time indices and 8 measured variables)  
- **Target:** Oil Temperature (OT) inside the transformer  
- **Challenges:** Missing values, high dimensionality, and nonlinear temporal dependencies  


### Approach Overview
{% include elements/figure.html image="/assets/images/ETT_forecast/slides/pipeline.svg" %}

The project consists of two parallel pipelines:
1. **Ensemble Model (XGBoost)** — regression using boosted decision trees  
2. **Neural Network (PyTorch)** — regression using a fully-connected deep network  

Each model was trained and compared based on **Mean Squared Error (MSE)**, **feature impact**, and **temporal generalization**.

---

### 0. Feature Engineering

> **Core idea:** redefine the target as **Δy = yₜ − yₜ₋₁** instead of absolute y, and enrich the dataset with **temporal, statistical, and cyclic features** to improve generalization.

| Step | Operation | Purpose |
|------|------------|----------|
| 1 | **Missing value handling:** forward-fill, then fill remaining NaNs with train mean (train/test) | Maintain time-series continuity |
| 2 | **Lag features (Train):** create `y_lag_1`, `y_lag_2`; remove first 2 NaN rows | Inject temporal dependency |
| 3 | **Lag features (Test):** same shift logic, fill first rows using train mean | Stabilize initial test sequence |
| 4 | **Difference feature:** `y_diff = y_lag_1 − y_lag_2` | Capture short-term variation |
| 5 | **Residual target:** `y_residual = y − y_lag_1` → renamed as `y` | Learn Δy instead of absolute y |
| 6 | **Outlier handling:** replace out-of-range values (`feat_5 > 100`, `feat_7 ∉ [1,8]`) with NaN → forward-fill | Remove extreme noise |
| 7 | **Moving average (MA):** apply 5-step mean to `feat_1~8` → `*_ma` | Smooth short-term fluctuations |
| 8 | **Log transform:** log-scale `feat_1~8` using train-min offset | Normalize skewed distributions |
| 9 | **Cyclic encoding:** convert `day_of_week`, `hour` → `sin/cos` pairs | Encode daily/weekly periodicity |
| 10 | **Boundary handling:** detect if test follows train → if yes, copy last train y’s; otherwise, use **meta XGBoost** to predict initial lags | Ensure seamless test transition |
| 11 | **Post-processing (y features):** apply MA(5) to `y_lag_1`, `y_diff`, `y_residual` | Reduce high-frequency noise |
| 12 | **Feature selection:** choose active features from raw/log/MA/lag/diff/cyclic; set `y_residual → y` as final target | Avoid overfitting, finalize training set |
| 13 | **Inverse transform:** `inverse_y(pred) = pred + y_lag_1` (auto-handled for train/test) | Convert residuals back to actual y |
| 14 | **Validation sync:** remove first 2 train rows to align with augmented dataset | Maintain consistency during evaluation |

**Final Training Target**  
- Train: `y ← y_residual (Δy)`  
- Test prediction restored as: `ŷ = inverse_y(ŷ_residual) = ŷ_residual + y_lag_1`

**Selected Feature Groups**  
- Raw: `feat_1,2,3,4,6,7,8`  
- Log-scaled: `feat_1~4,6~8_log`  
- Moving averages: `feat_1~4,6~8_ma`  
- Lag/diff: `y_lag_1, y_diff, y_lag_1_ma, y_diff_ma`  
- Cyclic encodings: `day_sin, day_cos, hour_sin, hour_cos`

> Overall, this feature pipeline separates **trend (baseline)** from **change (Δy)**, reduces nonstationarity, and enhances generalization through temporal smoothing and cyclic signal encoding.




### 1. Ensemble Model (XGBoost)
{% capture carousel_images %}
/assets/images/ETT_forecast/slides/xgboost_param.png
/assets/images/ETT_forecast/slides/xgboost_result.png
{% endcapture %}
{% include elements/carousel.html carousel_id="ett-xgb" carousel_images=carousel_images %}

- Explored multiple XGBoost hyperparameters:
  - `n_estimators`, `max_depth`, `learning_rate`, and `subsample`
- Applied **feature engineering**:
  - Time decomposition (hour, day, week)
  - Rolling-window statistics (mean, variance)
  - Normalization and missing value imputation
- **Result:** Improved prediction stability and lower MSE compared to baseline  
- **Key insight:** Properly tuned tree depth and subsample ratio improved temporal generalization while preventing overfitting.

*(Insert loss curve or feature importance plot here)*

---

### 2. Neural Network Model
{% capture carousel_images %}
/assets/images/ETT_forecast/slides/nn_architecture.png
/assets/images/ETT_forecast/slides/nn_loss.png
{% endcapture %}
{% include elements/carousel.html carousel_id="ett-nn" carousel_images=carousel_images %}

- Implemented in **PyTorch**  
- Architecture:
  - Input: 11-dimensional vector (features)
  - Layers: MLP with dropout and ReLU activation  
  - Output: 1 (predicted oil temperature)
- Training details:
  - Optimizer: Adam  
  - Loss: MSELoss  
  - Scheduler: StepLR  
- Applied **hyperparameter tuning** on hidden size, learning rate, and batch size.  
- **Result:** NN model achieved smoother long-term trend prediction but required more data and epochs to converge.  

*(Insert training/validation loss curve here)*

---

### Comparison & Discussion
| Model | Type | Best Test MSE ↓ | Strengths | Limitations |
|:------|:------|:---------------:|:-----------|:-------------|
| XGBoost | Ensemble (tree-based) | ~0.00X | Fast, interpretable, handles small data well | Limited temporal context |
| NN (MLP) | Deep learning | ~0.00X | Learns complex temporal dependencies | Requires careful tuning and longer training |

**Takeaway:**  
XGBoost showed strong baseline performance with efficient training, while neural networks captured nonlinear interactions more effectively, suggesting potential improvement through hybrid models or temporal architectures (e.g., LSTM, Transformer).

---

### Future Work
Potential extensions include:
- Incorporating **sequence-aware architectures** (RNN, LSTM, Transformer).  
- Applying **attention mechanisms** for temporal importance weighting.  
- Building a **hybrid ensemble** combining tree-based and neural models for better stability.  

---

### Repository & Notebook
📂 All implementation details are available in the Jupyter notebooks:  
- [`final_project_1_ensemble.ipynb`](https://github.com/yourusername/forecasting-ett/blob/main/final_project_1_ensemble.ipynb)  
- [`final_project_2_nn.ipynb`](https://github.com/yourusername/forecasting-ett/blob/main/final_project_2_nn.ipynb)

*(Optional) Add a GIF or figure showing predictions vs ground truth curves here for visual comparison.*