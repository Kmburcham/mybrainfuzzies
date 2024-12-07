# Final Examination

## Due Friday, December 6, 2024 at 11:59 PM in your GitHub repository.

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

*Please see the revised version of the pdf copy of the question paper, uploaded Nov. 23, 2024.*

## Part A: Data Handling and Preliminary Regression Modelling

### Question 1

a) Read in the ```airplane_sales.csv``` dataset and store it in a data frame called ```airplane_sales``` in your workspace. 


```

airplane_sales <- read_csv("~/GitHub/mybrainfuzzies/final_exam/airplane_sales.csv")

```

b) Calculate and copy the printed output from a ```summary``` of the data. 
Use this to get familiar with the contents of the dataset. 


```

airplane_sales <- read.csv('airplane_sales.csv')

# Inspect the contents.
summary(airplane_sales)

X0Sale_ID          age            price       
 Min.   :101.0   Min.   :13.00   Min.   :  9000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250  
 Median :198.0   Median :22.00   Median : 33500  
 Mean   :198.0   Mean   :24.61   Mean   : 50237  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500  
 Max.   :295.0   Max.   :44.00   Max.   :254000  


```

c) Estimate a regression model to predict ```price``` as a function of ```age```. 
Copy the printed estimation output from the ```summary``` command. 


```
lm_model_1 <- lm(data = airplane_sales,
                 formula = price ~ age + Sale_ID) 

summary(lm_model_1)

Call:
lm(formula = price ~ age + Sale_ID, data = airplane_sales)

Residuals:
   Min     1Q Median     3Q    Max 
-36273 -11306  -4024   8330 179397 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 22805.85   11142.46   2.047    0.042 *  
age         -2332.28     266.00  -8.768 9.68e-16 ***
Sale_ID       428.43      32.77  13.073  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 23270 on 192 degrees of freedom
Multiple R-squared:  0.6883,	Adjusted R-squared:  0.6851 
F-statistic:   212 on 2 and 192 DF,  p-value: < 2.2e-16
```


### Question 2

a) Read in the ```airplane_specs.csv``` dataset and store it 
in a data frame called ```airplane_specs``` in your workspace. 


```

library(readr)
airplane_specs <- read_csv("airplane_specs.csv")
View(airplane_specs)

```

b)  Form a dataset ```airplane_sales_specs.csv``` 
by ```merge```ing the data frames 
```airplane_sales.csv``` and ```airplane_specs.csv```. 
Store the new dataset in a data frame called 
```airplane_sales_specs``` in your workspace. 


```
# Join the two datasets.

airplane_sales_specs <- merge(airplane_sales, airplane_specs, all = TRUE)

# Verify that the data were joined correctly.
summary(airplane_sales_specs)

```


c) Calculate and copy the printed output from a ```summary``` of the data. 
Use this to get familiar with the contents of the dataset. 


```

 summary(airplane_sales_specs)
    Sale_ID           age            price             pass            wtop       
 Min.   :101.0   Min.   :13.00   Min.   :  9000   Min.   :2.000   Min.   :0.0000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250   1st Qu.:4.000   1st Qu.:0.0000  
 Median :198.0   Median :22.00   Median : 33500   Median :4.000   Median :0.0000  
 Mean   :198.0   Mean   :24.61   Mean   : 50237   Mean   :4.287   Mean   :0.4615  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500   3rd Qu.:6.000   3rd Qu.:1.0000  
 Max.   :295.0   Max.   :44.00   Max.   :254000   Max.   :6.000   Max.   :1.0000  
    fixgear           tdrag        
 Min.   :0.0000   Min.   :0.00000  
 1st Qu.:0.0000   1st Qu.:0.00000  
 Median :0.0000   Median :0.00000  
 Mean   :0.4513   Mean   :0.05641  
 3rd Qu.:1.0000   3rd Qu.:0.00000  
 Max.   :1.0000   Max.   :1.00000  

```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```. 
Copy the printed estimation output from the ```summary``` command. 


```
lm_model_2 <- lm(data = airplane_sales_specs,
                 formula = price ~ age + pass + wtop + fixgear + tdrag) 

summary(lm_model_2)

summary(lm_model_2)

Call:
lm(formula = price ~ age + pass + wtop + fixgear + tdrag, data = airplane_sales_specs)

Residuals:
   Min     1Q Median     3Q    Max 
