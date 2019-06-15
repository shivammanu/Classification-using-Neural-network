# Neural_network

## Training Neural Networks on multiple data sets for

A marketing department of a bank runs various marketing campaigns for cross-selling products, improving customer retention and better customer services. Let us take a marketing data sample in which the bank is interested in selling a term deposit product to its existing customers.
Contacting all customers is costly and does not create good customer experience. So, the bank wants to build a predictive model which will identify customers who are more likely to respond to the marketing campaign.



The dataset “housing.csv” has information on the housing values in suburbs of Boston. Predict the median value of the owner occupied homes “OwnOcc” using neural net algorithm. The attributes description is given below:
1. Crimerate: per capita crime rate by town
2. ResiLandZone: proportion of residential land zoned for lots over 25,000 sq.ft.
3. INDUS: proportion of nonretail business acres per town
4. CHAS: Charles River dummy variable (= 1 if tract bounds river; 0 otherwise)
5. NOX: nitric oxides concentration (parts per 10 million)
6. Rooms: average number of rooms per dwelling
7. AGE: proportion of owner occupied units built prior to 1940
8. Distance: weighted distances to five Boston employment centers
9. RAD: index of accessibility to radial highways
10. TAX: full value property tax rate per $10,000
11. PTRATIO: pupil teacher ratio by town
12. Blacks: 1000(Bk 0.63)^2 where Bk is the proportion of blacks by town
13. LSTAT: % lower status of the population


## Steps
1. Read “housing.csv” file into R
2. install.packages("drat", repos="https://cran.rstudio.com")
#drat:::addRepo("dmlc")
#install.packages("mxnet")
3. Study structure, summary etc.
4. Apply type conversion to attributes if necessary.
5. If attributes are categorical, convert them into dummies.
