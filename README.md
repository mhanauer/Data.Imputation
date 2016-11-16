# Data.Imputation
# This describes how to impute data using knnImpute with the Caret package
# Build an algorithm that predicts mpg from the variables in the data set
# This version can take a new data set and include the pre processing in the caret package
#install.packages("caret")
library(caret)
#install.packages("mlbench")
# This is to create some missing values to see if the pre processing works
library(mlbench)
set.seed(42)
mtcars[sample(1:nrow(mtcars), 10), "hp"] = NA
# Do the preprocessing outside the function, because it won't work inside the function
mtcars.knn = preProcess(mtcars, method = c("knnImpute")); mtcars_knn
#install.packages("RANN")
library(RANN)
mtcars.knn.pred =  predict(mtcars_knn, mtcars)
