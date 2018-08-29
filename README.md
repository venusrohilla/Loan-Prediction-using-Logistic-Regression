# Loan Prediction using Logistic Regression:

I referred the following resources for understanding Logistic Regression and building model.
* [UC Business Analytics R programming Guide](http://uc-r.github.io/)
* [Introduction to Logistic Regression with R](http://www.dataperspective.info/2015/10/introduction-to-logistic-regression.html)
* [Simple Guide to Logistic Regression in R](https://www.analyticsvidhya.com/blog/2015/11/beginners-guide-on-logistic-regression-in-r/)

#### Logistic Regression is a classification algorithm and not a prediction algorithm. It is used to predict a binary outcome (1 / 0, Yes / No, True / False) given a set of independent variables. To represent binary / categorical outcome, we use dummy variables.Logistic Regression is a special case of Linear Regression when the outcome variable is categorical where we are using log of odds as dependent variable.In simple words it predicts the probability of occurrence of an event by fitting data to a logit function.

# Logistic Regression Equation
For Linear Regression, where the output is a linear combination of input feature(s), we write the equation as:
            Y = βo + β1X + ∈     ,where Y is dependent variable, X is independent variable βo is the intercept and β1 is the coefficient and ∈ is the error term. 
In Logistic Regression, we use the same equation but with some modifications made to Y.Since  in logistic regression we try to calculate the probabilities and probabilities always lie between 0 and 1,as a result our response variable must be positive and lower than 1.
 As we know the exponential of any value is always a positive number. And, any number divided by number + 1 will always be lower than 1.
 so 
 ![put logit function image here](https://github.com/venusrohilla/Loan-Prediction-using-Logistic-Regression/blob/master/plots/logit%20function.PNG)
 
 Now the probability value will always lie between 0 and 1. To determine the link function,we do the following calculations. P(Y=1|X) can be read as "probability that Y =1 given some value for x." Y can take only two values, 1 or 0.let's rewrite P(Y=1|X) as p(X).
 Hence we get the following link function:

![put link equation image here](https://github.com/venusrohilla/Loan-Prediction-using-Logistic-Regression/blob/master/plots/link%20equation.PNG)
 
 The right side of the (immediate) equation above depicts the linear combination of independent variables. The left side is known as the log - odds or odds ratio or logit function and is the link function for Logistic Regression. 
 
 # Loan Prediction
 I have built a Logistic Regression model on a dataset containing- age,income,experience,family and other information about 5000 people and  predicting  whether a person will accept a loan or not depending on the information provided in the dataset.
