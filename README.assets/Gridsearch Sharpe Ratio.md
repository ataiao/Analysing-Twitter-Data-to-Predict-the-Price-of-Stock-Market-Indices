​       

```python
import itertools
list(itertools.permutations([0.1, 0.2, 0.3, 0.4]))
```

The ratio describes how much excess return you receive for the extra volatility you endure for holding a riskier asset

```python
wts = list(itertools.permutations([0.1, 0.2, 0.3, 0.4]))
wts = wts+[(1,0,0,0), (0,1,0,0), (0,0,1,0), (0,0,0,1)]
lookbacks = [5] + list(range(22,22*13,22))

def calc_sharpe(lookback, wt):
    pos = wt[0]*ftse13.score + wt[1]*ftse13.score_retweets + wt[2]*ftse13.score_replies + wt[3]*ftse13.score_favorites
    pos = pos - pos.rolling(window=lookback, min_periods=1).mean()  #subtract bias, takes the average over a different period
    # position vector long or short it
    # todays sentiment subtracted the last 3month
    pos = np.sign(pos)#convert to 1 or -1
    pnl = pos.shift(1) * ftse.Returns
    sharpe = np.sqrt(252) * pnl.mean()/pnl.std()#pnl standard profit and loss
    return sharpe

maxsharpe = 0 
maxvars = None
for wt in wts:
    for lookback in lookbacks:
        sharpe = calc_sharpe(lookback, wt)
        if sharpe > maxsharpe:
            maxsharpe =sharpe
            maxvars = (wt, lookback)
            
print(maxsharpe)
print(maxvars)
```

```python
for var in ['score', 'score_retweets', 'score_replies', 'score_favorites', 'optimal_score']:
    pos = ftse13[var]
    print(var)
    pos = pos - pos.rolling(window=5,min_periods=1).mean()  #subtract bias
    pos = np.sign(pos)#convert to 1 or -1
    pnl = pos.shift(1) * ftse.Returns
    sharpe = np.sqrt(252) * pnl.mean()/pnl.std()#pnl standard profit and loss
    print(sharpe)
    
```