# Assignment 3



Following the instructions in the document ```QMB6316_assignment_03.pdf``` above, 
enter your responses in the code blocks shown below.

*Please note that the document has been revised to clarify some details and correct a typo. These changes are shown in red.*


In this exercise, we will follow an approach different than that taken in class. 
We will first estimate a model with our choices of functional form, then consider exclusions of insignificant variables from the full model. 
Note that this approach allows for inclusion of possibly irrelevant variables and avoids excluding any relevant variables. 


At each stage, use the best model that you have found so far, 
incorporating the findings from the answer to the previous question.




a. Estimate a regression model that uses all available variables.
	Make sure to choose a reasonable transformation of the dependent variable, 
	such as the logarithmic transformation, if necessary.
	
```
Summary lm model
Call:
lm(formula = saleprice ~ horsepower + age + enghours + diesel + 
    fwd + manual + johndeere + cab + spring + summer + winter, 
    data = tractor_full)

Residuals:
   Min     1Q Median     3Q    Max 
-43367  -6939   -972   5698 106859 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept) 15478.1695  4511.5224   3.431 0.000698 ***
horsepower    183.7491    15.3139  11.999  < 2e-16 ***
age          -659.7654   148.2680  -4.450 1.27e-05 ***
enghours       -1.7932     0.3972  -4.514 9.58e-06 ***
diesel       1444.4664  4039.3857   0.358 0.720932    
fwd          2289.7272  2437.3099   0.939 0.348359    
manual      -4727.2221  2575.5053  -1.835 0.067563 .  
johndeere   13830.7849  3001.4687   4.608 6.33e-06 ***
cab         10589.8712  2622.7887   4.038 7.08e-05 ***
spring      -3005.2271  2698.7841  -1.114 0.266486    
summer      -7485.2891  2646.2313  -2.829 0.005033 ** 
winter      -6250.4788  2962.2099  -2.110 0.035793 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 16540 on 264 degrees of freedom
Multiple R-squared:  0.6073,	Adjusted R-squared:  0.5909 
F-statistic: 37.11 on 11 and 264 DF,  p-value: < 2.2e-16

Summary log model
Call:
lm(formula = log_saleprice ~ horsepower + age + enghours + diesel + 
    fwd + manual + johndeere + cab + spring + summer + winter, 
    data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.71960 -0.27081  0.06041  0.29064  0.93637 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  9.035e+00  1.179e-01  76.616  < 2e-16 ***
horsepower   4.287e-03  4.003e-04  10.709  < 2e-16 ***
age         -2.933e-02  3.876e-03  -7.569 6.31e-13 ***
enghours    -3.530e-05  1.038e-05  -3.400 0.000779 ***
diesel       3.188e-01  1.056e-01   3.019 0.002782 ** 
fwd          2.671e-01  6.371e-02   4.192 3.78e-05 ***
manual      -1.647e-01  6.732e-02  -2.447 0.015068 *  
johndeere    2.973e-01  7.846e-02   3.789 0.000187 ***
cab          6.899e-01  6.856e-02  10.063  < 2e-16 ***
spring      -1.015e-01  7.055e-02  -1.438 0.151552    
summer      -2.060e-01  6.917e-02  -2.978 0.003169 ** 
winter      -1.874e-01  7.743e-02  -2.420 0.016201 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4323 on 264 degrees of freedom
Multiple R-squared:  0.7609,	Adjusted R-squared:  0.751 
F-statistic:  76.4 on 11 and 264 DF,  p-value: < 2.2e-16

I am choosing the Log Model in this assignment as it has a higher adjusted r squared
compared to the lm model.

```

Does this seem to be a reasonable model, as opposed to using average tractor prices? 
Said differently, do at least some of the variables help to predict the prices of used tractors?
Is the R-squared or the R-bar-squared reasonably high?

```

The r squared and adjusted r squared are higher in the log form making it the better model to choose. 


```


b. Which variables seem to help explain used tractor prices? 
	Which have positive and negative relationships with tractor prices?
	Which variables that do not seem to have statistically significant coefficients under this specification?
	
```
I believe it is a reasonable model to use, however, some variables are not accurately 
related to the price of a tractor. Variables that are most significant in this model include horsepower, 
age, horsepower, diesel (fuel type), john deere (tractor brand), cab, and fwd. This is all based on the p
value analysis- any variables less than 0.05 is statistically significany with a lower number increasing
the significance of relation to tractor price. There are a few variables in this regression
that have a negative significant relationship such as: age, fwd, spring, engine hours. This means that for age
the older the tractor becomes, the less the price of the tractor will be. Alike with engine hours, the 
more a tractor was used prior to sell, decreases the price of the tractor. I assume spring is negative as it is 
planting and not harvesting seasons in which a tractor would not be used as much. All others increase the
price of a tractor is each unit is increased by its estimate. 


```



