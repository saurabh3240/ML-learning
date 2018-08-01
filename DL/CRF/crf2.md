# Conditional Random Fields

source : http://blog.echen.me/2012/01/03/introduction-to-conditional-random-fields/
## Application
- consider sequence of inputs as a feature in classification of inputs
- sequence of character images we want to predict words
- PART OF SPEECH TAGGING

## Feature Function in CRF
- a sentence s
- the position i of word in sentence
- the label $ l_{i} $ for the current word
- the label $ l_{i-1} $for the  previous word

## Maths
- let $ f_j $ has weight $\lambda_j $
- score is weighted features overs all words in the sentence
$ score(l | s) = \sum_{j = 1}^m \sum_{i = 1}^n \lambda_j f_j(s, i, l_i, l_{i-1}) $
- first sum over each feature function j and 
- inner sum over each position i 
- transform score into probability by softmax or exponential nomralizing
- $ p(l | s) = \frac{exp[score(l|s)]}{\sum_{l’} exp[score(l’|s)]} = \frac{exp[\sum_{j = 1}^m \sum_{i = 1}^n \lambda_j f_j(s, i, l_i, l_{i-1})]}{\sum_{l’} exp[\sum_{j = 1}^m \sum_{i = 1}^n \lambda_j f_j(s, i, l’_i, l’_{i-1})]}$

## Example features
- if the words ends in -ly ADVERB
- if i=1 and $l_i $ = VERB ,the sentence ends in quesion mark
- if $l_{i-1}$ and $ l_i$ is NOUN
- if $l_{i-1}$ and $l_i$ both PREPOSITION a negative $\lambda$ for that
- etc.
- some feature depende on the entire sentenc, current position and nearby labels assign them weights and add together.


**CRFs are basically similar to sequential  version of logistic regression:
LR is log-linear model where as CRF are log-linear model for sequential labels.**

## Similarity to HMM
- HMM takes a generative approach in labelling POS
- defined as
	- $p(l|s) = p(l_i)\Pi_i p(l_i|l_{i-1}) * p(w_i|l_i)$ 
	- $ p(l_i|l_{i-1})$ are transitional probabilities.
	- $ p(w_i|l_i) $ are emission probabilities

** How CRF are more powerful than HMM **
- log of HMM probabilities
- $ \log p(l,s) = \log p(l_0) + \sum_i \log p(l_i | l_{i-1}) + \sum_i \log p(w_i | l_i) $
-  this is same as log linear form of a CRF if we consider log-proab
- **transition probabilities ** of HMM can be modeled as:
- 	$f_{x,y}(s, i, l_i, l_{i-1}) = 1$ 
	-	if $l_i=y $and $l_{i−1}=x$.
	- 	and weight will be $w_{x,y} = \log p(l_i = y | l_{i-1} = x)$
- ** emission probabilities ** can be modelled as:
- $g_{x,y}(s, i, l_i, l_{i-1}) = 1$
	- if $ w_i = z$ and $l_i = x$ 
	- and weight $w_{x,z} = \log p(w_i = z | l_i = x)$ 
- thus CRF by these features are proportional to HMM 
- CRF can model much richer set of label distribution(REASONS)
 	- ** CRF can define a large set of features **
 	 - can capture global feature such as starting word likely to be VERB if sentence ends with a question mark.
 	- ** CRF can have arbitary weights ** 
 		- HMM have weight b.w 0 and 1 
 		- $0 <= p(w_i | l_i) <= 1, \sum_w p(w_i = w | l_1) = 1)$
 		- CRF weighs are unrestricted $ log p(w_i|l_i) $ can be anything 
 		
## Learning Weights
- one way can be gradient Descent
	- Assume having bunch of examples
	- Randomly initialize weight of CRF model
	- shift the weight to correct ones for each training examples.
	- for each feature function $f_i$
		- calculate its gradient of log probability of training example with respect to $\lambda_i$.
		- $\frac{\partial}{\partial w_j} \log p(l | s) = \sum_{j = 1}^m f_i(s, j, l_j, l_{j-1}) - \sum_{l’} p(l’ | s) \sum_{j = 1}^m f_i(s, j, l’_j, l’_{j-1})$
			- first term is contribution of feature $f_i$ under true label
			- second term is contirbution of feature $f_i$ under the current model.
		- move $\lambda_i$  in the direction of gradient:
		- $\lambda_i = \lambda_i + \alpha [\sum_{j = 1}^m f_i(s, j, l_j, l_{j-1}) - \sum_{l’} p(l’ | s) \sum_{j = 1}^m f_i(s, j, l’_j, l’_{j-1})]$
		- $\alpha$ is learning rate.
		- repeat until convergence.

## Find Optimal Labelling
- calculate $p(l|s) $ for every possible labeling l and choose l that maximizes proabability .
- exponential check for k labels and m sentence length $k^m$ possible label sequence.
- similar to Viterbi for HMM there exist a polynomial time DP algo on CRF label calculations.