-34133 -13201  -2957   8476 145275 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  42071.7     9364.6   4.493 1.22e-05 ***
age          -2544.7      256.1  -9.935  < 2e-16 ***
pass         15635.9     1690.8   9.248  < 2e-16 ***
wtop         -1809.3     3459.7  -0.523  0.60161    
fixgear      13552.4     4794.3   2.827  0.00521 ** 
tdrag       -27030.8     8402.5  -3.217  0.00152 ** 
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 22040 on 189 degrees of freedom
Multiple R-squared:  0.7249,	Adjusted R-squared:  0.7176 
F-statistic:  99.6 on 5 and 189 DF,  p-value: < 2.2e-16

```




### Question 3

a) Read in the ```airplane_perf.csv``` dataset and store it 
in a data frame called ```airplane_perf``` in your workspace. 


```

library(readr)
airplane_perf <- read_csv("airplane_perf.csv")
View(airplane_perf)

```

b) Form a dataset ```airplane_full.csv``` 
by ```merge```ing all three datasets. 
Store the new dataset 
in a data frame called ```airplane_full``` in your workspace. 


```

# Join the two datasets.

airplane_full <- merge(airplane_sales_specs, airplane_perf, all = TRUE)

# Verify that the data were joined correctly.
summary(airplane_full)

```

c) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```
airplane_full <- merge(airplane_sales_specs, airplane_perf, all = TRUE)
> 
> # Verify that the data were joined correctly.
> summary(airplane_full)
    Sale_ID           age            price             pass            wtop       
 Min.   :101.0   Min.   :13.00   Min.   :  9000   Min.   :2.000   Min.   :0.0000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250   1st Qu.:4.000   1st Qu.:0.0000  
 Median :198.0   Median :22.00   Median : 33500   Median :4.000   Median :0.0000  
 Mean   :198.0   Mean   :24.61   Mean   : 50237   Mean   :4.287   Mean   :0.4615  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500   3rd Qu.:6.000   3rd Qu.:1.0000  
 Max.   :295.0   Max.   :44.00   Max.   :254000   Max.   :6.000   Max.   :1.0000  
    fixgear           tdrag             horse            fuel           ceiling     
 Min.   :0.0000   Min.   :0.00000   Min.   :108.0   Min.   : 29.00   Min.   : 8500  
 1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:180.0   1st Qu.: 51.00   1st Qu.: 9700  
 Median :0.0000   Median :0.00000   Median :210.0   Median : 68.00   Median :13000  
 Mean   :0.4513   Mean   :0.05641   Mean   :219.2   Mean   : 67.79   Mean   :14007  
 3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:285.0   3rd Qu.: 84.00   3rd Qu.:16800  
 Max.   :1.0000   Max.   :1.00000   Max.   :310.0   Max.   :130.00   Max.   :28000  
     cruise     
 Min.   : 97.0  
 1st Qu.:119.0  
 Median :144.0  
 Mean   :144.7  
 3rd Qu.:170.0  
 Max.   :221.0  


```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```, 
as well as ```horse```, ```fuel```, ```ceiling```, and ```cruise```.
Copy the printed estimation output from the ```summary``` command. 


```

lm_model_3 <- lm(data = airplane_full,
                 formula = price ~ age + pass + wtop + fixgear + tdrag + horse + fuel + ceiling + cruise) 

summary(lm_model_3)

Call:
lm(formula = price ~ age + pass + wtop + fixgear + tdrag + horse + 
    fuel + ceiling + cruise, data = airplane_full)

Residuals:
   Min     1Q Median     3Q    Max 
-40971  -9653  -1189   7035 127745 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept) -4.189e+04  1.440e+04  -2.910  0.00406 ** 
age         -2.354e+03  2.338e+02 -10.070  < 2e-16 ***
pass         5.586e+03  2.218e+03   2.518  0.01264 *  
wtop        -9.928e+03  3.118e+03  -3.184  0.00170 ** 
fixgear     -3.096e+04  6.802e+03  -4.552 9.62e-06 ***
tdrag       -4.925e+04  7.909e+03  -6.226 3.13e-09 ***
horse        2.241e+02  6.720e+01   3.335  0.00103 ** 
fuel        -3.038e+01  1.264e+02  -0.240  0.81033    
ceiling      1.525e+00  5.261e-01   2.899  0.00420 ** 
cruise       5.460e+02  1.117e+02   4.886 2.22e-06 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 18840 on 185 degrees of freedom
Multiple R-squared:  0.8032,	Adjusted R-squared:  0.7936 
F-statistic:  83.9 on 9 and 185 DF,  p-value: < 2.2e-16



```






## Part B: Advanced Regression Modelling


### Question 4

