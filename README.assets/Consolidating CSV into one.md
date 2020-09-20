​       

```python
df = []
# dt_range = pd.date_range(start=datetime(2011,1,1),end=datetime(2011,1,31))
for dt in dt_range:
    print(f' i am inside date {dt:%Y%m%d}')
    if not os.path.exists(f'Equity_sentiment_twitter/tweets_{index}_{dt:%Y%m%d}.csv'):
        continue
    df.append(pd.read_csv(f'Equity_sentiment_twitter/tweets_{index}_{dt:%Y%m%d}.csv'))
df = pd.concat(df,ignore_index=True)
df.text = df.text.astype(str)
if not os.path.exists(f'Equity_sentiment_twitter/{index}_consolidated'):
    os.mkdir(f'Equity_sentiment_twitter/{index}_consolidated')
df.to_csv(f'Equity_sentiment_twitter/{index}_consolidated/tweets_and_sentiment_consolidated.csv')
df['score'] = df.text.apply(lambda x: sentiment_analyzer_scores(x))
df.to_csv(f'Equity_sentiment_twitter/{index}_consolidated/tweets_and_sentiment_consolidated_with_sentiment.csv')

```



