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
### Data normalization
BoxPlot is after data was normalized. Decided to normalize the data, because after building the model without normalizing the data, mae was equal with nan, increasing the batch size did not solve the problem. Normalizing will create a more robust data and the values with large magnitudes will not overwhelm small values.

Normalization used: y = (x - mean) / standard_deviation where standard_deviation = sqrt( sum( (x - mean)^2 ) / count(x))

The mean and standard deviation estimates of a dataset can be more robust to new data than the minimum and maximum.

Output features: Benign cell = 357 and Malignant = 212
![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Histogram.PNG)


## 2- Neural network with a linear regression vs logistic regression
Using a SGD (sigmoid) optimizer because it works well for shallow networks, having binary-crossentropy for loss since it is binary classification and keeping track of metrics using accuracy.
Because it is a binary classification, linear regression does not work well compared to logistic regression. Output in Logistic regression is a binary value (0 or 1) and on Linear regression it predicts integer values, dependent variable is continuous. It can have any one of an infinite number of possible values.

![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/linear%20vs%20logistic.PNG)


## 2&3- Performance difference when linear activation used instead of sigmoid (and vice versa)

## Linear Activation
* At the beginning I used a linear regresssion model, linear avtivation with 1 dense layer.
Epoch size = 128 and Batch size = 32, layer = 1, activation = linear
acc = 0.1450 and val_acc = 0.1953. 
(acc is the accuracy of a batch of training data and val_acc is the accuracy of a batch of testing data)
With this model Accuracy is very low from what we are looking, from a rate of 0-1, 0.1953 is not what we are aiming for. 
These results clearly tell us that a linear model is not the right one for our dataset and for the prediction 
that we are trying to get.
![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Linear%20model.PNG)

* Increasing the batch size to 250 and batch size to 64 still did not improve our predictions. Actually val_acc dropped by .02. (I am guessing that maybe overfitting is happening here since the dataset is not as large)
* Building a bigger model, with 32 dense layers, and 16 dense layers in between still did not improve our accuracy.
 ![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/neural%20network.png)
 
 
## Sigmoid activation

* First simple model created with 1 dense layer and epochs = 128, batch size = 32,
accuracy improved drastically. 
acc = 09775 and val_acc = 0.9822  (one of the best prediction I attained)
![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/sigmoid%20activation.PNG)

* Increasing the number of epochs to 256 and batch size to 64 increased my accuracy to 0.9645
 and acc = 0.9750  (loss = 0.0885) and also decreased loss
 ![alt test](https://github.com/Acelhaka/AIFinalProject/blob/master/sigmoid%20activation%20(increasing%20batch%20size).PNG)
 
 ## Bigger models
 * Model with 2 hidden layers, when activation for the first two layers is linear and the third is sigmoid, did not result with a better accuracy (val_ acc = 0.9704) than the simple logistic model.
 
 * Changing one of the hidden layers into RELU acivation slightly improved our accuracy. 
    val_acc = 0.9764 , acc = 0.9850, loss = 0.0437
 * Changing the first layers into RELU activation and keeping the last one sigmoid resulted with
    loss = 0.0335 (lower than previous models) loss = 0.0335 and val_acc = 0.9704
    
 ## Effort to code a function that represents my model.
  Used a model with one layer. 
  ![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/sigmoid%20function.PNG)
  
  ![alt text](https://github.com/Acelhaka/AIFinalProject/blob/master/Function%20prediction.PNG)
 
 
 
    
    
