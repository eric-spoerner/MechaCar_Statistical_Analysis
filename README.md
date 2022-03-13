# MechaCar_Statistical_Analysis

## Tools used

* R
* RStudio
* tidyverse/dplyr

## The Data

* Two CSV files.  Details coming later.

## Linear Regression to Predict MPG

Using 50 prototype MechaCars, generate a linear model to predict impact on MPG of various factors:
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

Results of suspension coils from multiple production lots.  Testing the weight capacity as measured in PSI of each lot. Design specifications for the car dictate that the variance of the suspension coils must not exceed 100 PSI.  This data was tested both in total for all produced coils, as well as based on all three unique production lots.

### Total summary
```
     Mean Median Variance       SD
1 1498.78   1500 62.29356 7.892627
```
### Lot-based summary
```
# A tibble: 3 x 5
# Groups:   Lot [3]
  Lot    Mean Median Variance     SD
  <chr> <dbl>  <dbl>    <dbl>  <dbl>
1 Lot1  1500   1500     0.980  0.990
2 Lot2  1500.  1500     7.47   2.73 
3 Lot3  1496.  1498.  170.    13.0  
```

Based on the results of this analysis, we can accept the variance in aggregate for all produced coils (Variance: 62.29 PSI), driven largely by the consistency of lots 1 (0.98 PSI) and 2 (7.47 PSI).  Lot 3, with its variance of 170 PSI, should be rejected.

## T-Tests on Suspension Coils

With the same suspension coil data, analyze if all manufacturing lots in total as well as each unique lot are statistically different from the population mean of 1,500 PSI.

To do this we will be using a one-sample t-test for each sample, comparing the data against the population's μ<sub>0</sub> of 1,500.

The **total sample** of coils has a μ of 1498.78, with a p-value of 0.0028; therefore H<sub>0</sub> cannot be rejected.  The total set of statistically similar.
```	
t = -1.8931, df = 149, p-value = 0.06028
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1497.507 1500.053
sample estimates:
mean of x 
  1498.78 
```

**Lot 1** is *statistically identical* to the population, with a μ of 1500 and a p-value of exactly 1.
```
t = 0, df = 49, p-value = 1
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1499.719 1500.281
sample estimates:
mean of x 
     1500 
```

**Lot 2** has a μ of 1500.2, with a p-value of 0.6072; while there is a discrepancy between this sample and the population's data, the confidence is too low to reject H<sub>0</sub>.
```
t = 0.51745, df = 49, p-value = 0.6072
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1499.423 1500.977
sample estimates:
mean of x 
   1500.2 
```

**Lot 3** has a μ of 1496.14, with a p-value of 0.04168; we can reject H<sub>0</sub> in this case and assume that this lot is statistically dissimilar from the general population.
```
t = -2.0916, df = 49, p-value = 0.04168
alternative hypothesis: true mean is not equal to 1500
95 percent confidence interval:
 1492.431 1499.849
sample estimates:
mean of x 
  1496.14 
```