​       

```python
from vaderSentiment.vaderSentiment import SentimentIntensityAnalyzer
analyzer = SentimentIntensityAnalyzer()
pos_words = ['up','bull','high']
neg_words = ['down','bear','low']
uncertain_words = ['shaky']
words = pd.read_csv('finance_dict.csv')
for col in words.columns:
    words[col] = words[col].str.lower()
pos_words = pos_words + list(words.positive)
neg_words = neg_words + list(words.negative)
uncertain_words = uncertain_words + list(words.uncertain)

new_words_dict = {}
for word in pos_words + neg_words + uncertain_words:
    if word in pos_words:
        new_words_dict[word] = 1
    elif word in neg_words:
        new_words_dict[word] = -1
    else:
        new_words_dict[word] = -0.2

analyzer.lexicon.update(new_words_dict)
```



