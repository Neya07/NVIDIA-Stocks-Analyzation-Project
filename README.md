#Conducting Microchip Research: An Analyzation of NVIDIA Corporation Stocks

#### Bar Graph of the Top 10 Semiconductor Companies -->

import pandas as pd
import matplotlib.pyplot as plt

data = pd.read_csv(r"Top_Semiconductors_Companies.csv")
data = data.head(10)
data['Market Cap (USD)'] = data[' Market Cap (USD) '].replace('[\$,]', '', regex=True).astype(float)
colors = ['#76b900','#ce0631','#f20c1b','#009a66','#137cc1','#3254dc', '#bd382f', '#0070b8', '#121c84', '#f58025']
plt.figure(figsize=(20, 13))
bars = plt.bar(data['Company'], data['Market Cap (USD)'], color=colors)
plt.title('Market Capitalization of the Top 10 Semiconductor Companies', fontsize=34, fontname='Impact')
plt.xlabel('Company Name', fontsize=25, fontweight='bold', fontname='Monospace')
plt.ylabel('Market Cap (USD)', fontsize=25, fontweight='bold', fontname='Monospace')
plt.xticks(rotation=85, fontsize=14, fontname='Verdana')

for bar in bars:
    yval = bar.get_height()
    plt.text(bar.get_x() + bar.get_width()/2, yval, f'{yval:,.0f}', ha='center', va='bottom', fontsize=10, fontname='Verdana')

plt.show()

#### Line Graph of Nvidia's Stocks of May -->

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"NVDA (1).csv")
data = data.iloc[6359:6381]
data['Date'] = pd.to_datetime(data['Date'])


plt.figure(figsize=(14, 6))
plt.plot(data['Date'], data['Close'], linestyle='-', color='#76b900')
plt.title('NVIDIA Closing Stock Prices of May 2024', fontsize=34, fontweight='bold', fontname='Impact')
plt.ylabel('Closing Price (USD)', fontsize=22, fontweight='bold', fontname='Monospace')
plt.xlabel('Date', fontsize=22, fontweight='bold', fontname='Monospace')

plt.xticks(rotation=45, fontsize=10, fontname='Verdana')
plt.yticks(fontsize=10, fontname='Verdana')
plt.ylim(0, data['Close'].max() + 20)
plt.grid(True)

plt.show()

#### OHLC Chart of Nvidia's Stocks of May -->

import pandas as pd
import mplfinance as mpf

data = pd.read_csv(r"NVDA (1).csv")
data = data.iloc[6359:6381]

data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)
y_min = 0
y_max = data[['High']].max().max()

mpf.plot(data, type='ohlc', style='checkers', title='NVIDIA Stock Prices in May 2024', ylabel='Prices (USD)', xlabel='Date', ylim=(y_min, y_max))

#### LINE GRAPH OF NVIDIA STOCKS 1999-2024 -->

import pandas as pd
import matplotlib.pyplot as plt
data = pd.read_csv(r"NVDA (1).csv")
data = data.iloc[[0, 239, 491, 739, 991, 1243, 1495, 1747, 1998, 
2249, 2502, 2754, 3006, 3258, 3508, 3760, 4012, 4264, 4516, 
4767, 5018, 5270, 5523, 5775, 6026, 6276]]
data['Date'] = pd.to_datetime(data['Date'])


plt.figure(figsize=(14, 6))
plt.plot(data['Date'], data['Close'], linestyle='-', color='#76b900')
plt.title('NVIDIA Closing Stock Prices Through 1999-2024', fontsize=34, fontweight='bold', fontname='Impact')
plt.ylabel('Closing Price (USD)', fontsize=22, fontweight='bold', fontname='Monospace')
plt.xlabel('Date', fontsize=22, fontweight='bold', fontname='Monospace')

plt.xticks(rotation=45, fontsize=10, fontname='Verdana')
plt.yticks(fontsize=10, fontname='Verdana')
plt.ylim(0, data['Close'].max() + 10)

plt.grid(True)
plt.show()

#### OHLC CHART OF NVIDIA STOCKS 1999-2024 -->
import pandas as pd
import mplfinance as mpf

data = pd.read_csv(r"NVDA (1).csv")
data = data.iloc[[0, 239, 491, 739, 991, 1243, 1495, 1747, 1998, 
2249, 2502, 2754, 3006, 3258, 3508, 3760, 4012, 4264, 4516, 
4767, 5018, 5270, 5523, 5775, 6026, 6276]]

data['Date'] = pd.to_datetime(data['Date'])
data.set_index('Date', inplace=True)
y_min = 0
y_max = data[['High']].max().max()

mpf.plot(data, type='ohlc', style='checkers', title='NVIDIA Stock Prices Through 1999-2024', ylabel='Prices (USD)', xlabel='Date', ylim=(y_min, y_max))

