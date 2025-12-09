# Vocabulary Note

This project uses several terms that are common in quantitative finance and machine learning:

- Time series — A sequence of data points indexed in chronological order, such as daily stock prices.
- Technical indicators — Calculated signals (RSI, MACD, moving averages…) used to analyse market behaviour.
- Return — The percentage change in price from one day to the next.
- Volatility — A measure of how much the price fluctuates over time.
- Momentum — A measure of recent price acceleration or deceleration.
- Binary classification — A prediction task with only two possible outcomes (here: up or down).
- Baseline model — A simple model used as a reference to evaluate future improvements.
- Random Forest — A machine learning algorithm based on multiple decision trees, used here to predict price direction.
-  Bagging (Bootstrap Aggregating) – An ensemble technique that trains multiple models on random subsets of the data to reduce variance and improve stability.
- GridSearchCV – A hyperparameter optimization method that tests all possible combinations of predefined parameter values using cross-validation.
- TimeSeriesSplit – A cross-validation strategy that preserves the temporal order of financial data to avoid data leakage.
- F1-score – A performance metric that combines precision and recall, especially useful when classes are imbalanced.
- ROC Curve – A graphical representation of the trade-off between true positive rate and false positive rate across different thresholds.
- AUC (Area Under the Curve) – A metric measuring a model’s ability to distinguish between two classes. An AUC of 0.5 corresponds to random guessing.
- Data leakage – A situation where information from the future is unintentionally used during training, leading to overly optimistic performance estimates.

  
# Overview

This vocabulary provides the foundation needed to understand the techniques and modelling choices presented throughout the project.

This project applies Machine Learning techniques to financial time series with the goal of predicting short-term stock price movements.
Using historical market data from AAPL (Apple), the notebook walks through the essential steps of a predictive modelling workflow: descriptive exploration of market data, creation of technical indicators commonly used in trading, preprocessing and preparation of time-series features, definition of a binary classification problem (up/down prediction), training of a baseline model using a Random Forest Classifier, evaluation of predictive performance and model stability. 
The objective is not to forecast exact prices but to capture directional trends, providing a foundation that can be further extended with more advanced quantitative or machine learning methods.

# Introduction to the Stock Market and Shares

The stock market is an organized marketplace where financial assets are traded, such as shares (ownership stakes in companies), bonds (corporate or government debt), ETFs (investment funds), and other financial instruments (options, futures, etc.).

A share represents a portion of ownership in a publicly listed company. By purchasing a share, an investor can receive dividends paid by the company or sell the share later if its price increases, generating a capital gain.

The price of a share corresponds to the most recent transaction price on the market.

For example, if a share is traded at $20, its price is considered to be $20. If the next transaction occurs at $18, the new displayed price becomes $18. As a result, stock prices fluctuate in real time based on supply and demand.

Prices rise when many investors want to buy and fall when investors want to sell. Influencing factors include the company’s financial results, economic conditions such as inflation, and psychological factors like collective market euphoria.

The opening price is the share price at the start of the trading session, while the closing price is the price at the end of the session.
Volume refers to the number of shares traded.Volatility measures the magnitude of price fluctuations. Market capitalization represents the total value of a company (number of shares × price per share).


# Data Extraction – Step 1

The first step of the project consists in collecting real historical market data to build a reliable foundation for analysis and modelling.
We use the yfinance library, which provides an easy interface to download financial time series directly from Yahoo Finance. The dataset used in this step corresponds to the stock AAPL (Apple), covering the period from 2020 to 2025.

The extraction process begins by calling the yf.download() function with a specified ticker, start date and end date. The data returned includes the standard market variables used in quantitative analysis: opening price, closing price, daily highs and lows, adjusted close and traded volume. After downloading, the dataset is cleaned by resetting the index to expose the time column properly and flattening the columns to remove the multi-index structure generated by yfinance.

This results in a clean and structured table with one row per trading day and six essential variables. This dataset serves as the basis for all subsequent steps of the project, including feature engineering, time-series preprocessing and model training.


# Data Analysis and Strategy Setup - STEP 2 

This first stage focuses on understanding the financial dataset and establishing the foundations of the modelling strategy. After extracting historical market data for AAPL, we begin with an exploratory analysis to observe price evolution, volatility behaviour, volume patterns and the overall structure of the time series. This initial inspection highlights the stock’s dynamics and reveals elements such as trends, market regimes and seasonality.

Based on this analysis, we define a modelling approach centred on predicting short-term price direction rather than exact price levels. The dataset is then enriched with technical indicators commonly used in trading, such as returns, momentum, moving averages, RSI, MACD and volatility—to capture market behaviour more precisely. These engineered features, combined with the temporal nature of the data, provide a solid foundation for the predictive modelling carried out in the next stages of the project

# Data Analysis and Strategy Refinement – STEP 3

The objective of this stage is to re-evaluate the initial modelling strategy and improve the overall structure of the project. Based on the results obtained in the previous steps, we revisit the feature engineering process,the modelling choices and the evaluation methodology in order to optimise predictive performance.

This step involves rewriting and refining parts of the code to improve clarity, efficiency and robustness, as well as tuning hyperparameters more systematically using cross-validation techniques adapted to time series data.

To support this analysis, we rely on visual tools such as heatmaps and comparative graphs to assess model performance, parameter sensitivity and feature importance across different approaches.
These visualisations help highlight strengths and weaknesses of each strategy and guide the final optimisation decisions.
