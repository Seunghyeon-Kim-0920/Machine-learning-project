Data Preparation and Feature Engineering 

We used the yfinance library to retrieve historical TSLA stock data. The primary objective was to predict the next day's closing price, which served as our target variable.We engineered several technical indicators to capture market dynamics Simple moving averages (SMA_20 and SMA_50).
Momentum: Relative strength index (RSI) and moving average convergence divergence (MACD).
Volatility: Bollinger Bands.The data was cleaned by applying numeric conversions and removing null values created by the time-series calculations.

2. Machine Learning Comparison (Raw Price Prediction)
The data was chronologically split (80% Train, 20% Test) to maintain the time series integrity.The baseline model (Linear Regression) established an RMSE of 10.14. This model performs strongly because, in stock markets, the most effective predictor is often the previous day's price (Random Walk Theory).
We tried to optimize XGBoost parameters using RandomizedSearchCV. The model achieved an RMSE of 19.45, which indicates that the model struggles to extrapolate the continuous upward trend seen in the raw price data.

3. Deep Learning (LSTM)We prepared the data for the neural network by scaling prices (MinMax Scaler) and structuring it into 60-day sequences (Lookback).The model was a basic Keras sequential model, featuring one LSTM layer (50 units) followed by a Dense output layer. The LSTM model achieved an RMSE of 18.80, showing performance similar to the XGBoost model in predicting raw price values.

4. Advanced Approach: Predicting ReturnsRecognizing the difficulty in predicting volatile raw price values, we adopted a different strategy: predicting the daily percentage return instead of the absolute price. This transforms the data into a more stationary time series.We trained a new XGBoost regressor on the return feature. We then reconstructed the final price by applying the predicted return to the previous day's actual closing price: $P_{t+1} = P_t \times (1 + \text{Predicted Return})$.

This specialized model achieved an RMSE of 10.96, significantly outperforming the previous ML/DL models and closing the gap with the naive baseline.ConclusionWe concluded that predicting raw stock prices is generally less reliable than predicting price movements. The most robust result was achieved by predicting daily returns, which provided a stable forecast highly competitive with the basic Linear Regression benchmark.
