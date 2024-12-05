
# Assignment 5


Continue the in-class exercise using the script 
```data_mining_A5.R``` in RStudio, 
which is a modified version of the script 
```data_mining_demo.R```.  
In this exercise, we generate simulated data for car prices, 
which depend on mileage, 
whether the car has been in an accident, 
and whether the car has sustained major structural damage, 
which can happen only as a result of an accident. 



Run the entire script and observe the output from the 
series of models.


		
a) Verify that damage occurs in both the samples. 
	Observe the output under the code blocks in lines 123-139
	to verify that the bottom right numbers 
	(the number of observations with accidents with damages) are not zero.
	If one of these bottom-right numbers is zero, run the script again. 
	
```


      0   1
  0 120   0
  1  66  14


```

		
b) Copy and paste the table of selected models and R-squared values, 
	under the command ```print(best_models)``` on line 315. 
	
```

1         1            damage    0.6540606     0.5927690
2         2          accident    0.7192817     0.6705927
3         3         mileage_2    0.7512055     0.7255170
4         4       rainfall_16    0.7563538     0.7193316
5         5        rainfall_1    0.7582207     0.7185279
6         6        rainfall_3    0.7605394     0.7229938
7         7       rainfall_19    0.7631756     0.7176937
8         8        rainfall_6    0.7648780     0.7217033
9         9        rainfall_2    0.7652574     0.7218462
10       10        rainfall_4    0.7655409     0.7178666
11       11       rainfall_20    0.7652175     0.7187272
12       12        rainfall_5    0.7641380     0.7149645
13       13         mileage_1    0.7626194     0.7194065
14       14       rainfall_12    0.7610721     0.7113630
15       15       rainfall_10    0.7591658     0.7145344
16       16        rainfall_8    0.7573122     0.7190220
17       17       rainfall_15    0.7552919     0.7169288
18       18       rainfall_13    0.7530070     0.7186321
19       19       rainfall_17    0.7505841     0.7173015
20       20       rainfall_11    0.7479741     0.7184810
21       21       rainfall_18    0.7453325     0.7190352
22       22        rainfall_7    0.7425663     0.7188212
23       23       rainfall_14    0.7396917     0.7187062
24       24        rainfall_9    0.7367427     0.7186349


```

		
c) Compare the models according to the in-sample ```R-bar-squared``` 
		under the column ```R2_in_sample```. 
		Which model is best under this criterion? 
		The variables in the model are listed in the column ```best_new_variable```
		up to the row of the chosen model. 

```

In the in-sample set, the best data set is line 10 rainfall_4    0.7655409 because 
it has the highest r squared. It contains the 9 variables above the line.

The best model with 10 variables is "
[1] "car_price ~  damage + accident + mileage_2 + rainfall_16 + rainfall_1 + rainfall_3 + rainfall_19 + rainfall_6 + rainfall_2 + rainfall_4"
[1] "with an R-squared of 0.765541.
```
		
d) Compare the models according to the out-of-sample ```R-bar-squared``` 
		under the column ```R2_out_sample```. 
		Which model is best under this criterion? 
		The variables in the model are listed in the column ```best_new_variable```
		up to the row of the chosen model. 

```

In the out-sample data set, line 6  rainfall_3 0.7229938 is the best model. 
It contains the line and the 5 variables above line 6. 

[1]car_price ~ damage + accident + mileage_2 + rainfall_16 + rainfall_1 + 
[1]    rainfall_3 "with an R-squared of 0.7229939.


```
		
e) Compare the differences between the two models.
		Do any variables appear in one model and not the other?
		Which model do you recommend on the basis of this data? 
		Is your recommended model the same as the true model? 



```
These variables would not be present in the out-sampling data regression model compared to the
in-sampling data set. 

7         7        rainfall_19   0.7631756     0.7176937
8         8        rainfall_6    0.7648780     0.7217033
9         9        rainfall_2    0.7652574     0.7218462
10       10        rainfall_4    0.7655409     0.7178666

These variables would not be present in the out-sample model. This is the difference in 
variables between in and out sample. This would suggest that more sourced variables
are able to be included and fit the model. When out-data is applied to this model, less variables
become significant in terms of high adjusted r squared. Per my chart, I would suggest using the 
out-sample data set because the adjusted r squared for the variables is not that much less significant
than in-sample data. Damage, accident, and mileage are more indicators of which variables is a better
fit, even though they are not that much different. I would recommend using the in-sample data if there was
more variation in the out-sampling r-squared as the regression model would not be as strong.


```
