​       

```python
FTSE_historical = pd.read_csv('/Users/ataiotorbaev/Desktop/General_Assembly_DSI/DSI13-lessons/project/project-capstone/FTSE_data/FTSE_HistoricalPrices.csv')
FTSE_historical.Date = pd.to_datetime(FTSE_historical.Date)
FTSE_historical = FTSE_historical.sort_values(by = 'Date', ascending=True).reset_index(drop=True)
FTSE_historical['Returns'] = FTSE_historical[' Close'].pct_change()
FTSE_historical = FTSE_historical.rename(columns={'Date': 'bindate',' Close': 'Close'}).set_index('bindate')[['Close', 'Returns']]
FTSE_historical
```





