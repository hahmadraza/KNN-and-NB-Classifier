# KNN-and-NB-Classifier
I produced my own version of the k-nearest neighbour (kNN) and naive Bayes (NB) classiﬁers to test against Pima Indians Diabetes Database [1].
# Data
The data set that I used is a modiﬁed version of the Pima Indians Diabetes Database. The modiﬁcation of the original was simply replacing missing values with the average calculated using the rest of the data set. The data was collected from females over the age of 21 years old with Pima Indian heritage [2]. The dataset includes the following attributes: 
1) Number of times pregnant
2) Plasma glucose concentration over 2 hours in an oral glucose tolerance test
3) Diastolic blood pressure (mm Hg) 
4) Triceps skin fold thickness 
5) 2-Hour serum insulin (mu U/ml) 
6) Body mass index (kg/m2) 
7) Diabetes pedigree function 
8) Age (years) 
9) Class (yes/no)
The data was normalised using the software Weka [3] to ensure that all attribute values are between zero and one.
# k-Nearest Neighbour
My kNN algorithm uses Euclidean distance to measure the distance between each data point. Although this is not always the best choice for a kNN algorithm, because the data is not only normalised, but also continuous, it was an appropriate choice in this case [5].

![](http://latex.codecogs.com/gif.latex?D%28A%2CB%29%3D%20%5Csqrt%7B%5Csum_%7Bi%3D1%7D%5E%7Bn%7D%28a_i-b_i%29%5E2%7D)

where	![](http://latex.codecogs.com/gif.latex?A%3D%28a_1%2Ca_2%2C...%2Ca_n%29)

and	![](http://latex.codecogs.com/gif.latex?B%3D%28b_1%2Cb_2%2C...%2Cb_n%29)

The algorithm uses above equation to ﬁnd the euclidean distance between the testing data point and each one of the training data points. It then selects the k nearest data points and takes the average of the class values to determine the class of the testing data point. If there is a tie, the algorithm chooses ‘yes’.
#  Naive Bayes
Naive Bayes (NB) algorithm is a statistical based classiﬁer that uses Bayes theorem (equation given below), to determine the probability of a given data point with attributes, A, being in class C [6].

![](http://latex.codecogs.com/gif.latex?P%28C%7CA%29%3D%5Cfrac%7BP%28A%7CC%29P%28C%29%7D%7BP%28A%29%7D)

For the purposes of this classiﬁer I assume a normal distribution for all attributes. P(A|C) can be broken down to P(a1|C)P(a2|C)...P(an|C) where A = (a1,a2,...,an) is the set of attributes for each data point.
## Training
The training phase of the algorithm calculates the mean and standard deviation for each attribute for each class. It also ﬁnds P(C) for each class, yes and no, by simply dividing the number of yes and no data points by the total.
## Testing
The testing phase of the algorithm uses a normal distribution using below equation where a is an attribute in a testing data point, µ is the mean of that attribute for a given class, and σ is the standard deviation of that attribute for a given class.

![](http://latex.codecogs.com/gif.latex?P%28a_i%7CC%29%3D%20%5Cfrac%7B1%7D%7B%5Csigma%20%5Csqrt%7B2%5CPi%7D%7De%5E-%5Cfrac%7B%28a_i-%5Cmu%29%5E2%7D%7B2%5Csigma%5E2%7D)

Because the algorithm is comparing the probability of the test data being in either yes or no class (i.e. P(ai|yes)/P(ai|no)), it is not necessary to calculate P(A). The class with the highest probability is chosen by the algorithm. If both classes have the same probability, then ’yes’ is chosen.
# APPENDIX A
## Algorithm
The ﬁle you will need to run my code for kNN and NB is MyClassifier.py
Run the algorithms using Python 3 by running MyClassiﬁer.py. The ﬁrst command line argument is the path to the training data, the second command line argument is the path to the testing data, and the third command line argumen is the algorithm you would like to run (eg. NB, 1NN, 3NN, etc.).
for example,

!python MyClassifier.py pima.csv testData.csv 3NN

## s-fold cross-validator
Run s-folds.py using Python 3 with the path to the testing data ﬁle as the ﬁrst command line argument, and the number of folds you would like to use as the second command line argument. The code will print the accuracy for each algorithm to standard output,and generate a ﬁle of the folds used.
for example,

!python MyClassifier.py testData.csv 10
