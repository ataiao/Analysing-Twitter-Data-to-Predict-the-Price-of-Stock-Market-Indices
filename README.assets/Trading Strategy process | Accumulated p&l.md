​       

```python
def plot_pnl(s):
    s = s.to_frame(name='Cumulative_P&L')
    s = s.reset_index()
    s.plot(kind='line', x='bindate', y='Cumulative_P&L', figsize=(12,9) )
for var in ['score', 'score_retweets', 'score_replies', 'score_favorites']:
    pos = ftse13[var]
    print(var)
    pos = pos - pos.rolling(window=5,min_periods=1).mean()  #subtracts bias
    # position vector long or short it
    pos = np.sign(pos)#convert to 1 or -1
    pnl = pos.shift(1) * ftse.Returns
    cumpnl = pnl.cumsum()
    plot_pnl(cumpnl)
    plt.title(var)
```



