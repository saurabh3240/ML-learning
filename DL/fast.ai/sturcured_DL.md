# Structured Deep Learning

source : https://towardsdatascience.com/structured-deep-learning-b8ca4138b848

- Structured data : 
  - row: collection of individual data points or observation
  - column: fields that represent a single attribute of each observation.
- Unstructured vs Structured:
  - In unstructured we often deal with single entities/units like pixels, voxels, audio frequencies, radar
  - in structured we deal with two type of data
    - numerical
    - categorical
      - It requires preprocessing
  - category data should be encoded carefully
    - days of week when encoded by one hot encoding will take away some information
    - as it assumes difference b/w each pair of days are equal 

**“The continuous nature of neural networks limits their applicability to categorical variables. Therefore, naively applying neural networks on structured data with integer representation for category variables does not work well” **

- Tree algorithms do not require any assumption on continuity of categorical variable .
- here entity embedding can be useful .

## Entity Embedding

(to be filled )