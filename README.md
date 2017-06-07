# Stock_prediction_using_ML_and_Deep_learning
This is our final project for STA 208: Principles of Machine Learning, Spring 2017, UC Davis
__Authors:__ Zamir Akimbekov and Pamela Patterson

__Description of Project:__ Our goal is to determine if there is a relationship between sentiment (positive or negative) of news about Apple, Inc. on a given day and whether the stock for that company rises or falls in price on that same day. 

__Method:__ 
__News Articles__ We first scraped Motley Fool for news articles with the company name as a search criteria. We retrieved 3 years of news data so that we could analyze 3 years of stock data in conjunction. We then made a sentiment scoring algorithm in which we use a list of negative words and a list of positive words commonly found in financial news to give each article a total score. One occurance of a positive word gives a point value of +1, while one occurance of a negative word gives a point value of -1. Our algorithm takes the total from the entire article as the sentiment score. This score is added as a column to the dataframe containing the news articles. We then add a column that counts how many times the word "Apple" is mentioned in each article, then we filter the dataframe to only include articles that mention Apple more than a threshold, in our case we chose 5 times. Finally, we sort the dataframe by date and choose the subset of columns containing date and sentiment score so we can merge it with the stock data. 

__Stock Data__ We used quandl.com to retrieve stock data for Apple. We add a column called "diff" that calculates the difference in ending price and beginning price for each day. After merging with the news dataframe, we add two colums that give binary values to the two features we are interested in: sentiment and diff. So a positive sentiment gets a score of 1, a negative sentiment gets a score of -1, a positive "diff" gets a score of 1, and a negative "diff" gets a score of -1. Sentiments and "diff" scores equal to 0 get a score of 0, so that our classification problem has 3 classes. 

__Classification__ We separate the data from the last 3 years into a training set and a testing set. Since this is time series data, we don't do this randomly. Instead, the training data consists of the first 2 years, and the test set is the last 1 year. The training set has all of the labels in tact, while the test set ignores the score for the stock difference for each day. We want to see if we can predict if the price will rise, fall, or stay the same based on the news sentiment of that day. 
[__Finish talking about method of classification__]

__Results__ 

