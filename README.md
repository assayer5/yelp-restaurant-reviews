
## Project: Yelp Restaurant Reviews

### Overview
Analysis of 2M+ Yelp users and 5M+ restaurant reviews to develop a data driven strategy to pick a delicious meal, applying VADER sentiment analysis and visualized with matplotlib, seaborn

VADER sentiment analysis done with cleaned review text and then also just with sentence tokenization. Data processing adapted to work for distributed computing with PySpark.

### Language
Python

### Packages Used
json, numpy, pandas, matplotlib, seaborn, nltk, scipy, pyspark

### Data Cleaning and Preparation
- converted json files to csv files
- selected subset of data (restaurants only)
- parsed dates to generate new features
- filled or dropped zero and nan values
- sentence or word tokenized, cleaned, POS-tagged, and lemmatized review text

### Sentiment Analysis
- VADER sentiment analysis	

### Insights into Yelp restaurant reviews
- Around 30% of the users have written 1 review on Yelp
- Almost 60% of the users had <=10 reviews
- Users with a single review likely share more extreme experiences since their ratings tended to be either 1 star or 5 stars.
- Some users only give reviews after poor experiences. Their average rating remains near 1 star even as their review count increases.
- 'Active users' with 10-30 reviews/year comprised almost 20% of the restaurant reviews even though they represent less than 10% of the users. These users regularly review restaurants and generally have more than 100 reviews total. Since their average rating as a group is about 4 stars, these reviews may describe the typical restaurant experience.
- Beware of users with several hundred or thousands of reviews. They are a small fraction of users and may be fake reviews since it seems unlikely that someone would write 100+ genuine reviews/year. Although reviews from these types of users were present in about half the restaurants, they represent less than 2% of the 'Yelp recommended' reviews so it's likely that they are screened out.

- My hypothesis that 4 star reviews are somehow more objective than 5 star reviews appears to be somewhat correct when VADER neutral sentiment is used as a measure of objectivity. The mean neutrality score of the 4 star reviews (61%) is slightly higher than the 5 star reviews (56.5%), with a slightly narrower spread, and a t-test shows that the means are significantly different (p-value = 0). However, although the difference between the two distributions is statistically significant (probably due to the massive sample size), the Cohen's d effect size (d = 0.36) is small to moderate, indicating a rather minimal difference in neutrality between 4 and 5 star reviews, and in this context, probably indescernible to the reader of restaurant reviews.



### Resources
[Yelp Open Dataset](https://www.yelp.com/dataset)

[VADER sentiment analysis](https://github.com/cjhutto/vaderSentiment)

[Databricks Community Edition](https://community.cloud.databricks.com/)

[PySpark 3.0.0 documentation](https://spark.apache.org/docs/3.0.0/api/python/pyspark.sql.html)

[Kaggle](https://www.kaggle.com/)
