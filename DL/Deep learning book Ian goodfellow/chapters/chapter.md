# INTRODUCTION

**Shorhands**

```
* DL -> Deep Learning
* AI -> Artificial Intelligence
* ML -> Machine Learning
* stmts -> statements.
* algo(s) -> algorithm(s)
* LR -> Logistic Regression
* feat(s) ->  feature(s)
* + -> positive point
* - -> negative point
???? incomplete(FILL It later)
```

- AI is thriving with many practical applications and active research topics.
- some examples are:
  - intelligent software to automate routine labor
  - understand speech or images
  - make diagnoses in medicine
  - support basic scientific research
- in early days AI tackled problem that were difficult for humans but easy for computers.
  - problem which can be describe with formal mathematical rules.

- **TRUE CHALLENGE**

  - solve tasks easy for human but hard for people to describe it formally
    - recognition of images, speech etc.
  - much of knowledge is subjective and intuitive & difficult to express formally.

- **SOLUTION**

  - allow computer to gather knowledge from experience
  - understand world in terms of hierarchy of concepts
    - relation to simpler concepts
  - avoid human to specify knowledge.
  - concepts are built on the top of each other in graphical layer-wise manner hence the terms **AI Deep Learning.**

- **Early Success**

  - where no require of much knowledge of environment.
    - IBM's Deep Blue, chess very simple world
    - large search space for moves to select.
    - chess can be described by very brief list of completely formal rules.

- **Approaches**

  - **Knowelge Based (KB)** using logical inference rules to reason about stmts. in formal languages.
    - project _Cyc (Lenat and Guha, 1989)_.
    - several flaws with this approach.

- **Machine Learning(ML)**:

  - Definition: AI ability to acquire their own knowledge from patterns in raw data.
  - + allowed to tackle problem involving real world knowledge
  - + make decision that appear subjective.
  - e.g.
    - Logistic Regression Classifiers to recommend cesarean delivery. _(Mor-Yosef et al., 1990)_
    - Naive Bayes to detect spams in emails
  - ML algos performance heavily depends on Data Representation.
    - features - piece of information.
  - LR correlates features with outcomes.
    - - doesn't influence the way in which feats defined.
    - - it can't make useful prediction by MRI scans instead of Dr. detailed report.
      - no correlation of individual pixel of MRI scan

- **Representation Importance [ from lecture]**

  - choice of feats Representation is very Importance in daily life.
  - and on the ML algo performance.
  - for e.g. useful feats in Speech Recognition will be
    - speakers vocal tract (strong clues for a child, male, female)

![](images\fig1.1.png)

- **Deep learning as technique for how to represent data in machine learning system**
- taking a line and telling one side of line belongs to one category
other side to other category.
- No actual line in Cartesian coordinates
- if we choose polar coordinates then we can fit a line and separate.
- can use same technique by Deep learning in
    - machine Translation
    - object Recognition
    - robotic control

![](images\fig1.2.png)
- **Repeated Composition [ from lecture]**
    - creates a form a representation where  one representation formed out of another.
    - gradual transformation to get more abstract feats and meaningful.
    - This Example
        - collection of pixel values
        - individually these pixel are meaning less.
        - change representation several times each new representation referring the representation before.
        -  next layer ( 2nd last ) detect edges. group of dark pixels next to light pixels.
        - extract different features from the images.
        - next layer ( 3rd last) trying to find corners and extended contours.
            - two different edges to form a corner.
            - or several edges to form a contour or curve.
        - continue to apply we can get wheels of car or heads of people.
        - with each step we get something simple but powerful.

- **Computational Graphs [From lectures]**

 describe these structures as computation graphs.

![](images\fig1.3.png)

  * depth of architecture is length of path from input to output in computational graph .
  * most earlier ML algos have are very shallow.
  *  In figure explain a simple Logistic Regression algos representation
    *  X is product of weights and inputs
    * +  is sum of all the product below
    * sigma is tradition sigmoid function
    * depth of 3
    * in DL the graph has depth 1 only

#### **Machine Learning in AI**  

![](images\fig1.4.png)

 * DL is an approach to AI.
 * AI broad Definition here ????
 * there are AIs without learning
   * knowledge for AI system designed by humans
   * CYCs project
 * understand data in terms of features
   * e.g. logistic Regression
 * Feats learning from raw inputs such pixels
    * e.g. AutoEncoders(AE) memorize the input and redraw the input. idea is to capture important characteristic of inputs
 * DL algos are representation learning algos   that apply sequential transformation on the data to give a sophisticated data representation.

#### Learning Multiple Component

![](images\fig1.5.png)
