# Results Summary
## Answers to the three questions posed:
1. **How can we predict the popularity of a track and what are the most important predictors?**
2. **Do different genres see varying levels of popularity, and does this change over time?**
3. **By what characteristics can we group/cluster tracks? What subcategories of tracks exist?**

## 1. How can we predict the popularity of a track and what are the most important predictors?

I started to answer this question by using linear regression with regularization. I sought to find the best regularization technique for this data, which was Ridge.
Here are the r-squared and mean-squared error values:

![image](https://user-images.githubusercontent.com/75226784/135770833-d2f758cf-4c78-4ba5-9b74-7640c561eed7.png)


Ridge slightly outperforms LASSO wth a lower MSE and higher r-squared value. 

The following bar plots contain the coefficients for the Ridge regression.

![image](https://user-images.githubusercontent.com/75226784/135770619-1019f5e0-4fe0-4c16-89df-966b31ca85e5.png)

![image](https://user-images.githubusercontent.com/75226784/135770628-a68371bd-23b8-4a53-9152-bd567994626c.png)

![image](https://user-images.githubusercontent.com/75226784/135770646-55ec772c-9b23-4f22-b7d7-82f7b2c21a05.png)

![image](https://user-images.githubusercontent.com/75226784/135770663-f42115a9-fc32-498f-8c6a-369516da5929.png)

![image](https://user-images.githubusercontent.com/75226784/135770671-a12eb9a6-1980-4b59-a0b9-1818fb468bcc.png)

I am including the LASSO coefficients not reduced to zero to reinforce the 'important' coefficients are the same as the coefficients with high magnitudes in the Ridge regression.

![image](https://user-images.githubusercontent.com/75226784/135770512-5a405920-d62f-4f61-96ae-8173bafcf5f5.png)

This bar graph shows the coefficients that LASSO did not shrink to 0. Here we see that release_year and artist_popularity are the largest coefficients, implying that they have the largest impact on a track's popularity.


### Analysis: How can we predict the popularity of a track and what are the most important predictors?

For this question, I performed Linear Regression with two different types of regularization: LASSO and Ridge. I used both because they handle coefficients differently. An ideal predictive model performs well on training data and testing data, or data it has already seen and new data. Regularization helps minimize the impact of variables on the model when the variables may be less significant in the overall population of the data. Minimizing this impact lowers the risk of overfitting, or biasing the model to the point where it performs poorly on new data. LASSO regularization shrinks less important variables to have a coefficient of zero, so that they will not impact the model. Ridge regularization penalizes the coefficients but does not eliminate them, so there are coefficients that just have a lesser impact on the model. 

The results of this model can be explained through the r-squared scores shown. The LASSO model's training r-squared was 0.4785, and decreased to 0.4780 with the test data. The Ridge model had a higher training r-squared of 0.5079, which increased with the testing set to 0.5082. Both models' r-squared values imply that the variables used for the linear model explain around 50% of the variation in song popularity. The increase in r-squared in the Ridge model implies that the model is actually underfit, or doesn't understand the patterns in the existing data and handles new data because it's just guessing. This is backed up by the fact that both test mean squared errors decreased from the training to the test set in both LASSO and Ridge regressions. This underfitting implies that a simple linear model cannot well predict track popularity.

It is worth noting that the most important variables for the regression, those with the largest magnitudes, are the artist's popularity and the song's release date. Spotify is a relatively new streaming service started within the last 15 years. As its consumer base has grown, it makes sense that music produced and listened to today would be more popular than music from a long time ago. The artist's popularity also is significant because they're usually well-known, which means they likely have the money to advertise their song and make it popular because they are popular. Interestingly, liveness and acousticness have negative impacts on whether the song will be popular. The negative liveness impact may be due to the "live" version of songs not being normally listened to. Acousticness encompasses a lot of instrumental or classical music, which is not as popular as a lot of vocal-based music. Lastly, the overall average loudness of the track has a positive impact; apparently, the louder a song is across its runtime, the better people like it. 



## 2. Do different genres see varying levels of popularity, and does this change over time?

Let's start by looking at the amount of tracks released per year from 1922 to May 2021.

![image](https://user-images.githubusercontent.com/75226784/135770929-3b7c675d-a11a-413c-9c60-4273a4aebe32.png)

Here we see that the largest amount of tracks on Spotify were released after 1975. To break the catalog down by genre, here are the top 10 genres over all time recorded.
This visualization excludes the 'Other' category to make the trends for the top 10 genres more clear.

![image](https://user-images.githubusercontent.com/75226784/135771050-70dba1ed-7599-4e1e-a3ac-cccfd3dd5069.png)


These next bar plots show the 10 most popular genres per decade broken down by year.

![image](https://user-images.githubusercontent.com/75226784/135770986-6ca5e1a9-e6fc-41ae-9238-c148b91eff91.png)

![image](https://user-images.githubusercontent.com/75226784/135770993-d88d917c-8923-47a5-89c8-c5181ae76553.png)

![image](https://user-images.githubusercontent.com/75226784/135770995-0781bb17-8803-4768-bb14-95951b9a5810.png)

![image](https://user-images.githubusercontent.com/75226784/135770999-7741d10b-4464-42a8-85d1-3b665e6318fc.png)

![image](https://user-images.githubusercontent.com/75226784/135771001-160d8af6-0ba3-4f75-801b-fdd5269db39c.png)

![image](https://user-images.githubusercontent.com/75226784/135771005-d0217600-b52a-42ce-a098-f660b1d3a690.png)

![image](https://user-images.githubusercontent.com/75226784/135771006-d2184ef2-d273-4ee3-b842-6c08dcf4835a.png)

![image](https://user-images.githubusercontent.com/75226784/135771008-8004c23e-325b-4a39-ada8-d5cd995fc53a.png)

![image](https://user-images.githubusercontent.com/75226784/135771013-3a5cdbce-d6c5-4bbb-89de-721e29c33f8f.png)

![image](https://user-images.githubusercontent.com/75226784/135771016-2b1b49e9-acca-47f3-92ac-9bfe2fe90acb.png)

### Analysis: Do different genres see varying levels of popularity, and does this change over time?

In a word, yes! These graphs show the top 10 genres for all the songs over each decade, starting in 1922. While the listening data or Billboard 100 information is not available, especially for songs that predate that type of opinion collection, the existence of recordings implies a trend for producing and selling that music that must have been driven by some sort of customer demand. The top 10 genres with the most recordings on Spotify changes from decade to decade, implying changing tastes and the diffusion of Western recording techniques. Taking a look at the top 10 genres of all Spotify-recorded-time, we see that each one has its own heyday. Latin music increased in recording frequency from 1975 onwards, while dance pop seriously grew starting in the 2000's. Album rock was prominent in the 1970's-1990's, and remains relevant today. 
Another important consideration is the ever-growing "other" category in the decade graphs. This shows that the variety of genres has been growing throughout the 1922-2021 period, which also means that Spotify has a large collection of different music. This increase in genre diversity implies advancement in music and in whose voices are heard by recording companies.



## 3. By what characteristics can we group/cluster tracks? What subcategories of tracks exist?

I attempted to cluster tracks using Hierarchical Agglomerative Clustering since it easily shows relationships between clusters, which would allow us to see subcategories or larger relationships between different tracks. I originally planned to use a dendrogram to see this relationships, but the clustering did not turn out as expected.

![image](https://user-images.githubusercontent.com/75226784/135771608-39768dfa-abc5-4f52-bf89-07983e2deb97.png)

The model returned a high silhouette score of 0.877. However, 43,199 tracks belong to Cluster 0 while only 1 track belongs to Cluster 1. Looking further into this split, we can see the average track popularity in Cluster 0 is around 30/100, whereas the one track in Cluster 1 is not popular at all.

![image](https://user-images.githubusercontent.com/75226784/135771673-b671dff2-8624-4724-8443-52d5004b9b1a.png)

I have used a bar chart to display visually how unbalanced the cluster membership is, instead of seeing the clusters through a dendrogram. I am using a box-and-whisker plot to see the distribution of track popularity across this sampled data.

This Hierarchichal Agglomerative Clustering algorithm did not allow us to cluster and discover subgenres of tracks in a meaningful way. It grouped the randomly sampled data into 2 clusters or groups and returned a high silhouette score, which means that the clusters are separable and cohesive. Separation and cohesion means that group members are close to each other and far away from the other cluster. These results were initially promising. However, all points except 1 (43,199) belong to the first cluster, Cluster 0, and the other point makes up its own cluster. This implies that the relationships between individual points and genres and subgenres is not able to be viewed through this type of clustering.

To attempt this clustering, I would test out other algorithms like K-Means, Gaussian Mixture Models, and DBSCAN.
