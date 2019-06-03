rm(list = ls())

#install.packages("drat", repos="https://cran.rstudio.com") 
#drat:::addRepo("dmlc") 
#install.packages("mxnet")

require(mxnet)

Bank<-read.table("bank.txt",header=T,sep=";")

############Data Pre-Processing#############
str(Bank)  
# subset categoric attributes (already these are factors)
bank_catg <- Bank[,c("job","marital","default","housing","loan",
                     "contact","poutcome","education","month")]

library(dummies)
bank_catg_dummy <- dummy.data.frame(bank_catg,sep = ".")
str(bank_catg_dummy)

# Subset numeric attributes 
bank_num <- Bank[,c("age","balance","day","campaign","pdays","previous")]
# convert the subsetted numerical attributes 
bank_num <- data.frame(apply(bank_num,2,function(x){as.character(x)}))
bank_num <- data.frame(apply(bank_num,2,function(x){as.numeric(x)}))

# Standardization the independent variables using decostand funcion in vegan R library
library(vegan)
# Note: To standardize the data using 'Range' method
independent_Variables = decostand(bank_num, "range")

#Recode the levels for "y"
Bank$outcome <- ifelse(Bank$y=="yes",1,0)
#Bank$outcome <- as.numeric(as.character(Bank$outcome))
Bank<-Bank[,-17]
Target <-subset(Bank,select = ("outcome"))
str(Target)
#Combine all attributes into final dataframe
Final_Data <-data.frame(bank_catg_dummy,independent_Variables,Target)
str(Final_Data)
sum(is.na(Final_Data)) 

library(caret)
set.seed(1234)
intrain = createDataPartition(y = Final_Data$outcome, p=0.7, list = F)
train.x = data.matrix(Final_Data[intrain, -51])
train.y = Final_Data[intrain, 51]
test.x = data.matrix(Final_Data[-intrain, -51])
test.y = Final_Data[-intrain, 51]

mx.set.seed(0)
Sys.time() -> start
model <- mx.mlp(train.x, train.y, hidden_node=c(10), out_node=1, activation="tanh", out_activation="logistic",
                 num.round=20, array.batch.size=100, learning.rate=0.02, momentum=0.9,
                 eval.metric=mx.metric.accuracy)
 Sys.time() -> end
 paste(end - start)
 
preds = predict(model, test.x)

preds=t(preds)
pred.label = ifelse(preds<0.55, 0, 1)

conf.mat = table(pred.label, test.y)
conf.mat
accuracy = sum(diag(conf.mat))/sum(conf.mat)
accuracy
precision = conf.mat[2,2]/sum(conf.mat[2,])
precision
recall = conf.mat[2,2]/sum(conf.mat[,2])
recall

table(test.y)