a) Create new variables 
	```log_price```, ```log_age```, ```log_horse```, 
	```log_fuel```, ```log_ceiling```, and ```log_cruise```
	from the variables 
	```price```, ```age```, ```horse```, 
	```fuel```, ```ceiling```, and ```cruise```, 
	using the logarithm function ```log()``` in ```R``` 
	to create these new variables. 


```

airplane_full[, 'log_price'] <- log(airplane_full[, 'price'])
airplane_full[, 'log_age'] <- log(airplane_full[, 'age'])
airplane_full[, 'log_horse'] <- log(airplane_full[, 'horse'])
airplane_full[, 'log_fuel'] <- log(airplane_full[, 'fuel'])
airplane_full[, 'log_ceiling'] <- log(airplane_full[, 'ceiling'])
airplane_full[, 'log_cruise'] <- log(airplane_full[, 'cruise'])

lm_model_4 <- lm(data = airplane_full,
                 formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + log_horse + log_fuel + log_ceiling + log_cruise) 

summary(airplane_full)

```

b) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```
summary(airplane_full)
    Sale_ID           age            price             pass            wtop       
 Min.   :101.0   Min.   :13.00   Min.   :  9000   Min.   :2.000   Min.   :0.0000  
 1st Qu.:149.5   1st Qu.:19.00   1st Qu.: 19250   1st Qu.:4.000   1st Qu.:0.0000  
 Median :198.0   Median :22.00   Median : 33500   Median :4.000   Median :0.0000  
 Mean   :198.0   Mean   :24.61   Mean   : 50237   Mean   :4.287   Mean   :0.4615  
 3rd Qu.:246.5   3rd Qu.:30.00   3rd Qu.: 73500   3rd Qu.:6.000   3rd Qu.:1.0000  
 Max.   :295.0   Max.   :44.00   Max.   :254000   Max.   :6.000   Max.   :1.0000  
    fixgear           tdrag             horse            fuel           ceiling     
 Min.   :0.0000   Min.   :0.00000   Min.   :108.0   Min.   : 29.00   Min.   : 8500  
 1st Qu.:0.0000   1st Qu.:0.00000   1st Qu.:180.0   1st Qu.: 51.00   1st Qu.: 9700  
 Median :0.0000   Median :0.00000   Median :210.0   Median : 68.00   Median :13000  
 Mean   :0.4513   Mean   :0.05641   Mean   :219.2   Mean   : 67.79   Mean   :14007  
 3rd Qu.:1.0000   3rd Qu.:0.00000   3rd Qu.:285.0   3rd Qu.: 84.00   3rd Qu.:16800  
 Max.   :1.0000   Max.   :1.00000   Max.   :310.0   Max.   :130.00   Max.   :28000  
     cruise        log_price         log_age        log_horse        log_fuel      log_ceiling    
 Min.   : 97.0   Min.   : 9.105   Min.   :2.565   Min.   :4.682   Min.   :3.367   Min.   : 9.048  
 1st Qu.:119.0   1st Qu.: 9.865   1st Qu.:2.944   1st Qu.:5.193   1st Qu.:3.932   1st Qu.: 9.180  
 Median :144.0   Median :10.419   Median :3.091   Median :5.347   Median :4.220   Median : 9.473  
 Mean   :144.7   Mean   :10.519   Mean   :3.166   Mean   :5.349   Mean   :4.169   Mean   : 9.499  
 3rd Qu.:170.0   3rd Qu.:11.205   3rd Qu.:3.401   3rd Qu.:5.652   3rd Qu.:4.431   3rd Qu.: 9.729  
 Max.   :221.0   Max.   :12.445   Max.   :3.784   Max.   :5.737   Max.   :4.868   Max.   :10.240  
   log_cruise   
 Min.   :4.575  
 1st Qu.:4.779  
 Median :4.970  
 Mean   :4.953  
 3rd Qu.:5.136  
 Max.   :5.398  

```


c) Estimate a regression model to predict ```log_price``` as a function of 
	```log_age```, ```pass```, ```wtop```, ```fixgear```, 
	and ```tdrag```, 
	as well as 
	```log_horse```, ```log_fuel```, ```log_ceiling```, 
	and ```log_cruise```. 
	Copy the printed estimation output from the ```summary``` command. 


