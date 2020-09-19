# General Assembly Capstone Project: Analysing Twitter Data to Predict the Price of Stock Market Indices (FTSE)
<img src="README.assets/Screenshot 2020-09-17 at 08.35.43.png" style="width: 800px;">

## Abstract
The five-week final project for my General Assembly data science immersive programme. I built a model that predicted (FTSE) Index Stock Returns using Twitter Sentiment. The first step involved constructing the dataframe. I scraped Twitter and conducted Vader sentiment analysis on the dataset, I then downloaded the FTSE historical data, created the Returns column, and joined the two dataframes together to get the final dataset. 
The second step involves the application of modelling techniques on the dataset, I applied Linear Regression modelling. The results highlighted that this was a poor model, the predicted score was lower than the baseline (0.0.0022320050_LR). From a statistical point of view its a pretty bad model, but it is important to look from an economic perspective. 

For the final part of the project, I conducted a backtest and devised a trading strategy that predicted the direction and return of the FTSE index. I established cumulative P&L scores, which showed that from an economic perspective that it is a good course of action.

## Files in This Repository
- Presentation Slides: This was prepared to present the projectm findings, results, adn reccomendations to a non-technical audience
- Technical Report: This was prepared for reporting and explaining my project to a technical audience. It offers a detailed explanation of thea literature review, data cleaning, feature engineering process, exploratory data analysis, findings per research question, limitations and recommendations for future research.

#### - Jupyter notebook
  - Step 1: Dataset and Data Collection
  - Step 2: Data Cleaning and Exploratory Data Analysis
  - Step 3: Data Modelling
  - Step 4: Backtesting and Devising a Trading Strategy
  
## Problem Statement
The ability to predict asset prices would be highly valuable for investors and other parties. Consequently, the field of stock market prediction has received a great deal of attention from both academia and businesses. Behavioural finance research shows that our emotion and mood plays a large and important role in our financial decision-making.Therefore, it is reasonable to assume that the public sentiment, mood and opinion may affect the stock market prices and movements. For this project i aim to find out if sentiment extracted from Twitter can be used to predict the direction of Returns of a Stock Market Index.

## Objectives
Five-week final project for my General Assembly Data Science Immersive programme. 

I conducted an exploratory study; The aim of which was to investigate if sentiment expressed on Twitter has an effect on Price of Individual Stock Market Indices (FTSE).
- Can Twitter Data be used to predict the Price of an Index up to one day ahead?
- Is Twitter a suitable data source to help forecast future stock market movement?
## Hypothesis
1. Twitter Sentiment reflects the mood of the market.
2. Twitter can be used to predict the direction of future stock market movements.

# Project Layout

### Acquiring the Data
When starting this project, the biggest challenge i faced was scraping Twitter, and consolidating the DataFrame.
#### Scraping Twitter and Assign Sentiment Scores
Most time consuming part of the project.
<img src="README.assets/Screenshot 2020-09-17 at 08.35.05.png" style="width: 800px;">
### Parse: Understand the Data 

### Mine:Prepare Sturcture and Clean 

### Refine: EDA
#### - Correlation , Summary Statistics
Description of the process

### Modelling: Linear Regression
<img src="README.assets/Screenshot 2020-09-17 at 09.16.01.png" style="width: 800px;">
#### Results
The shifted regression will not be a good fit. But its good nevertheless, because i conducted a backtest which shows that economically it is good option.
Discuss the baseline and LR scores


### Backtesting & Devising a Trading Strategy
#### Make a Decision on which position to take based on Twitter sentiment at the closing time.
- Having a “long” position in a security means that you own the security. Investors maintain “long” security positions in the expectation that the stock will rise in value in the future. The opposite of a “long” position is a “short” position.
- A "short" position is generally the sale of a stock you do not own. Investors who sell short believe the price of the stock will decrease in value. If the price drops, you can buy the stock at the lower price and make a profit.
#### P&L Vector + Accumulated P&L
Choose a position either long or short depending on if the twitter sentiment score on a specific date is greater or lower than the last weeks/ 5 business days (time period) average.
#### Sharpe Ratio 
-  Sharpe Ratio is used to help investors understand the return of an investment compared to its risk. The ratio is the average return earned in excess of the risk-free rate per unit of volatility or total risk. Volatility is a measure of the price fluctuations of an asset or portfolio. Basically, reflects the consistency of the return.

- Sharpe Ratio Optimization/ Gridsearch
#### CAGR

#### Back to Mining creating a new optimal_score column 

### Part 4: Presentation
Presented the findings to a non-technical audience. Covering the goals, success criteria, challenges, findings, risks and limitations, the impact of the findings as well as the next steps and conclusion.

## Findings and Overview
- Accept the two hypothesis.

The results indicate that Twitter data is a suitable source to help understand and forecast future stock market movements.
Sentiment extracted from Twitter has significant predictive power for predicting the direction of stock Returns.

The Trading Strategy devised works, and proves that it is possible to generate profits over a large timeframe by only Twitter.
