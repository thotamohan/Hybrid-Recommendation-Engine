# **Recommendation-Systems**

## **Introduction:**
This is a competition project has been done in fulfillment to the completion of Foundations and applications of Data Minig(INF553) course at University of Southern California. The work on the project was all done by myself.

The project objective is to build a hybrid recommendation engine by mixing recommendations from content-based filtering, user-based and item-based collaborative filtering recommendation models.

**In this project, all the Data Mining and recommendation algorithms are implemented without using any library from scratch**. Coding and implementing the algorithms without using libraries helps us in better understanding of them and use the algorithms as per our input data and requirements.

**This project stood at third place in a class of 106 students at Data Mining class Spring 2020 and the rankings are given as per RMSE.** 

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


