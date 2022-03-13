# MechaCar_Statistical_Analysis

## Linear Regression to Predict MPG

What is the r-squared?
* Multiple: 0.7149
* Adjusted: 0.6825

What is p?
* p-value: 5.35e-11

Regression was conducted to determine the impact of the following factors on MPG:
* Vehicle Length
* Vehicle Weight
* Spoiler Angle
* Ground Clearance
* All-wheel Drive

Below are the results for this linear regression:

```
lm(formula = mpg ~ vehicle_length + vehicle_weight + spoiler_angle + 
    `ground_clearance + AWD, data = mpg)

Coefficients:
     (Intercept)    vehicle_length    vehicle_weight     spoiler_angle  ground_clearance               AWD  
      -1.040e+02         6.267e+00         1.245e-03         6.877e-02         3.546e+00        -3.411e+00
```

```
Coefficients:
                   Estimate Std. Error t value Pr(>|t|)    
(Intercept)      -1.040e+02  1.585e+01  -6.559 5.08e-08 ***
vehicle_length    6.267e+00  6.553e-01   9.563 2.60e-12 ***
vehicle_weight    1.245e-03  6.890e-04   1.807   0.0776 .  
spoiler_angle     6.877e-02  6.653e-02   1.034   0.3069    
ground_clearance  3.546e+00  5.412e-01   6.551 5.21e-08 ***
AWD              -3.411e+00  2.535e+00  -1.346   0.1852    
---
Signif. codes:  0 ‘***’ 0.001 ‘**’ 0.01 ‘*’ 0.05 ‘.’ 0.1 ‘ ’ 1

Residual standard error: 8.774 on 44 degrees of freedom
Multiple R-squared:  0.7149,	Adjusted R-squared:  0.6825 
F-statistic: 22.07 on 5 and 44 DF,  p-value: 5.35e-11
```

Vehicle length and ground clearance variables appear to have the most non-random amount of variance based on their minuscule p scores, and therefore the most direct impact on the car's MPG.  This is made clear by their coefficients in the linear regression model, which are **6.267** and **3.546**, respectively.

This linear regression model can be considered strongly predictive of MPG given the r-squared value of **0.7149**.  Along with a p-value of **5.35e-11**, which is effectively zero, we can confidently reject the null hypothesis that these data points are not predictive.

## Summary Statistics on Suspension Coils

write a short summary using screenshots from your total_summary and lot_summary dataframes, and address the following question:

Variance is 62.29 for aggregate set

1 - 0.980
2 - 7.47
3 - 170

The design specifications for the MechaCar suspension coils dictate that the variance of the suspension coils must not exceed 100 pounds per square inch. Does the current manufacturing data meet this design specification for all manufacturing lots in total and each lot individually? Why or why not?


## T-Tests on Suspension Coils

Null hypothesis cannot be rejected.  (PSI mean not different enough to match prior)

```	
One Sample t-test

data:  susp_coil$PSI
t = -1.8931, df = 149, p-value = 0.06028
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1497.507 1500.053
sample estimates:
mean of x 
  1498.78 
```
  
briefly summarize your interpretation and findings for the t-test results. Include screenshots of the t-test to support your summary.