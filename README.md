# AI Final Project

[Breast Cancer DataSet](https://www.kaggle.com/uciml/breast-cancer-wisconsin-data#data.csv)

## Abstract
In this project, I am using a dataset from Kaggle (link provided above). Data set provides with informative feautures that are computed from a digitized image of a fine needle aspirate (FNA) of a breast mass. They describe characteristics of the cell nuclei present in the image. 
With the 30 features provided from the dataset I am splliting the first 400 rows for the training dataset and the remaining rows are used to test our model. The goal of the project is to create as an accurate model as we can that will predict if the diagnosed client will have a Benign or Malignant (cancerous) tumor. 


![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Breast%20Cancer.PNG)

## Metadata

Attribute Information:
`````````````
1) ID number 
2) Diagnosis (1 = malignant , 0 = benign)
3-32)

Ten real-valued features are computed for each cell nucleus:

a) radius (mean of distances from center to points on the perimeter)
b) texture (standard deviation of gray-scale values) 
c) perimeter 
d) area 
e) smoothness (local variation in radius lengths) 
f) compactness (perimeter^2 / area - 1.0) 
g) concavity (severity of concave portions of the contour) 
h) concave points (number of concave portions of the contour) 
i) symmetry
j) fractal dimension ("coastline approximation" - 1)

The mean, standard error and "worst" or largest (mean of the three largest values) 
of these features were computed for each image, resulting in 30 features. 
For instance, field 3 is Mean Radius, field 13 is Radius SE, field 23 is Worst Radius.

All feature values are recoded with four significant digits.

Missing attribute values: none

Class distribution: 357 benign, 212 malignant
```````````````````
## 1- Data Analysis
To check the correlation of each input feature with the output look at the plots in the project.

#### Comparisison of a Benign vs Malignant tumor cell in an image

(Useful image to undestand the features used in the dataset to build my model)

![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Benign%20vs%20Malignant%20image.png)

A boxplot is used to look for possible outliers of each feature.

![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/BoxPlot.PNG)
Overall seems like features 11-19 (standard_error columns) have a few outliers, however not significally affecting our prediction so I did not remove them.  

Output features: Benign cell = 357 and Malignant = 212
![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Histogram.PNG)


##2- Neural network with a linear regression vs logistic regression
Using a SGD (sigmoid) optimizer because it works well for shallow networks, having binary-crossentropy for loss since it is binary classification and keeping track of metrics using accuracy.
Because it is a binary classification, linear regression does not work well compared to logistic regression. Output in Logistic regression is a binary value (0 or 1) and on Linear regression it predicts integer values, dependent variable is continuous. It can have any one of an infinite number of possible values.

![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/linear%20vs%20logistic.PNG)

For the first neural network using a linear activation

