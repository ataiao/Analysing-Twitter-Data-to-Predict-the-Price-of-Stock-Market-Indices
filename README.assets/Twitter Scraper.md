​       

```python
def my_pmap(f,jobs,num_procs=10):  
    return Parallel(n_jobs=num_procs)(delayed(f)(i) for i in jobs)
  
from datetime import datetime
from time import time,sleep
num_tweets = 1200
want_incremental = True
num_tweets_enc = 0
start_time = time()
dt_range = pd.date_range(start=datetime(2007, 2, 1),  end =datetime(2020, 8, 15))
index = 'FTSE'
def datewise(dt):
        if (os.path.exists(f'Equity_sentiment_twitter/tweets_{index}_{dt:%Y%m%d}.csv') and want_incremental):
            return
        print(f' i am inside date {dt:%Y%m%d}')
        successful_api_call= False
        while successful_api_call==False:
            try:
                tweetCriteria = got.manager.TweetCriteria().setQuerySearch(f'{index}')\
                                               .setSince(f'{dt:%Y-%m-%d}')\
                                               .setUntil(f'{dt+pd.Timedelta(days=1):%Y-%m-%d}')\
                                               .setMaxTweets(num_tweets)\
                                               .setEmoji("unicode")\
                                               .setLang('english')
                tweet = got.manager.TweetManager.getTweets(tweetCriteria)
                successful_api_call = True
            except:
                print(f'Encountered an error. Retrying.')
                
        print(f'Day tweets = {len(tweet)}')
        df = pd.DataFrame(columns=['date','text', 'username', 'hashtags', 'favorites', 'retweets', 'mentions', 'replies'])
        for i in range(0, len(tweet)):
            mydict = {'author_id':tweet[i].author_id, 'date':tweet[i].date,'text':tweet[i].text, 'username':tweet[i].username, 'hashtags':tweet[i].hashtags, 'retweets':tweet[i].retweets, 'favorites':tweet[i].favorites, 'mentions':tweet[i].mentions, 'replies':tweet[i].replies}
            df = df.append(mydict,ignore_index=~True)
        df.to_csv(f'Equity_sentiment_twitter/tweets_{index}_{dt:%Y%m%d}.csv')
        


my_pmap(datewise,dt_range,num_procs=-1)
```



