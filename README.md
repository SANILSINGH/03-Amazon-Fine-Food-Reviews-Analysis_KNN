# 03-Amazon-Fine-Food-Reviews-Analysis_KNN

Data Source: https://www.kaggle.com/snap/amazon-fine-food-reviews

EDA: https://nycdatascience.com/blog/student-works/amazon-fine-foods-visualization/

### Objective:

Given an Amazon fine food reviews, determine whether the review is positive (rating of 4 or 5) or negative (rating of 1 or 2).

### Data Description

The Amazon Fine Food Reviews dataset consists of reviews of fine foods from Amazon.

Number of reviews: 568,454 Number of users: 256,059 Number of products: 74,258 Timespan: Oct 1999 - Oct 2012 Number of Attributes/Columns in data: 10

#### coloumns

1. Id
2. ProductId - unique identifier for the product
3. UserId - unqiue identifier for the user
4. ProfileName
5. HelpfulnessNumerator - number of users who found the review helpful
6. HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not
7. Score - rating between 1 and 5
8. Time - timestamp for the review
9. Summary - brief summary of the review
10. Text - text of the review

#### Sample Data:

1 B001E4KFG0 A3SGXH7AUHU8GW delmartian 1 1 1 1303862400 Good Quality Dog Food I have bought several of the Vitality canned d...

1 2 B00813GRG4 A1D87F6ZCVE5NK dll pa 0 0 0 1346976000 Not as Advertised Product arrived labeled as Jumbo Salted Peanut

## Exploratory Data Analysis
###Data Cleaning: Deduplication

It is observed that the reviews data had many duplicate entries. Hence it was necessary to remove duplicates in order to get unbiased results for the analysis of the data

It was inferred after analysis that reviews with same parameters other than ProductId belonged to the same product just having different flavour or quantity. Hence in order to reduce redundancy it was decided to eliminate the rows having same parameters.

The method used for the same was that we first sort the data according to ProductId and then just keep the first similar product review and delelte the others. for eg. in the above just the review for ProductId=B000HDL1RQ remains. This method ensures that there is only one representative for each product and deduplication without sorting would lead to possibility of different representatives still existing for the same product.

## Preprocessing
### Preprocessing Review Text

Now that we have finished deduplication our data requires some preprocessing before we go on further with analysis and making the prediction model.

Hence in the Preprocessing phase we do the following in the order below:-


1. Id
2. ProductId - unique identifier for the product
3. UserId - unqiue identifier for the user
4. ProfileName
5. HelpfulnessNumerator - number of users who found the review helpful
6. HelpfulnessDenominator - number of users who indicated whether they found the review helpful or not
7. Score - rating between 1 and 5
8. Time - timestamp for the review
9. Summary - brief summary of the review
10. Text - text of the review
11. 
12.Begin by removing the html tags
13.Remove any punctuations or limited set of special characters like , or . or # etc.
14.Check if the word is made up of english letters and is not alpha-numeric
15.Check to see if the length of the word is greater than 2 (as it was researched that there is no adjective in 2-letters)
16.Convert the word to lowercase
17.Remove Stopwords
18.Finally Snowball Stemming the word (it was obsereved to be better than Porter Stemming)

After which we collect the words used to describe positive and negative reviews

## Featurization
### BAG OF WORDS
### Bi-Grams and n-Grams.
### TF-IDF
### Word2Vec
### Avg W2v
### TFIDF weighted W2v
