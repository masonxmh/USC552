# homework-1-masonxmh

<center><h1>DSCI-552 HOMEWORK 1</h1></center>
<center><font size="4">Classification Using KNN</font></center>
<center><font size="3"><strong>Mason(Mohan) Xing</font></center>
<center><font size="3"><strong>USCID:	6880083372</font></center>

# Homework 1

#### Background

This Biomedical data set was built by Dr. Henrique da Mota during a medical residence
period in Lyon, France. Each patient in the data set is represented in the data set
by six biomechanical attributes derived from the shape and orientation of the pelvis
and lumbar spine (in this order): pelvic incidence, pelvic tilt, lumbar lordosis angle,
sacral slope, pelvic radius and grade of spondylolisthesis. The following convention is
used for the class labels: DH (Disk Hernia), Spondylolisthesis (SL), Normal (NO) and
Abnormal (AB). In this exercise, we only focus on a binary classication task NO=0
and AB=1.1

This homework contains 6 parts:

#### (a) Download the Vertebral Column Data Set from: https://archive.ics.uci.edu/ml/datasets/Vertebral+Column.

#### (b) Pre-Processing and Exploratory data analysis:
##### i. Make scatterplots of the independent variables in the dataset. Use color to
show Classes 0 and 1.
ii. Make boxplots for each of the independent variables. Use color to show
Classes 0 and 1 (see ISLR p. 129).
##### iii. Select the firrst 70 rows of Class 0 and the first 140 rows of Class 1 as the
training set and the rest of the data as the test set.

#### (c) Classification using KNN on Vertebral Column Data Set
##### i. Write code for k-nearest neighbor with Euclidean metric

``` python
def knnclf(knn, k, X_train, X_test, y_train, y_test):
    temp_dict = {}
    knn.set_params(n_neighbors=k)
    knn.fit(X_train, y_train)
    y_train_pred = knn.predict(X_train)
    y_test_pred = knn.predict(X_test)
    # calculate MSE
    train_error = mean_squared_error(y_train, y_train_pred, squared=True)
    test_error = mean_squared_error(y_test, y_test_pred, squared=True)
    # calculate error rate
    train_accuracy = accuracy_score(y_train, y_train_pred)
    test_accuracy = accuracy_score(y_test, y_test_pred)
    train_error_rate = 1-train_accuracy
    test_error_rate = 1-test_accuracy
    #construct output dict
    temp_dict['k'] = k
    temp_dict['train_error'] = train_error
    temp_dict['test_error'] = test_error
    temp_dict['train_error_rate'] = train_error_rate
    temp_dict['test_error_rate'] = test_error_rate
    
    return temp_dict 
```

#### ii. Test all the data in the test database with k nearest neighbors. Take decisions by majority polling. Plot train and test errors in terms of k for k âˆˆ { 208, 205, . . . ,7,4,1,} (in reverse order) 

K* : 4

Minimum test error rate: 0.06

Minimum train error rate: 0.0

True Positive Rate is : 0.9857142857142858

True Negtive Rate is : 0.8333333333333334

Precision is : 0.9324324324324325

f1 score is : 0.9583333333333333

##### iii Since the computation time depends on the size of the training set, one may only use a subset of the training set. Plot the best test error rate, which is obtained by some value of k, against the size of training set, when the size of training set is N âˆˆ {10, 20, 30, ...., 210} 

| N | K * | Minimum Test Error Rate  |
| --| --- | --- |
|10|[1]|0.25|
|20|[6]|0.2|
|30|[1]|0.22|
|40|[11]| 0.25|
|50|[26]|0.3|
|60|[21]|0.29|
|70|[26]|0.29|
|80|[31]|0.29|
|90|[41]|0.29|
|100|[6]|0.25|
|110|[6]|0.22|
|120|[16]|0.17|
|130|[16]|0.16|
|140|[16]|0.15|
|150|[16]|0.13|
|160|[6]|0.13|
|170|[6]|0.13|
|180|[6]|0.1|
|190|[6]|0.09|
|200|[6]|0.09|
|210|[6]|0.08|

#### (d)Replace the Euclidean metric with Manhattan Distance, log10(p), Chebyshev, Mahalanobis Distance. 

Summary of the Best Test Error Rate


| |Distance|	k * 	|min_test_error_rate|
| -| --| --- | --- |
|0|	Manhattan	|[6]|	0.11|
|1|	log10P=[0.6]|	[6]	|0.06|
|2|	Chebyshev|        [16]	|0.08|
|3|	Mahalanobis| [1] | 0.17 |

#### (e)  The majority polling decision replaced by weighted decision

| |Distance|	k * 	|min_test_error_rate|
| -| --| --- | --- |
|0|	Euclidean		|[6]|	0.10|
|1|	Manhattan|	[26]	|0.10|
|2|	Chebyshev|        [16]	|0.11|

#### (f) The lowest training error rate in this homework

| |Problem|	min_train_error_rate|
| -| --| --- |
|0	|cii	|0.000000|
|1	|ciii	  |0.000000|
|2	|diA	|0.000000|
|3	|diB	|0.133333|
|4	|diC	|0.000000|
|5	|dii	|0.000000|
|6	|e_Euclidean	|0.000000|
|7	|e_Manhattan	|0.000000|
|8	|e_Chebyshev	|0.000000|