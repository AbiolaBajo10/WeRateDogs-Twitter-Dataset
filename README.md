# WeRateDogs Tweet Archive Data

## by Abiola Ogunbajo


## Dataset
The dataset for this project is the tweet archive of Twitter user @dog_rates, also known as WeRateDogs. WeRateDogs is a Twitter account that rates people's dogs with a humorous comment about the dog. To perform an analysis, the following datasets was needed:
1. The WeRateDogs Twitter archive
2. The tweet image predictions
3. Additional data from the Twitter API(retweet_count, favorite_count)

### Gathering

#### The WeRateDogs Twitter archive

The WeRateDogs Twitter archive data was provided by Udacity as 'twitter_archive_enhanced.csv' file. I downloaded the data manually, uploaded it locally on the jupyter notebook and read it into a pandas DataFrame (twitter_df).

#### The tweet image prediction

This file (image_predictions.tsv) is present in each tweet according to a neural network. It is hosted on Udacity's servers and was downloaded programmatically using the Requests library and a URL provided by Udacity. This dataset was read into a pandas dataframe (image_df).

#### Additional data from the Twitter API(retweet_count, favorite_count)

Each tweet's retweet count and favorite ("like") count was gathered using the tweet IDs in the WeRateDogs Twitter archive. I queried twitter API for each tweet's JSON data using Python's Tweepy library and each tweet's entire set of JSON data  was stored in a file called tweet_json.txt file.

Each tweet's JSON data was written to its own line and read into a .txt file line by line. Finally, I read this .txt file into a pandas DataFrame (tweet_count) with (at minimum) tweet ID, retweet count, and favorite count.

### Assessing

The three datasets were assessed in two ways which are the visual assesssment and programmatic assessment.
#### 1. Visual Assessment -

I opened the twitter_df (twitter_archive_enhanced dataframe) in a spreadsheet, printed the image_df and tweet_count in the jupyter notebook. I scrolled through the columns and rows of these dataframes to find issues present.

#### 2. Programmatic Assessment - 

The three dataframes were assessed programmatically using some pandas method such as .head(), .tail(), .info(), . describe(), .sample(), .duplicated(), .isnull(), and attributes such as .shape. I identified quality issues and tidiness isues. The following were observed from the programmatic assessment on the three dataframes.

#### Quality Issues

twitter_df table
- Retweets present in the dataset.
- Missing values in some columns.
- Erroneous datatype in the timestamp column.
- Nulls represented as None in the name column.
- Incorrect ratings in rows 313, 516 and 2335. 
- The name column consists of lowercase names.

image_df table
- Non-descriptive column names.
- The columns: p1, p2 and p3 have lowercase variables and uppercase variables

#### Tidiness Issues

twitter_df
- The columns doggo, floofer, pupper and puppo should be in a single column 'dog types'
- Redundant columns: text column.

twitter_df, image_df and tweet_count
- The three dataframes should be in one dataframe.

### Cleaning

Before cleaning, I made copies of the three dataframes.I defined the issue, wrote the cleaning code and tested the cleaning code to know if it worked. 
The issues that were assessed in the second wrangling step were cleaned in the following ways:
- I dropped the retweets in the first dataframe because we only need the original tweets
- I dropped the columns with missing values.
- The tidiness issues were cleaned next. 
- Followed by the quality issues which were properly cleaned.
- Lastly, the general tidiness issue was cleaned by merging the three dataframes.

The merged dataframe was stored in a csv file named "twitter_archive_master.csv".


## Summary of Findings
Some of the insights found from the analysis are:

The minimum and maximum number for the retweet_count(the number of retweets for a tweet) is 11 and 70742 respectively.
The minimum and maximum number for the favorite_count(the number of retweets for a tweet) is 66 and 144891 respectively.
Most dogs are pupper.
Dogs with multiple stages(doggo, puppo) have the highest mean retweet_count and favorite_count.


