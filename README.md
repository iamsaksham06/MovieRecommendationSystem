# Movie Recommendation System

There are two types of recommendation system -

1. Content based
   
   Content-based recommendation systems recommend items similar to those the user has liked or interacted with in the past. This similarity is determined based on the attributes or features of the items.

2. Collaborative filtering
   
   Collaborative filtering makes recommendations by identifying patterns in user behavior, typically by analyzing user-item interaction data. It doesn't rely on item attributes but rather on the preferences of other users.

We are designing a content based recommandation system using a big dataset

# Dataset Used 

MovieLens 100k Dataset

It contains many files which gives us vast information about data. 

This data set consists of:

* 100,000 ratings (1-5) from 943 users on 1682 movies.
* Each user has rated at least 20 movies.
* Simple demographic info for the users (age, gender, occupation, zip)

The data was collected during the seven-month period from September 19th, 1997 through April 22nd, 1998.

# Preparing Dataset

Used two files - 'u.data','u.item'

Used columns - 'user_id', 'item_id', 'rating' and 'movie_title' from both files and combined these columns to make a dataframe 'df'.

# Exploratory Data Analysis

Now, our dataframe df is ready.

To analyse the dataframe, we use parameters like popularity and ratings.

Grouped dataframe by number of ratings to know how many people have rated a single movie and grouped dataframe by mean ratings to know the most rated movie and plotted histogram for both.

![image](https://github.com/iamsaksham06/MovieRecommendationSystem/assets/97757688/53a6a13c-9b09-47f5-8d0a-6a53848f20e0)
![image](https://github.com/iamsaksham06/MovieRecommendationSystem/assets/97757688/4006116d-3bb2-458c-b304-42a11324b0aa)

Now, there is a catch, most rated movie might not be the most popular one, therefore, we need to know the movie that is rated well as well as by decent number of people.

To know this, we plotted a jointplot using seaborn library -

![image](https://github.com/iamsaksham06/MovieRecommendationSystem/assets/97757688/ff312194-9a49-45cc-9c35-ae3ce98e4d7d)

This plot shows movies which are highly rated as well as popular enough.

# Creating Movie Recommendation

Starting by creating a matrix of 943 rows representing each user and 1664 columns representing movie. This matrix shows the rating given by user to movies. If a user has not rated a particular movie, then that cell is marked 'NaN'.

Next step is to creating a dataframe which gives correlation of a movie given by user to the movie matrix created.

This dataframe contains movie titles as well as the correlation value with movie given by user.

Now, drop the null rows and join the dataframe with rating dataframe made when we were analysing the data to plot graphs. 

After joining the dataframe, we have a final dataframe of movie title as index, ratings and correlation as columns.

Finally returning top 10 rows by sorting it in descending order.

The result output is top 10 movies similar to the movie given by user from the dataset.

# Conclusion

Correlation based on the number of users gave how much rating to each movie as compared to the number of users gave what rating to the user input movie is calculated. 

Movies with highest positive correlation is given as the most similar movies.

Threshold of 150 ratings is set, movies having number of ratings less tha 150 are not included in output as they are not popular enough.