```

lm_model_4 <- lm(data = airplane_full,
                 formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + log_horse + log_fuel + log_ceiling + log_cruise) 

summary(lm_model_4)

Call:
lm(formula = log_price ~ log_age + pass + wtop + fixgear + tdrag + 
    log_horse + log_fuel + log_ceiling + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.50754 -0.11123  0.00186  0.11226  0.53375 

Coefficients:
             Estimate Std. Error t value Pr(>|t|)    
(Intercept)  3.786112   1.067378   3.547 0.000494 ***
log_age     -1.527922   0.063521 -24.054  < 2e-16 ***
pass         0.048006   0.021645   2.218 0.027776 *  
wtop        -0.048649   0.031384  -1.550 0.122823    
fixgear     -0.179043   0.075662  -2.366 0.018998 *  
tdrag       -0.459069   0.081906  -5.605 7.47e-08 ***
log_horse    1.021321   0.135777   7.522 2.27e-12 ***
log_fuel     0.167589   0.084245   1.989 0.048141 *  
log_ceiling -0.005037   0.088651  -0.057 0.954748    
log_cruise   1.086126   0.195242   5.563 9.18e-08 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1896 on 185 degrees of freedom
Multiple R-squared:  0.9438,	Adjusted R-squared:  0.9411 
F-statistic: 345.5 on 9 and 185 DF,  p-value: < 2.2e-16


```


d) If you notice that any coefficients are statistically insignificant, 
	estimate the model by removing them one at a time. 
	For each variable removed, 
	determine whether the variable should be removed 
	by considering the four specification criteria: 
		statistically significant $t$-statistics, 
		an increase in ```R-bar-squared```, 
		a good theoretical justification, and 
		no large change in the other coefficients.


```
lm_model_5 <- lm(data = airplane_full,
                 formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + log_fuel + log_ceiling + log_cruise) 
                 
summary(lm_model_5)
# removed wtop as the first insignificant variable

Call:
lm(formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + 
    log_fuel + log_ceiling + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.11120  0.01233  0.11318  0.55682 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.24337    1.02967   4.121 5.67e-05 ***
log_age     -1.52909    0.06376 -23.984  < 2e-16 ***
pass         0.05215    0.02156   2.419   0.0165 *  
fixgear     -0.13729    0.07097  -1.934   0.0546 .  
tdrag       -0.45681    0.08220  -5.557 9.39e-08 ***
log_horse    0.98983    0.13475   7.345 6.24e-12 ***
log_fuel     0.17135    0.08453   2.027   0.0441 *  
log_ceiling -0.02693    0.08785  -0.307   0.7595    
log_cruise   1.05544    0.19497   5.413 1.89e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1903 on 186 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.9407 
F-statistic: 385.5 on 8 and 186 DF,  p-value: < 2.2e-16

In the first model the wtop characteristics was removed .048649   0.031384  -1.550 0.122823  
The T-statistic was not statisitcally significant. The adjusted r squared decreased. With removing this variable, the
adjusted r-squared decreased from 0.9411 to 0.9407, though not significant amount of decrease, 
it should be left in the model. There was also a larger change in variables when removing wtop potentially
suggesting multicollinearity. 

Removing wtop and reducing the adjusted r squared to a lower value than the previous model does not
make the model bad. It is a more simplified version that is not victim to overfitting and wtop could be
artifically inflating the adjusted r-sqaured. This model could be accepted. 

```

Next regression model:

```
lm_model_6 <- lm(data = airplane_full,
                 formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + log_fuel + log_cruise) 

summary(lm_model_6)

Call:
lm(formula = log_price ~ log_age + pass + fixgear + tdrag + log_horse + 
    log_fuel + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.10900  0.01349  0.11515  0.54790 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.07670    0.87236   4.673 5.66e-06 ***
log_age     -1.52942    0.06359 -24.051  < 2e-16 ***
pass         0.05188    0.02149   2.414   0.0167 *  
fixgear     -0.14417    0.06717  -2.147   0.0331 *  
tdrag       -0.46649    0.07571  -6.161 4.32e-09 ***
log_horse    0.98598    0.13384   7.367 5.44e-12 ***
log_fuel     0.17238    0.08426   2.046   0.0422 *  
log_cruise   1.04191    0.18944   5.500 1.24e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1898 on 187 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.941 
F-statistic: 442.7 on 7 and 187 DF,  p-value: < 2.2e-16

This model takes out all statistically insignificant variables from the original model: log_ceiling and wtop.
These variables both had T-scores that were not signigicant to 1.96 in either direction. The p-values also
were not testing significant. The adjusted r-squared did not signigicantly change suggesting that the 
variables in no way add to the correlation of the regression. These varaibles did not over adjust the r-sqaured
value but added more clutter. The remaining variables did not change significantly from the original run.



```

Next regression model, if necessary:

