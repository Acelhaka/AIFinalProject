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

The mean, standard error and "worst" or largest (mean of the three largest values) of these features were computed for each image, resulting in 30 features. 
For instance, field 3 is Mean Radius, field 13 is Radius SE, field 23 is Worst Radius.

All feature values are recoded with four significant digits.

Missing attribute values: none
`````````````
Class distribution: 357 benign, 212 malignant
![alt text]()


