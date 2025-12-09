Tesla stock price prediction

The goal of this project is to predict the close price of Tesla stock for the next day. We used historical data from 2020 to 2025 and applied technical analysis indicators to compare three different machine learning approaches and see which forecasting method is the most effective.



This work was done by \[TON NOM] and \[NOMS DES AUTRES MEMBRES] as students at ESILV in the financial engineering and data science major.



For the data, we fetched everything from Yahoo Finance using the yfinance API. We focused on feature engineering by calculating indicators like SMA, RSI, MACD and Bollinger bands to help the models. We implemented three main algorithms: a linear regression to serve as a baseline, an XGBoost ensemble method, and a deep learning LSTM model, which turned out to be the best performer. We also performed some data analysis including correlation heatmaps and PCA to check variance, along with overfitting checks.



The repository structure contains the full report in the reports folder, the main jupyter notebook with the code, the requirements file and this readme.