```
lm_model_7 <- lm(data = airplane_full,
                 formula = log_price ~ log_age + pass + fixgear + wtop + tdrag + log_horse + log_fuel + log_cruise) 
                 
summary(lm_model_7)

Call:
lm(formula = log_price ~ log_age + pass + fixgear + wtop + tdrag + 
    log_horse + log_fuel + log_cruise, data = airplane_full)

Residuals:
     Min       1Q   Median       3Q      Max 
-0.50764 -0.11136  0.00149  0.11191  0.53199 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  3.75306    0.89258   4.205 4.06e-05 ***
log_age     -1.52798    0.06334 -24.122  < 2e-16 ***
pass         0.04793    0.02155   2.224   0.0273 *  
fixgear     -0.18054    0.07073  -2.553   0.0115 *  
wtop        -0.04893    0.03090  -1.584   0.1150    
tdrag       -0.46085    0.07549  -6.105 5.87e-09 ***
log_horse    1.02080    0.13511   7.555 1.83e-12 ***
log_fuel     0.16775    0.08397   1.998   0.0472 *  
log_cruise   1.08384    0.19053   5.689 4.90e-08 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1891 on 186 degrees of freedom
Multiple R-squared:  0.9438,	Adjusted R-squared:  0.9414 
F-statistic: 390.8 on 8 and 186 DF,  p-value: < 2.2e-16

I chose to add back in wtop and remove log_ceiling as it was the next variable 
that was not statistically significant. The t-score was -0.307 making it not statisitcally
significant to this model. The adjusted r-squared for this model increased from .9407 to .9414
This shows that removing log_ceiling and replacing wtop bettered the model. 

This is the last model in which I could get a higher adjusted r-squared than the original summary.


```

Next regression model, if necessary:

```

Copy your regression results here.


```

Next regression model, if necessary:

```

Copy your regression results here.


```



e) Print the output from a ```summary``` of the regression results
of your final regression model.


```
Residuals:
     Min       1Q   Median       3Q      Max 
-0.49050 -0.10900  0.01349  0.11515  0.54790 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept)  4.07670    0.87236   4.673 5.66e-06 ***
log_age     -1.52942    0.06359 -24.051  < 2e-16 ***
pass         0.05188    0.02149   2.414   0.0167 *  
fixgear     -0.14417    0.06717  -2.147   0.0331 *  
tdrag       -0.46649    0.07571  -6.161 4.32e-09 ***
log_horse    0.98598    0.13384   7.367 5.44e-12 ***
log_fuel     0.17238    0.08426   2.046   0.0422 *  
log_cruise   1.04191    0.18944   5.500 1.24e-07 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 0.1898 on 187 degrees of freedom
Multiple R-squared:  0.9431,	Adjusted R-squared:  0.941 
F-statistic: 442.7 on 7 and 187 DF,  p-value: < 2.2e-16

```

f) Finally, for each of the variables in the datasets, 
	list those that are positively related to airplane prices,
	negatively related to airplane prices, 
	and statistically unrelated to airplane prices. 


```
All of these variables are taken from the second regression where both insignificant variable are removed. I think 
my third regression was more for fun...and not the requirement. 


Positively related:
pass         0.05188    0.02149   2.414   0.0167 * 
log_horse    0.98598    0.13384   7.367 5.44e-12 ***
log_fuel     0.17238    0.08426   2.046   0.0422 *  
log_cruise   1.04191    0.18944   5.500 1.24e-07 ***

Increase of horsepower, fuel, and the ability to cruise at higher speeds increases with the 
price of an airplane. 

Negatively related:
log_age     -1.52942    0.06359 -24.051  < 2e-16 ***
fixgear     -0.14417    0.06717  -2.147   0.0331 *  
tdrag       -0.46649    0.07571  -6.161 4.32e-09 ***

A decrease in age, if a plane has fixed landing gear, wings above the fuselage, and if there are wheels on the tail
are inversely related to the price of an airplane. One would assume that having landing gear is sufficient enough and a fixed
position would not make or break a deal. Age of course of would decrease any price of most machinary. 

Statistically unrelated:
wtop        -0.048649   0.031384  -1.550 0.122823
log_ceiling -0.005037   0.088651  -0.057 0.954748

Wings in the center of the plane (fuselage) I would think depends on the body of the plane style...(almost all are centerd) so there is not much room 
for a great fit in this model for this variable. 
Ceiling height in this regression is also not significant because one would assume there is an industry standard or 
relies heavily on the style and use of the plane ie megabus from US to a European country that takes 24 hours and has three floors compared
to a Delta line flight from Orlando to NYC. 

```




## Part C: Version Control

### Question 5

Push your completed files to the ```final_exam``` folder 
in your private GitHub repository.