c. Before making any reductions to your model, revise the model specification first
	by considering nonlinear specifications.
	A used tractor dealer tells you that overpowered used tractors are hard to sell, since they consume more fuel. 
      Tractor prices often increase with horsepower, up to a point, but beyond that they decrease. 
      To incorporate this advice, you create and include a variable for squared horsepower and include that in a new regression model. 
      

```
Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + diesel + fwd + manual + johndeere + cab + 
    spring + summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.70032 -0.23458  0.05526  0.29542  0.74373 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.862e+00  1.114e-01  79.527  < 2e-16 ***
horsepower          1.125e-02  1.069e-03  10.533  < 2e-16 ***
squared_horsepower -1.569e-05  2.258e-06  -6.948 2.92e-11 ***
age                -3.205e-02  3.591e-03  -8.926  < 2e-16 ***
enghours           -4.089e-05  9.596e-06  -4.261 2.84e-05 ***
diesel              2.132e-01  9.842e-02   2.166  0.03121 *  
fwd                 2.761e-01  5.869e-02   4.704 4.12e-06 ***
manual             -1.534e-01  6.202e-02  -2.474  0.01400 *  
johndeere           3.100e-01  7.228e-02   4.289 2.52e-05 ***
cab                 4.762e-01  7.023e-02   6.781 7.85e-11 ***
spring             -1.115e-01  6.498e-02  -1.716  0.08741 .  
summer             -1.972e-01  6.372e-02  -3.095  0.00218 ** 
winter             -1.774e-01  7.132e-02  -2.487  0.01351 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.3982 on 263 degrees of freedom
Multiple R-squared:  0.798,	Adjusted R-squared:  0.7888 
F-statistic: 86.59 on 12 and 263 DF,  p-value: < 2.2e-16
```


  c.i) Hypothesize the signs for the coefficients on horsepower 
	under this scenario. 
		What should be the sign of the coefficient for horsepower? 
		What sign do you expect for squared horsepower?
      
```
I expected horsepower to be positive in the original regression as I had the impression
that an increase of horsepower would increase the value of a tractor for being able to 
handle more workload. It never occured to me that at some point too much horsepower is not
essential and could just cost a worker more in fuel. Squaring a value cannot mathmatically make it
have a negative impact, so squaring the variable would make it more signigicant, lowering the p value
even more. It should increase the adjusted r squared because it will be a more 
accurate representation of how Horsepower and Fuel interact with price.

```

  c.ii) Perform 1-sided t-tests of the hypotheses for each of the horsepower coefficients. 
That is, are the t-statistics higher than 1.96, with the same sign as you hypothesized?

```

Enter your response here.
Use the coefficients and t-statistics from the regression output for this model to draw your conclusions.



```

  c.iii) Compare the models with and without the quadratic functional form for horsepower.
            Which model do you recommend? 
		Be sure to cite evidence to support your choice. 
		Specifically, check the four specification criteria: 
		statistical significant $t$-statistics, 
		an increase in R-squared, 
		a good theoretical justification, and 
		no large change in the other coefficients.

```
Log sales & Horsepower- not squared
Multiple R-squared:  0.7609,	Adjusted R-squared:  0.751 
F-statistic:  76.4 on 11 and 264 DF,  p-value: < 2.2e-16

Log Sales & Horsepower- squared
Multiple R-squared:  0.798,	Adjusted R-squared:  0.7888 
F-statistic: 86.59 on 12 and 263 DF,  p-value: < 2.2e-16

I would suggest picking the log form horsepower squared regression as the best fit in the 
assignment thus far. Adding that horsepower squared increased the adjusted r squared from 0.751 (without square)
to 0.7888 (squared). P value stayed the same for both regressions. The regression with
horsepower squared also has a higher f-statistic, which is more valued. 

```


d. Again, use the best model that results from the answer to the previous question to address further questions.
	Use the model you have so far to test that the time of year has no effect on the sale of tractors.
	That is, test whether the t-statistics on the seasonal indicators are statistically significant. 
	Is there evidence that tractor prices follow a seasonal pattern? 

