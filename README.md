# **Recommendation-Systems**

## **Introduction:**
This is a competition project has been done in fulfillment to the completion of Foundations and applications of Data Minig(INF553) course at University of Southern California. The work on the project was all done by myself.

The project objective is to build a hybrid recommendation engine by mixing recommendations from content-based filtering, user-based and item-based collaborative filtering recommendation models.

**In this project, all the Data Mining and recommendation algorithms are implemented without using any library from scratch**. Coding and implementing the algorithms without using libraries helps us in better understanding of them and use the algorithms as per our input data and requirements.

**This Recommendation project stood at second place in a class of 106 students at Data Mining class Spring 2020 and the rankings are given as per RMSE.** 

## **Problem:**

Recommendation systems have become an integral part of many businesses. They produce individualized recommendations as output or have the effect of guiding the user in a personalized way to interesting objects in a larger space of possible options.

In this project, we want to apply machine learning and data mining algorithms to develop predictive models and hence build a hybrid restaurant recommendation system that suggests the most suitable restaurants for users based on their preferences. This is done by predicting the ratings given by a user on a particular business unit.

## **Dataset description:**
This project uses the Yelp dataset available at https://www.yelp.com/dataset

The data set contains 4,700,000 reviews on 156,000 businesses in 12 metropolitan areas 1,000,000 tips by 1,100,000 users Over 1.2 million business attributes like hours, parking, availability, and ambience.

The data files are supplied in two flavours: json and SQL (MySQL, Postgres). This project utilizes the json version which has the following files:

**business.json:** Contains business data including location data, attributes, and categories.

**review.json:** Contains full review text data including the user_id that wrote the review and the business_id the review is written for.

**user.json:** User data including the user's friend mapping and all the metadata associated with the user.

**user_avg.json:** User average rating for all the business units.

**business_avg.json:** business unit average is given as file.

**checkin.json:** Checkins on a business.

**tip.json:** Tips written by a user on a business. Tips are shorter than reviews and tend to convey quick suggestions.
photos: (from the photos auxiliary file) This file is formatted as a JSON list of objects.
Each file is composed of a single object type, one JSON-object per-line. Description available at (https://www.yelp.com/dataset/documentation/json)

As the focus of this project is on building a recommendation engine, the core files will be used are business.json, review.json, and user.json. Additionally, taking into consideration the limited hardware resources used available, data for the city of Toronto will be considered for building the recommendation engine.

## **Approach:**

Both content-based filtering and user and item based collaborative filtering have their strengths and weaknesses. We plan to mix both recommendations methods in addition to Friends ratings to provide a better personalized recommendation system.

Yelp users give ratings and write reviews about businesses and services on Yelp. These reviews and ratings help other Yelp users to evaluate a business or a service and make a choice. While ratings are useful to convey the overall experience, they do not convey the context which led a reviewer to that experience. We plan to apply various Natural Language Processing (NLP) and Text Analytics techniques on the review text to build features for the content filtering recommendations. The ratings will be used in the collaborative filtering recommendations.

A hybrid recommendation engine will be built to mix the results of the three above recommendations methods. Moreover, key words search recommendations will also be developed based on the featurizaion built on the content filtering part, to accommodate cold-start problem, i.e. new users with no history in the system.

Apache Spark (https://spark.apache.org/) is a fast and general engine for big data processing, with built-in modules for streaming, SQL, machine learning and graph processing. Parquet files generated by Apache Drill will be loaded into Spark dataframes for further analysis and machine learning modeling.


## **Content-based recommendation system:**

In this task, we build a content-based recommendation system by generating profiles from review
texts for users and businesses in the train review set. Then I use the system/model to predict if a
user prefers to review a given business, i.e., computing the cosine similarity between the user and item
profile vectors.
During the training process, we constructed business and user profiles as the model:
* Concatenating all the review texts for the business as the document and parsing the document, such
as removing the punctuations, numbers, and stopwords. Also, we removed extremely rare words
to reduce the vocabulary size, i.e., the count is less than 0.0001% of the total words.
* Measuring word importance using TF-IDF, i.e., term frequency * inverse doc frequency
* Using top 200 words with highest TF-IDF scores to describe the document
* Creating a Boolean vector with these significant words as the business profile
* Creating a Boolean vector for representing the user profile by aggregating the profiles of the items
that the user has reviewed
During the predicting process, we estimated if a user would prefer to review a business by computing
the cosine distance between the profile vectors. The (user, business) pair will be considered as a valid
pair if their cosine similarity is >= 0.01. We only output these valid pairs. 

## **Collaborative Filtering Recommendation Systems:**

In this task, we built collaborative filtering recommendation systems with train reviews and used the
models to predict the ratings for a pair of user and business. We implemented in two cases:

## **User-based CF recommendation system:**

In this, during the training process, we built a model by computing the **Pearson correlation** for the
business pairs that have at least three co-rated users. 

During the predicting process, we used the model to predict the rating for a given pair of user and business. we used at most N business neighbors that are most similar to the target business for prediction (N=3).

## **Item-based CF recommendation system:**

In item-based CF recommendation system, during the training process, since the number of potential user pairs is too large to
compute, we combined the Min-Hash and LSH algorithms in our user-based CF recommendation
system. You need to 
* identify user pairs who are similar using their co-rated businesses without
considering their rating scores . This process reduced the number of user pairs we need to compare for the final Pearson correlation score. 
* computed the Pearson correlation for the user pair candidates that have Jaccard similarity >= 0.01 and at least three co-rated businesses. The predicting process is similar to User-based CF recommendation System.

## **Result:**

This recommendation engine predicted user ratings on certain business with an rmse of 1.17269 on test dataset and 1.17078 on blind dataset.






