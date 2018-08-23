```{r}
getwd()
loan<-read.csv("loan.csv")
summary(loan)
```
```{r}
head(loan)
```
```{r}
loan<-loan[loan$Experience>0,]
summary(loan)
```
```{r}
hist(loan$Income)
```
#here we have to find whether accepted loan or not and that outcome is in 0 or 1
#have to find how many are 0 or 1.
```{r}
loannew=loan
t=loannew[,'PersonalLoan']==1
table(t)
```
#1's are less than 0's and while creating the test data our model could be
#biased towards zero,so we have create a data train test 
```{r}
classone=loannew[t,]
classzero=loannew[!t,]
classzero
```
```{r}
set.seed(222)
t=sample(1:nrow(classone),floor(0.5*nrow(classone)))
```
```{r}
classone_train=classone[t,]
classone_test=classone[-t,]
classzero_train=classzero[t,]
classzero_test=classzero[-t,]
classone_train
```
#training and test data for dependent and independent variable
```{r}
PlIndex=which(names(loan) %in% "PersonalLoan")
```
#which func. gives the position where the
#above condition satisfies here personalloan is 9th col. so PlIndex=9 
```{r}
View(PlIndex)
```
```{r}
Xtrain=rbind(classone_train[,-PlIndex],classzero_train[,-PlIndex])
Xtest=rbind(classone_test[,-PlIndex],classzero_test[,-PlIndex])
ytrain=c(classone_train[,PlIndex],classzero_train[,PlIndex])
ytest= c(classone_test[,PlIndex],classzero_test[,PlIndex])
```
```{r}
Mod=glm(ytrain~Age+Experience+Income+as.factor(Family)+CCAvg+as.factor(Education)+Mortgage+as.factor(SecuritiesAccount)+as.factor(CDAccount)+as.factor(Online)+as.factor(CreditCard),family=binomial,data=data.frame(Xtrain))
summary(Mod)
```
```{r}
Mod1=glm(ytrain~Age+Income+as.factor(Family)+as.factor(Education)+as.factor(SecuritiesAccount)+as.factor(CDAccount)+as.factor(Online)+as.factor(CreditCard),family=binomial,data=data.frame(Xtrain))
summary(Mod1)
```
```{r}
Mod2=Mod=glm(ytrain~Income+as.factor(Family)+as.factor(Education)+as.factor(CDAccount)+as.factor(Online),family=binomial,data=data.frame(Xtrain))
sury=summary(Mod2)
sury
```
```{r}
IncomeEst=sury$coefficients["Income","Estimate"]
(exp(IncomeEst)-1)*100
```
#prediction
```{r}
PredTest=predict(Mod,newdata=data.frame(Xtest),type="response")
classify=floor(PredTest+0.5)
ClassifyTable=table(ytest,classify)
ClassifyTable
classify1=floor(PredTest+0.6)
ClassifyTable1=table(ytest,classify)
ClassifyTable1
classify2=floor(PredTest+0.4)
ClassifyTable2=table(ytest,classify)
ClassifyTable2
```
```{r}
error=(ClassifyTable[1,2]+ClassifyTable[2,1])/length(PredTest)
error*100
```
```{r}
library(pscl)
install.packages("ROCR")
library(ROCR)
pr<-prediction(PredTest,yTest)
prf<-performance(pr,measure="tpr",x.measure)
```