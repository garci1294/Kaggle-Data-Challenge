Human Gene Function Prediction Challenge

# Goal
To identify a supervised learning approach that utilizes gene dependency data from genome-wide CRISPR-Cas9 screens to predict human gene function. This is a multi-class classification problem.

# Dataset: Provided in Kaggle
- Human genetic Interaction Profiles (genes X cell lines)
- GO Term Annotation matrix (Gene X GO annotations)

# Approach:
To select the best classifier to predict human gene function, we explore multiple data preprocessing steps and various classifiers on the given dataset. Below are some that were attempted.

# Data Pre-processing Attempted:

(1) Data Standardization: For the training and test data, remove the mean and scale it to unit variances.
(2) Correlation-based feature selection: Feature selection methods often enhance the ML performance. Hence, a correlation-based feature selection method was attempted with multiple learning algorithms to check for performance improvements. Firstly, the correlation between all features in the data set was calculated and from a highly correlated pair (i.e greater than 0.9 correlation score.), one of the features was eliminated.

# Learning Algorithms to attempt: 
(1) Random Forest (RF) with two different number of tree values
- Number of trees of 50
- Number of trees of 100

(2) Support Vector Machines (SVMs)
- Kernel with a polynomial degree of 4

(3) K-Nearest-Neighbor (KNN) with 3 different K’s
- K = sqrt(sample size)
- K = sqrt(sqrt(sample size))/2
- Individual label classification by balancing datasets

# Evaluation Metrics to Choose the Final Algorithm:
- Apply k-fold cross-validation: For each of the classifiers chosen, the five-fold cross-validation
scores were calculated
- Kaggle score for the Test data: The prediction probability calculated for the test data, when
submitted in Kaggle, gives us a score that is the “Mean Columnwise Area Under Receiving
Operating Characteristics Curve”.

# Result (Selected Approach)
K-NN (K = sqrt(sample size)) and Random Forest (trees = 100) obtained the best score among all classifiers, so, we used a stacked approach for this. The following is our selected Classification Approach:

(1) Data standardization

(2) Predict the test data probability using K-NN where K is selected as the square root of the total number of training samples.

(3) Predict the test data probability using RF where the total number of decision trees is 100

(4) Average of the prediction probabilities for KNN and RF was taken as the final prediction.

# Future Work Related
The future work part focuses on individual label vs all label classfications. Moreover, identifying that data is unbalanced for the individual label and the possibility of balancing the data by adding more data to the unbalanced side.
