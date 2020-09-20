​       

```python
from pandas.tseries.offsets import BDay
df.date = pd.to_datetime(df.date)
df['hours'] = df['date'].dt.hour
df['new_date'] = pd.to_datetime(df['date'].dt.date)
df['bindate'] = np.where(df['hours']<16,df['new_date']+BDay(0),df['new_date']+BDay(1))
df = df.set_index('bindate')
df.to_csv(f'Equity_sentiment_twitter/{index}_consolidated/tweets_and_sentiment_consolidated_with_sentiment_binned.csv')
print(df[['date','hours','new_date']])
df = df[df.score!=0]
print(df[['date','hours','new_date']])

for var in ['retweets','favorites','replies']: #Weighing the columns
    df[f'score_{var}'] = df.score * df[var]
df = df.groupby(df.index).agg({'score':'mean','score_retweets':'sum','score_replies':'sum','score_favorites':'sum','retweets':'sum','favorites':'sum','replies':'sum'})
for var in ['retweets','favorites','replies']:
    df[f'score_{var}']  = df[f'score_{var}']  / df[var].replace(0,1)
df
#df.to_csv(f'Equity_sentiment_twitter/{index}_consolidated/tweets_and_sentiment_consolidated_with_sentiment_binned.csv')



```



