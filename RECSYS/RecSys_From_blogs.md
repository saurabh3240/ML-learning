# Recommendation System(RecSys)

Links: http://blog.manugarri.com/a-short-introduction-to-recommendation-systems/(COMPLETED)

- the purpose of a RecSys is to predict a rating that a user will give to a item that they have not rated.
- rating predicted by analyzing either item characteristics or item user/item rating to provide personalized recommendation.

## Approaches
- Content Filtering
	- recommendation Depends on item characteristics.
- Collaborative Filtering.
	- Recommendation Depend on user-item rating.

### Content Based Filtering
- users have to express theire prefenece once.
-  need to map each item into feature sapce.
	- manually categories new item.
- recommendation are limited in scope. (new feat 
	- item can't be categorized in new features.

### Collaborative Filtering
- uses existing user-item score to predict the missing ones.
- **assumption**:  users get value from recommendations based on other users with similar tastes.
- To compute similarities b/w movies find correlation and then use it to find similar movies to those users have liked.
- capable of recommending new items without manually define them
- able to find hidden feature that an expert wouldn't able to find like genres or actors.
- **Drawback**: can not recommend items for new user until he/she has not reviewed any item **cold start problem**.
-  Can be avoided by using hybrid content based + collaborative filtering.

#### Pearson Product Moment Correlation Coefficient(PMCC)
- has value b/w -1 and 1.
- use python numpy.corrcoef
- corelation matrix is m X m  
   - where $M_{ij}$ represents correlation b/w ith and jth item.
# Deep Learning for RecSys

LINK: https://ebaytech.berlin/deep-learning-for-recommender-systems-48c786a20e1a

example: find right car quickly is a challenging task high gain- high risk Recommendation problem.

 ***Information Overload***  which describes the large amount of information invading our minds and demanding fast and accurate processing 

“It’s not Information Overload, it’s Filter Failure". -Clay Shirky

## Deep learning for Vehicle Recommendation

Basic goals

1. Increase the relevance of recommendations.
2. Provide them in scalable way

- the network output probability  and use it for ranking
- label positive interaction with 1 and others as 0'
- learning task as a binary classification process.
- augment DL approach by Nearest -neighbor search to scale well

## Tasks to solve

1. **Embedding**
   - ![img](https://cdn-images-1.medium.com/max/1600/1*0EGLHojSWp-xoUMNjHSQxA.png)
   - reduce dimensionality by compressing the info.
2. **Candidate Generation**
   - use user embedding as query
   - fetch T closest item for specified distance metric 
     - Euclidean distance.
   - Many implementation available
     - Locally Optimized Product Quantization ([LOPQ](https://github.com/yahoo/lopq)) from Yahoo or 
     - Approximate Nearest Neighbor Oh Yeah ([ANNOY](https://github.com/spotify/annoy)) provided by Erik Bernhardsson from Spotify.
3. **Raking **
   - RankNet to score each candidate.
   - Sort candidate by decreasing score, take top K .
   - 





https://www.kaggle.com/gspmoreira/recommender-systems-in-python-101/code

https://www.kaggle.com/rounakbanik/movie-recommender-systems/code

https://medium.com/@ACMRecSys/recsys2017-summaries-and-reviews-f2bea3f0e519

