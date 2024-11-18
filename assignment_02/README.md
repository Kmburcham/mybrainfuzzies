# Assignment 2

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

## Running the Script as Given

Run the entire script and compare 
the output from ```summary(lm_full_model)```, 
which includes all variables, 
with that from ```summary(lm_no_damage)```, 
which omits the damage indicator. 
If there are no cars with damage in your simulation, 
run the script again to take another draw.


a. Copy and paste the regression model estimates after the commands
```summary(lm_full_model)``` and ```summary(lm_no_damage)```. 

```
Call:
lm(formula = car_price ~ mileage + accident + damage, data = car_data)

Residuals:
    Min      1Q  Median      3Q     Max 
-9128.8 -2860.9   -86.1  2757.3  9853.6 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.366e+04  2.328e+03  23.054  < 2e-16 ***
mileage     -2.756e-01  4.315e-02  -6.387 6.02e-09 ***
accident    -5.605e+03  8.884e+02  -6.310 8.59e-09 ***
damage      -1.950e+04  1.505e+03 -12.954  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3963 on 96 degrees of freedom
Multiple R-squared:  0.7683,	Adjusted R-squared:  0.7611 
F-statistic: 106.1 on 3 and 96 DF,  p-value: < 2.2e-16

Call:
lm(formula = car_price ~ mileage + accident, data = car_data)

Residuals:
     Min       1Q   Median       3Q      Max 
-20440.2  -2879.3    752.4   3781.3  12428.1 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.143e+04  3.828e+03  13.434  < 2e-16 ***
mileage     -2.331e-01  7.096e-02  -3.285  0.00142 ** 
accident    -9.825e+03  1.363e+03  -7.208 1.24e-10 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 6536 on 97 degrees of freedom
Multiple R-squared:  0.3634,	Adjusted R-squared:  0.3503 
F-statistic: 27.69 on 2 and 97 DF,  p-value: 3.07e-10


```


b. Compare the estimated coefficient for ```ACCIDENT``` 
with and without the damage variable. 
How does this relate to the coefficient for ```DAMAGE```?

```
In a regression model, a negative coefficient correlation could stimulate a lack
of relationship between the variables being tested. When car prices were tested
with damage, the regression model was a closer fit to the data in determining the
right regression formula. Damage excluded in the regression formula makes the 
coefficient accident a less likely predictor of the cars price. The amount of damage
to a vehicle drastically changes the price of a vehicle. 
```


c. Compare the values of 
```Multiple R-squared``` and ```Adjusted R-squared``` for the two models. 
Which model do you recommend (pretending that you don't know the true model)? 

```
In a regression model, the adjusted r squared is the better fit for a better predicted
model, however, you want to choose the one that is closer to one. In this scenario, 
the adjusted r squared for model 1 is the better fit with the inclusion of damage to vehicles.
0.7611 is closer to one than 0.3503 found in model 2. 

```




## Running the Script after Modification


d. Copy and paste the new regression model estimates after the commands
```summary(lm_full_model)``` and ```summary(lm_no_damage)```. 

```
Call:
lm(formula = car_price ~ mileage + accident + damage, data = car_data)

Residuals:
    Min      1Q  Median      3Q     Max 
-9128.8 -2860.9   -86.1  2757.3  9853.6 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.366e+04  2.328e+03  23.054  < 2e-16 ***
mileage     -2.756e-01  4.315e-02  -6.387 6.02e-09 ***
accident    -5.605e+03  8.884e+02  -6.310 8.59e-09 ***
damage      -1.950e+04  1.505e+03 -12.954  < 2e-16 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 3963 on 96 degrees of freedom
Multiple R-squared:  0.7683,	Adjusted R-squared:  0.7611 
F-statistic: 106.1 on 3 and 96 DF,  p-value: < 2.2e-16


Call:
lm(formula = car_price ~ mileage + accident, data = car_data)

Residuals:
     Min       1Q   Median       3Q      Max 
-20440.2  -2879.3    752.4   3781.3  12428.1 

Coefficients:
              Estimate Std. Error t value Pr(>|t|)    
(Intercept)  5.143e+04  3.828e+03  13.434  < 2e-16 ***
mileage     -2.331e-01  7.096e-02  -3.285  0.00142 ** 
accident    -9.825e+03  1.363e+03  -7.208 1.24e-10 ***
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 6536 on 97 degrees of freedom
Multiple R-squared:  0.3634,	Adjusted R-squared:  0.3503 
F-statistic: 27.69 on 2 and 97 DF,  p-value: 3.07e-10

```


e. For this new set of regressions, compare the estimated coefficient 
for ```ACCIDENT``` with and without the damage variable. 
How does this relate to the new coefficient for ```DAMAGE```?

```
Identical to the first regression, having damage at 0 but included in the 
regression still pushes the accident coefficient further from correlation. 
Damage in this regression is not correlating the variables any further.
```


f. Compare the values of 
```Multiple R-squared``` and ```Adjusted R-squared``` for the two models. 
Now which model do you recommend (pretending that you don't know the true model)? 

```
In the absense of 0 damage entirely, the adjusted r squared is identical to the
first regression even in the absense of the coefficient all together. The first
regression has a adjusted r squared is 0.7611, which should be the preferred
model over the second with an adjusted r squared of 0.3505. 

Though damage or the amount of damage should be important to the price of car, the
added variable is not necessary for the regression, it simply helps the significance
of other variables included in the regression. 
```

