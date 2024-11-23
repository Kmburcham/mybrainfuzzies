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
lm(formula = log_saleprice ~ I(horsepower^2) + age + enghours + 
    diesel + fwd + manual + johndeere + cab + spring + summer + 
    winter, data = tractor_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-1.81301 -0.34593  0.02571  0.33309  1.13072 

Coefficients:
                  Estimate Std. Error t value Pr(>|t|)    
(Intercept)      9.132e+00  1.291e-01  70.749  < 2e-16 ***
I(horsepower^2)  6.635e-06  9.271e-07   7.156 8.20e-12 ***
age             -2.979e-02  4.266e-03  -6.984 2.32e-11 ***
enghours        -2.309e-05  1.124e-05  -2.054 0.041005 *  
diesel           3.732e-01  1.157e-01   3.224 0.001421 ** 
fwd              2.881e-01  6.983e-02   4.125 4.97e-05 ***
manual          -1.505e-01  7.381e-02  -2.039 0.042438 *  
johndeere        3.083e-01  8.602e-02   3.584 0.000402 ***
cab              8.768e-01  7.027e-02  12.476  < 2e-16 ***
spring          -7.633e-02  7.724e-02  -0.988 0.323963    
summer          -1.952e-01  7.583e-02  -2.575 0.010575 *  
winter          -1.677e-01  8.488e-02  -1.976 0.049186 *  
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.4739 on 264 degrees of freedom
Multiple R-squared:  0.7128,	Adjusted R-squared:  0.7009 
F-statistic: 59.57 on 11 and 264 DF,  p-value: < 2.2e-16
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
even more. 


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
Multiple R-squared:  0.7128,	Adjusted R-squared:  0.7009 
F-statistic: 59.57 on 11 and 264 DF,  p-value: < 2.2e-16

I would suggest picking the log form horsepower regression as the best fit in the 
assignment thus far. Adding that horsepower squared decreased the adjusted r squared from 0.75 (without square)
to 0.70 (squared). P value stayed the same for both regressions. The regression without
horsepower squared also has a higher f-statistic, which is more valued. 





```


d. Again, use the best model that results from the answer to the previous question to address further questions.
	Use the model you have so far to test that the time of year has no effect on the sale of tractors.
	That is, test whether the t-statistics on the seasonal indicators are statistically significant. 
	Is there evidence that tractor prices follow a seasonal pattern? 

```
Enter your response here.
Use the coefficients from the regression output for this model to draw your conclusions.



```
	
	
e. Finally, consider another modification to your model. 
	Some say that John Deere tractors hold their value longer than other tractors. 
      This raises the question of whether an additional hour of use affects the value of a John Deere tractor 
	differently than for tractors of other brands. 
	You can test this by including an interaction with ```enghours:johndeere``` in the regression.
	
```
Enter your regression results here.



```

Test the hypothesis, at the 5 percent level of significance, that the slope for engine hours differs by brand. 

Does an additional hour of use affect the price of a John Deere tractor
differently than tractors of other brands?
	
```
Enter your response here.



```
	
	
	