```
Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + diesel + fwd + manual + johndeere + cab, 
    data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.77600 -0.22279  0.04383  0.25746  0.78445 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.751e+00  1.078e-01  81.177  < 2e-16 ***
horsepower          1.121e-02  1.085e-03  10.335  < 2e-16 ***
squared_horsepower -1.586e-05  2.293e-06  -6.914 3.49e-11 ***
age                -3.159e-02  3.640e-03  -8.678 4.11e-16 ***
enghours           -4.035e-05  9.730e-06  -4.147 4.53e-05 ***
diesel              2.186e-01  9.970e-02   2.193   0.0292 *  
fwd                 2.809e-01  5.918e-02   4.746 3.38e-06 ***
manual             -1.606e-01  6.293e-02  -2.552   0.0113 *  
johndeere           3.121e-01  7.307e-02   4.272 2.70e-05 ***
cab                 4.857e-01  7.121e-02   6.820 6.09e-11 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4048 on 266 degrees of freedom
Multiple R-squared:  0.7888,	Adjusted R-squared:  0.7817 
F-statistic: 110.4 on 9 and 266 DF,  p-value: < 2.2e-16.

In this model you can see that there was a decrease in r square and adjusted r square.
Though this regression is removing negatively correlated variables, they are still
statisically signifanct to estimating tractor price. If you were to remove the season that is not 
significant to the model, you would get this regression output, which has removed "spring".

Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + diesel + fwd + manual + johndeere + cab + 
    summer + winter, data = tractor_full)

Residuals:
    Min      1Q  Median      3Q     Max 
-1.6958 -0.2222  0.0490  0.2501  0.7485 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.833e+00  1.106e-01  79.892  < 2e-16 ***
horsepower          1.116e-02  1.071e-03  10.420  < 2e-16 ***
squared_horsepower -1.560e-05  2.266e-06  -6.886 4.18e-11 ***
age                -3.195e-02  3.603e-03  -8.867  < 2e-16 ***
enghours           -4.094e-05  9.631e-06  -4.251 2.96e-05 ***
diesel              2.127e-01  9.878e-02   2.154  0.03218 *  
fwd                 2.701e-01  5.880e-02   4.594 6.73e-06 ***
manual             -1.564e-01  6.223e-02  -2.513  0.01258 *  
johndeere           3.079e-01  7.253e-02   4.245 3.03e-05 ***
cab                 4.762e-01  7.049e-02   6.755 9.07e-11 ***
summer             -1.560e-01  5.923e-02  -2.633  0.00895 ** 
winter             -1.360e-01  6.737e-02  -2.019  0.04454 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.3996 on 264 degrees of freedom
Multiple R-squared:  0.7958,	Adjusted R-squared:  0.7872 
F-statistic: 93.51 on 11 and 264 DF,  p-value: < 2.2e-16

This regression shows a slightly higher fit than removing the seasons entirely but 
it is slightly lower than the adjusted r squared in the original log regression with squared
horsepower which was .7888. From this, we can gather that tractor prices do follow season changes.
More tractor-useful seasons (winter and summer) result in an increase in tractor price. 


```
	
	
e. Finally, consider another modification to your model. 
	Some say that John Deere tractors hold their value longer than other tractors. 
      This raises the question of whether an additional hour of use affects the value of a John Deere tractor 
	differently than for tractors of other brands. 
	You can test this by including an interaction with ```enghours:johndeere``` in the regression.
	
```
Call:
lm(formula = log_saleprice ~ horsepower + squared_horsepower + 
    age + enghours + enghours:johndeere + diesel + fwd + manual + 
    johndeere + cab + summer + winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.69838 -0.22052  0.05042  0.24852  0.75596 

Coefficients:
                     Estimate Std. Error t value Pr(>|t|)    
(Intercept)         8.834e+00  1.109e-01  79.682  < 2e-16 ***
horsepower          1.115e-02  1.074e-03  10.382  < 2e-16 ***
squared_horsepower -1.557e-05  2.277e-06  -6.840 5.53e-11 ***
age                -3.196e-02  3.611e-03  -8.852  < 2e-16 ***
enghours           -4.147e-05  1.021e-05  -4.062 6.44e-05 ***
diesel              2.140e-01  9.928e-02   2.155  0.03204 *  
fwd                 2.698e-01  5.895e-02   4.576 7.30e-06 ***
manual             -1.558e-01  6.246e-02  -2.494  0.01325 *  
johndeere           2.950e-01  1.087e-01   2.715  0.00706 ** 
cab                 4.769e-01  7.075e-02   6.740 9.99e-11 ***
summer             -1.568e-01  5.959e-02  -2.632  0.00899 ** 
winter             -1.356e-01  6.754e-02  -2.008  0.04567 *  
enghours:johndeere  3.292e-06  2.070e-05   0.159  0.87377    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4004 on 263 degrees of freedom
Multiple R-squared:  0.7958,	Adjusted R-squared:  0.7865 
F-statistic:  85.4 on 12 and 263 DF,  p-value: < 2.2e-16

```

Test the hypothesis, at the 5 percent level of significance, that the slope for engine hours differs by brand. 

Does an additional hour of use affect the price of a John Deere tractor
differently than tractors of other brands?

```
The p value for enghours:johndeere is higher at 0.87377 (not statistically significant)	
	Testing the p value 0.050 > then we fail to reject the null hypothesis meaning there is not a increase 
	or decrease in price of a tractor, john deere or non-john deere with any additional hours of engine usage.

```
	
	
	
