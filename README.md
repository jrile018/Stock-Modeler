This repository contains Python code for fetching and analyzing historical stock data using the yfinance library. The script downloads data for the SPY and QQQ ETFs, calculates log returns, and plots cumulative returns.

Prerequisites
Make sure you have the following libraries installed:

yfinance
pandas
pandas_datareader
datetime
numpy
matplotlib

First, import the necessary libraries:

import yfinance as yf
import pandas as pd
from pandas_datareader import data as pdr
import datetime as dt
import numpy as np
import matplotlib.pyplot as plt

Define Date Range

endDate = dt.datetime.now()
startDate = endDate - dt.timedelta(days = 365*5)

Download Stock Data

stocks = ["SPY", "QQQ"]
df = yf.download(stocks, start = startDate, end = endDate)
print(df.head())

Extract Adjusted Close Prices

adj_close_prices = df['Adj Close']
adj_close_prices.head()

Calculate Log Returns

log_returns = np.log(adj_close_prices/adj_close_prices.shift(1))
log_returns.head()

Calculate Cumulative Log Returns

cumulative_log_returns = log_returns.cumsum()
print(cumulative_log_returns)

Plot Cumulative Returns

cumulative_log_returns.plot(title = "Cumulative Returns", figsize =(10,6))
plt.show()



Acknowledgments
yfinance
pandas
numpy
matplotlib
