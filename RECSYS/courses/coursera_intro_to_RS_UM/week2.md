## Non-personalized and Stereotyped Recommendation 

### Why Non-Personalized? 

- New users – we know little about them (cold start) 
- Simple but beneficial 
  - how many people bought this item
- Online communities around common displays (e.g. Reddit, Slashdot) 
  - everyone sees same set of stories
- Applications & media where personalization is impossible 
- It can be remarkably effective 

### Weak Personalized

Sometimes we know a little about a user 

- Zip code or location 
- Age, gender, nationality, ethnicity

This can be used for first-pass ‘stereotyped’ personalization 

Product associations allow recommendations based on current page/item/context

 

**stereotype-based-recommendation**

Recommenders that base their recommendations on groupings of people defined by attributes not directly related to consumption, such as age, gender, income, or geography. These recommenders aggregate implicit or explicit ratings according to these groups.  



## Summary statistics

### Computing The Scores 

- What should they mean?  (are these good measures)
  - Popularity 
    - Mc D is more popular
  - Average Rating 
    - for many people eating at home
  - Probability of You Liking 
- How to compute? 
  - Frequency 
  - Average 
  - More Complicated 

### Breaking it Down 

- Popularity is an Important Metric 
- Averages Can be Misleading 
  - Can adjust by summing % who like  
  - Can adjust by **normalizing** user ratings 
    - normalization addresses different rating scales
    - different people have different liking scale. 
  - May want to consider **credibility of individual raters** (history of ratings)
    - create an fake account for spreading hate or spam or promoting 
- More data is better … to a point 
  - Average, Count, Distribution 



### What’s missing here? 

- Who you are (Demographics) : 

  - If I’m looking for popular new songs, I might not be looking for songs popular among 15-year-old girls 

- Your **context**: 

  - If I’m ordering an ice-cream sundae and want a recommendation for a sauce, do I want to hear that ketchup is the most popular sauce ?

  - most popular sauce for ice cream.

      

### Some take-away lessons 

- Non-personalized popularity statistics or averages can be effective in the right application 
  - Need to understand relationship between average and user need; correct average 
- In many cases it can be best to show count, average, and distribution together 
- For ranking, one alternative to average is the percentage who score above a threshold – Or below!
- Personalization would address many limitations! 

## Summary Statistics II

### Reddit (Example)

- social new aggregation
- Non-personalized  recommender
- users vote on item to determine top item
- fresh source of news
- voting for comments as well

### Simple Display Approaches

- Average rating/upvote proportion
  - opinion of people who vote, do they like it ?
  - Doesn't show popularity
- Net upvotes/ # of like
  - shows popularity
  - No controversy
- % >= 4 stars('positive')
  - saving 5 that are extraordinary
  - every one has there scale of rating.
- Full distribution will histogram(Amazon)
  - complicated

### Why not rank by Score?

- Too little data. (one 5 star rated item  or item with many purchase but less stars say average 4.5)
- score may be multivariate(histogram)
- Domain or business considerations
  - item is old
  - item is unfavored

### Ranking Considerations

- confidence
  - how confident are we that this item is good? (lot of rating gives confidence)
- Risk tolerance 
  - High-risk, high-reward  
  - Conservative recommendation (recommend something that you are confident)
- Domain and business considerations 
  - Age 
  - System goals 

### Damped Mean

- Problem: low confidence w/ few ratings 

- Solution: assume that, without evidence, everything is average 

- Ratings are evidence of non-averageness 

- k controls strength of evidence require

- $\frac{\sum_u r_{ui}+k\mu}{n+k}$

- with less # ratings  k parameter makes the confidence close to mean

- with large rating k affect dampens out.

   

### Confidence Intervals 

- From the reading: lower bound of statistical confidence interval (95%) 
  - this interval narrows as we get more and more ratings
- Choice of bound affects risk/confidence 
  - Lower bound is conservative: be sure it's good 
  - Upper bound is risky: there's a chance of amazing 
- Reddit uses Wilson interval (for binomial) to rank comments 

### Domain Consideration: Time

-  Reddit: old stories aren't interesting 
  - even if they have many upvotes ! 
- eBay: items have short lifetimes 

### Scoring News stories

- Hacker News 
  -  $\frac{(U-D-1)^\alpha}{(t_{now}-t_{post}-1)^\gamma}. P$
  - U-D-1 net upvotes
  - alpha nearly = 0.8 and gamma 1.8 ,
    -  a post get older confidence get diminishes
  -  Net upvotes, polynomial decayed by age 
  - Old items scored mostly by vote 
  - Multiplied by item penalty terms  P
  - incorporate community goals into score 
- REDDIT
  - $log max(1,|U-D|) + \frac{sign(U-D) t_{post}}{45000}$
  - log strong dampening factor on latest vote
  - second term is time decaying term.
  - Log term applied to votes 
  - decrease marginal value of later votes 
  - Time is seconds since Reddit epoch 
  - Buries items with negative votes 
  - Time vs. vote impact independent of age 
  - scores news items, not comments 

### Ranking Wrap-Up 

- There are some theoretically grounded approaches (confidence interval, damping)
-  Many sites use ad-hoc methods 
- Most formulas have constants, will be highly service-dependent 
- Can manipulate for ‘good’ or ‘evil’
- Build based on domain properties, goals 



### Predict with sophisticated score? 

- Theoretically a fine thing to do 
- Be careful with transparency/scrutability 
  - If you say ‘average rating’ for damped mean, and show ratings, users may be confused 
  - Most important case (low ratings) also easiest to hand-verify 



### Conclusion

- Sparsity, inconsistency, temporal concerns make data messy 
- Simple scoring doesn't necessarily match the domain or business 
-  There are good ways to deal with this (decay, time, penalties, damping) 
- We'll see more normalizations later