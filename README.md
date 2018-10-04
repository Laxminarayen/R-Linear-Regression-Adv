# R-Linear-Regression-Deep
Build a minimal error Linear regressing model using the given dataset and there by forming equation to predict the 'Sale Price'
#library(magrittr)
#library(caret)
#library(dplyr)
A <- read.csv("E://housetrain.csv")
colSums(is.na(A))
str(A)
A <- A[,-c(7,58,73,74,75)]
colSums(is.na(A))
A <- na.omit(A)
d <- createDataPartition(A$SalePrice,p =0.9,list = FALSE) %>% c()
train <- A[d,]
test <- A[-d,]
model5 <- lm(SalePrice~OverallQual+YearBuilt+YearRemodAdd+TotalBsmtSF+GrLivArea+FullBath+GarageCars,A)
summary(model5)
colnames(A)
f <- predict(model5,test)
RMSE(f,test$SalePrice)
plot(model5)
