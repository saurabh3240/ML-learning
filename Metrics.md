# Metrics and ERRORS

![errors](/images/PR.png)

### confusion matrix

| Test\Actual | True                              | False                            |
| ----------- | --------------------------------- | -------------------------------- |
| True        | True Positive (TP)                | false positive (FP) **(type I)** |
| False       | False Negative (FN) **(Type II)** | true negative (TN)               |

**TP** : predicted  True actually was True

**FP:** predicted True actually was False

**TN:** predicted False actually was False

**FN:** predicted False actually was True

![img](https://cdn-images-1.medium.com/max/800/1*2lptVD05HarbzGKiZ44l5A.png)

**Type I error **

- predictive positive but actually false (FP). 
- incorrect rejection of true null hypothesis ( do no be confused)
- p value test (to be read)
  - value is very small $\mu \pm 2*\sigma$ or within 95 % range 
- t-statistics (to be read)

**Type II error **

- predictive negative but actually True (FN).
- incorrectly retaining a false null hypothesis

![](https://chemicalstatistician.files.wordpress.com/2014/05/pregnant.jpg?w=500&h=374)



## Accuracy

- $\frac{TP+TN}{TP+FP+TN+FN}$
- tell us how many of the total cases we correctly predicted the label.

## Precision |Positive prediction value(PPV)

- $precision = \frac{TP}{TP+FP} \ =   \frac{TP}{P} = 1 -FNR $
- Significance:
  - **IR (information retrieval) **: how many selected items were relevant?
  - **classification:**  What proportion of positive identifications was actually correct?



## Recall | True Positive Rate(TPR) | Sensitivity | hit rate

- $recall = \frac{TP}{TP+FN}$
- Significance:
  - **IR (information retrieval)**: how many relevant items were selected?
  - **classification:**  What proportion of actual positives was identified correctly?

## F-measure

## 

## OTHER  METRICS

#### True Negative rate (TNR) | Specificity | selectivity 

- $TNR = \frac{TN}{TN+FP} = \frac{TN}{N}  = 1 -FPR$

## Miss rate | false negative rate(FNR)





## ROC(Receiver Operating Characteristics)

- performance measurement of classifier at different different thresholds settings.
- Its a probability curve
- **Definition:** curve plotter with TPR(True positive rate) against the FPR ( False positive rate) 

##AUC (Area under the curve)

- Area under the ROC
- Represents **degree or measure of separability.**
- higher the AUC, better the model 

### What is AUC ?

- 

 

- used for binary classification
- can be used for dataset with high imbalance classes
- can be applied to multi classification problem when **one vs all** approach is used.
-   

##