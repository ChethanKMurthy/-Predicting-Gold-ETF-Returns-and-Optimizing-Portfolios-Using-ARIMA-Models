# ARIMA Model for Predicting Returns and Optimizing Portfolios

The goal of this project is to apply **ARIMA models** to historical returns of selected **Gold ETFs**, predict future returns, and **optimize portfolio allocation** for maximum compounded return. The Gold ETFs chosen for this analysis are:

- **GOLDBEES.NS**
- **HDFCMFGETF.NS**
- **SBIGETS.NS**
- **ICICIGOLD.NS**
- **BSLGOLDETF.NS**
- **KOTAKGOLD.NS**
- **QGOLDHALF.NS**
- **IVZINGOLD.NS**

## Steps Involved

### 1. Downloading Historical Data
I use the **yfinance** library to download historical adjusted close prices of the selected ETFs. The data spans from **January 1, 2020, to July 10, 2024**, forming the basis for calculating daily returns and fitting ARIMA models.

### 2. Calculating Returns

Once i have the historical data, we compute **daily returns** for each ETF. Daily returns are determined as the percentage change in adjusted closing prices from one day to the next. This transformation is crucial as ARIMA models work best with **stationary time series data**, where returns tend to be more stable than prices.

### 3. Fitting ARIMA Models

Next, I fit **ARIMA models** to the daily returns of each ETF using the **statsmodels** library. The ARIMA model comprises three components: **autoregression (AR)**, **differencing (I)**, and **moving average (MA)**. In this project, I select the **ARIMA(1, 1, 1)** model order but can adjust it based on data characteristics.

The fitting process includes:

- **AR(1)**: Reflects the relationship between an observation and a lagged observation.
- **I(1)**: Applies differencing once to attain stationarity.
- **MA(1)**: Shows the relationship between an observation and a lagged error.

### 4. Showing ARIMA Results

After fitting the ARIMA models, we extract essential metrics like **Akaike Information Criterion (AIC)**, **Bayesian Information Criterion (BIC)**, **AR(1)**, and **MA(1)** parameters. These metrics offer insights into model fit and complexity. We present these metrics in a **tabular format** for easier comparison among different ETFs.

### 5. Predicting Future Returns

Leveraging our fitted ARIMA models, we forecast future returns for a specific horizon of **30 days**. These predictions aid in evaluating each ETF's expected performance over the forecast period. Predicted returns are organized into a **DataFrame** for further analysis.

### 6. Optimizing Portfolio

To maximize compounded return, we optimize portfolio allocation based on predicted returns by:

- Defining an **Objective Function** that calculates negative compounded return.
- **Normalizing** predicted returns using standard scaling.
- Setting **Constraints and Bounds** ensuring sum of weights equals 1 and each weight is between 0 and 1.
- Leveraging **scipy.optimize.minimize** function to determine weights maximizing compounded return.

### 7. Displaying Allocation Results
I showcase **optimal portfolio weights** in a tabular format indicating percentage allocation to each ETF for achieving maximum compounded return. Additionally, we plot this allocation with a **bar chart** for visual representation of optimized portfolio.

