
## Project: Yelp Restaurant Reviews

### Overview
Analyzed of 2M+ Yelp users and 5M+ restaurant reviews to develop a data driven strategy to pick a delicious meal: applied VADER sentiment analysis and visualized with matplotlib, seaborn. Data processing adapted to work for distributed computing with PySpark.

### Some Details
The Yelp dataset contained review data for multiple business categories. I chose to focus on the restaurant reviews and analyzed the sentiment differences between different ratings (i.e. 4 versus 5 star reviews).

Data cleaning and preparation:
- *yelp-dataset-generate-csv-files.ipynb*
>I converted json files to csv files and selected a subset of the data (restaurants reviews only).
>
- *yelp-dataset-eda.ipynb*
>I explored the user data and review counts, parsed dates to generate new features, and filled or dropped zero and nan values. With a few plots, I looked at the distribution of the average rating for subsections of users.

Sentiment analysis:
- *yelp-dataset-sentiment-analysis_byword.ipynb*
>Since millions of reviews needed processing for sentiment analysis, I preprocessed the reviews in chunks to avoid memory issues. I word tokenized, cleaned, POS-tagged, and lemmatized the review text before applying VADER sentiment analysis. 
>
- *yelp-dataset-sentiment-analysis_bysentence.ipynb*
>VADER sentiment analysis was originally designed to look at sentiment at the sentence level (rather than word level). In this notebook, I cleaned and sentence tokenized the review text before applying VADER sentiment analysis. Again, I preprocessed the reviews in chunks to avoid memory issues.
>
- *yelp-dataset-sentiment-analysis-bysentence-distributed.ipynb*
>To better handle the large number of reviews, I adapted the sentence tokenization and VADER sentiment analysis to utilize distributed computing. I created user defined functions with PySpark to process the review text.

With VADER sentiment analysis, each review was scored for positive, negative, and neutral sentiment. I used these sentiment scores to compare the sentiment between 4 and 5 star reviews with a t-test. To get a sense of the magnitude of the sentiment differences, I used Cohen's D test for effect size.

Insights into Yelp restaurant reviews:
- Around 30% of the users have written 1 review on Yelp
- Almost 60% of the users had <=10 reviews
- Users with a single review likely share more extreme experiences since their ratings tended to be either 1 star or 5 stars.
- Some users only give reviews after poor experiences. Their average rating remains near 1 star even as their review count increases.
- 'Active users' with 10-30 reviews/year comprised almost 20% of the restaurant reviews even though they represent less than 10% of the users. These users regularly review restaurants and generally have more than 100 reviews total. Since their average rating as a group is about 4 stars, these reviews may describe the typical restaurant experience.
- Beware of users with several hundred or thousands of reviews. These users are a small fraction of users and may be fake reviews since few users would write 100+ genuine reviews/year. Although reviews from these types of users were present in about half the restaurants, they represent less than 2% of the 'Yelp recommended' reviews so it's likely that many of these reviews are screened out.

- When VADER neutral sentiment is used as a measure of objectivity, my hypothesis that 4 star reviews are somehow more objective than 5 star reviews appears to be statistically true, but not practically true. The mean neutrality score of the 4 star reviews (61%) is slightly higher than the 5 star reviews (56.5%), with a slightly narrower spread, and a t-test shows that the means are significantly different (p-value = 0). However, although the difference between the two distributions is statistically significant (probably due to the massive sample size), the Cohen's d effect size (d = 0.36) is small to moderate, indicating a rather minimal difference in neutrality between 4 and 5 star reviews. In this context, any difference in sentiment between the 4 and 5 star reviews is probably indescernible to the reader of the reviews.

### Language
Python

### Packages Used
json, numpy, pandas, matplotlib, seaborn, nltk, scipy, pyspark

### Resources
[Yelp Open Dataset](https://www.yelp.com/dataset)

[VADER sentiment analysis](https://github.com/cjhutto/vaderSentiment)

[Databricks Community Edition](https://community.cloud.databricks.com/)

[PySpark 3.0.0 documentation](https://spark.apache.org/docs/3.0.0/api/python/pyspark.sql.html)

[Kaggle](https://www.kaggle.com/)
