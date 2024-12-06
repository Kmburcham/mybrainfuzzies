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
                 formula = price ~ age + X0Sale_ID) 

summary(lm_model_1)

Call:
lm(formula = price ~ age + X0Sale_ID, data = airplane_sales)

Residuals:
   Min     1Q Median     3Q    Max 
-36273 -11306  -4024   8330 179397 

Coefficients:
            Estimate Std. Error t value Pr(>|t|)    
(Intercept) 22805.85   11142.46   2.047    0.042 *  
age         -2332.28     266.00  -8.768 9.68e-16 ***
X0Sale_ID     428.43      32.77  13.073  < 2e-16 ***
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

airplane_sales_specs <- merge(x = airplane_sales, y = airplane_specs)

# Verify that the data were joined correctly.
summary(airplane_sales_specs)

```


c) Calculate and copy the printed output from a ```summary``` of the data. 
Use this to get familiar with the contents of the dataset. 


```

X0Sale_ID        age            price           0Sale_ID        pass      
 Min.   :101   Min.   :13.00   Min.   :  9000   Min.   :101   Min.   :2.000  
 1st Qu.:149   1st Qu.:19.00   1st Qu.: 19000   1st Qu.:149   1st Qu.:4.000  
 Median :198   Median :22.00   Median : 33500   Median :198   Median :4.000  
 Mean   :198   Mean   :24.61   Mean   : 50237   Mean   :198   Mean   :4.287  
 3rd Qu.:247   3rd Qu.:30.00   3rd Qu.: 74000   3rd Qu.:247   3rd Qu.:6.000  
 Max.   :295   Max.   :44.00   Max.   :254000   Max.   :295   Max.   :6.000  
      wtop           fixgear           tdrag        
 Min.   :0.0000   Min.   :0.0000   Min.   :0.00000  
 1st Qu.:0.0000   1st Qu.:0.0000   1st Qu.:0.00000  
 Median :0.0000   Median :0.0000   Median :0.00000  
 Mean   :0.4615   Mean   :0.4513   Mean   :0.05641  
 3rd Qu.:1.0000   3rd Qu.:1.0000   3rd Qu.:0.00000  
 Max.   :1.0000   Max.   :1.0000   Max.   :1.00000  


```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```. 
Copy the printed estimation output from the ```summary``` command. 


```

Copy your results here.


```




### Question 3

a) Read in the ```airplane_perf.csv``` dataset and store it 
in a data frame called ```airplane_perf``` in your workspace. 


```

Enter the required code here.

```

b) Form a dataset ```airplane_full.csv``` 
by ```merge```ing all three datasets. 
Store the new dataset 
in a data frame called ```airplane_full``` in your workspace. 


```

Enter the required code here.

```

c) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```

Copy your results here.


```


d) Estimate a regression model to predict ```price``` as a function of 
```age```, ```pass```, ```wtop```, ```fixgear```, 
and ```tdrag```, 
as well as ```horse```, ```fuel```, ```ceiling```, and ```cruise```.
Copy the printed estimation output from the ```summary``` command. 


```

Copy your results here.


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

Enter the required code here.

```

b) Calculate and copy the printed output from a ```summary``` 
of the new variables. 
Use this to get familiar with the contents of the dataset. 


```

Copy your results here.


```


c) Estimate a regression model to predict ```log_price``` as a function of 
	```log_age```, ```pass```, ```wtop```, ```fixgear```, 
	and ```tdrag```, 
	as well as 
	```log_horse```, ```log_fuel```, ```log_ceiling```, 
	and ```log_cruise```. 
	Copy the printed estimation output from the ```summary``` command. 


```

Copy your results here.


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

Enter a description of your sequence of adjustments
to the regression model here.
Be sure to address the four specification criteria
described above.


```

Next regression model:

```

Copy your regression results here.


```

Next regression model, if necessary:

```

Copy your regression results here.


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

Copy your final regression results here.


```

f) Finally, for each of the variables in the datasets, 
	list those that are positively related to airplane prices,
	negatively related to airplane prices, 
	and statistically unrelated to airplane prices. 


```

Enter your response here.


```




## Part C: Version Control

### Question 5

Push your completed files to the ```final_exam``` folder 
in your private GitHub repository.