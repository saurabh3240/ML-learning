source of Reading https://hackernoon.com/how-to-build-a-simple-spam-detecting-machine-learning-classifier-4471fe6b816e

# SPAM DETECTION

## Naive Bayes classifier

* Need labelled data
* avoid overfitting
* need a good mix of both spam and ham mails

### Bayes' theorem

![bayes](images\bayes.png)
A probability that email is SPAM and
B as content of probability

P(A|B) > P(~A|B) then spam otherwise ham

remove denominator both side

P(A)\* P(B|A) > P(~A) \* P(B|~A)

p(A) and p(~A) is trivial class split

### Bag of words model
