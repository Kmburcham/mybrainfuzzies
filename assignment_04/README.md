# Assignment 4

Complete the exercise described in the pdf above and enter your answers in 
the spaces below.

## Running the Script as Given

Run the entire script and observe the output from the simulation.
In particular, observe the statistics printed at the bottom.



a. Copy and paste the means and standard deviations from the output after the commands
```sapply(reg_results[, full_list_of_variables], mean)``` 
and ```sapply(reg_results[, full_list_of_variables], sd)```. 


```
 sapply(reg_results[, full_list_of_variables], mean)
    intercept       mileage      accident        damage 
 4.999521e+04 -2.006398e-01 -4.948432e+03 -2.024889e+04  


> sapply(reg_results[, full_list_of_variables], sd)
   intercept      mileage     accident       damage 
2.164870e+03 4.203082e-02 8.235211e+02 3.956179e+03   


```

b. For each parameter, calculate the distance between the mean estimate and the true value, in terms of the number of standard deviations of that variable. 
The true values of the coefficients are listed in lines 74 to 78 in the script ```OLS_on_repeat_A4.R```.


```
Intercept
((4.999521e+04 - 50000)/-2.024889e+04) = 0.0002365562

Mileage
(((-2.006398e-01 - (-.20))/4.203082e-02)) = -0.01522216

Accident
(((-4.948432e+03 - (-5000))/8.235211e+02)) = 0.06261892

Damage
(((-2.024889e+04 - (-20000))/3.956179e+03)) = -0.06291171

```


c. Now compare the average values of each of the estimated coefficients with their true values.
Are they biased or unbiased?
Keep in mind that with an unbiased estimator 
a difference of less than $2$ standard deviations could often happen by chance.


```

All measures are unbiased and within two standard deviations from the mean.


```



## Running the Script after Modification


d. Copy and paste the means and standard deviations from the output 
after the commands 
```sapply(reg_results[, full_list_of_variables], mean)```

and ```sapply(reg_results[, full_list_of_variables], sd)```.


```
sapply(reg_results[, full_list_of_variables], mean)
    intercept     mileage_1      accident        damage 
 4.557070e+04 -1.102589e-01 -4.870802e+03 -2.101164e+04 

sapply(reg_results[, full_list_of_variables], sd)
   intercept    mileage_1     accident       damage 
1.576422e+03 2.987379e-02 8.765239e+02 1.777106e+03 

```


e. For each parameter, calculate the distance between the mean estimate and the true value, in terms of the number of standard deviations of that variable. 


```

Intercept
((4.557070e+04 - 50000)/1.576422e+03) = -2.809717

Mileage
(((-1.102589e-01 - (-.20))/2.987379e-02))= 3.004008

Accident
(((-4.870802e+03 - (-5000))/8.765239e+02)) = 0.1473981

Damage
(((-2.101164e+04 - (-20000))/1.777106e+03)) = -0.5692626


```


f. Now compare the average values of each of the estimates 
with their true values when the true 
```mileage``` is unobserved 
but inaccurate ```mileage_1``` is observed instead.
Are they biased or unbiased?
Again, keep in mind that with an unbiased estimator 
a difference of less than $2$ standard deviations could often happen by chance. 


```

The top two are biased because they are not withtin two standard deviations of the mean.
The bottom two are not biased because they are within two standard deviations of the mean.


```

