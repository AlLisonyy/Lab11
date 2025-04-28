Lab 11 - Grading the professor, Pt. 2
================
Allison Li
04282025

## Load packages and data

``` r
library(tidyverse) 
library(tidymodels)
library(broom)
library(openintro)
```

## Exercise 1

*Provide your answer here.*  
Add code chunks as needed. Ensure code chunks are properly labeled
without spaces.

``` r
m_bty <- lm(
  score ~ bty_avg,
  data = evals
)
summary(m_bty)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.9246 -0.3690  0.1420  0.3977  0.9309 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.88034    0.07614   50.96  < 2e-16 ***
    ## bty_avg      0.06664    0.01629    4.09 5.08e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5348 on 461 degrees of freedom
    ## Multiple R-squared:  0.03502,    Adjusted R-squared:  0.03293 
    ## F-statistic: 16.73 on 1 and 461 DF,  p-value: 5.083e-05

## Exercise 2

``` r
m_bty_gen <- lm(score ~ bty_avg + gender, data = evals)
summary(m_bty_gen)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg + gender, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8305 -0.3625  0.1055  0.4213  0.9314 
    ## 
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  3.74734    0.08466  44.266  < 2e-16 ***
    ## bty_avg      0.07416    0.01625   4.563 6.48e-06 ***
    ## gendermale   0.17239    0.05022   3.433 0.000652 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5287 on 460 degrees of freedom
    ## Multiple R-squared:  0.05912,    Adjusted R-squared:  0.05503 
    ## F-statistic: 14.45 on 2 and 460 DF,  p-value: 8.177e-07

## Exercise 3

The intercept represents the predicted professor course evaluation score
when the average beauty rating is 0 and when the professor is female.
The bty_avg slope indicates that for one point increase in average
beauty rating, the professor course evaluation score will increase by
about 0.074 points, when gender is hold constant. The gender slope
indicates that a male professor is predicted to have a 0.172 point
higher evaluation score than a female professor on average, when holding
beauty score as constant.

## Exercise 4

According to the output table, the R-squared value is .06. Therefore,
About 6% of the variability in professors’ evaluation scores can be
explained by the model m_bty_gen.

## Exercise 5

The line for male: score = $\hat{\text{Score}}_i$

## Additional Exercises

*Repeat the format above for additional exercises.*
