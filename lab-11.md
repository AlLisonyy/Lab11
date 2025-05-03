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

The line for male: score = 3.747 + .172 + .074 x bty_avg

## Exercise 6

Male professor tends to have the higher course evaluation score when
they receive the same appearance rating

## Exercise 7

``` r
m_bty_gen <- lm(score ~ bty_avg * gender, data = evals)
summary(m_bty_gen)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg * gender, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8084 -0.3828  0.0903  0.4037  0.9211 
    ## 
    ## Coefficients:
    ##                    Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)         3.95006    0.11800  33.475   <2e-16 ***
    ## bty_avg             0.03064    0.02400   1.277   0.2024    
    ## gendermale         -0.18351    0.15349  -1.196   0.2325    
    ## bty_avg:gendermale  0.07962    0.03247   2.452   0.0146 *  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5258 on 459 degrees of freedom
    ## Multiple R-squared:  0.07129,    Adjusted R-squared:  0.06522 
    ## F-statistic: 11.74 on 3 and 459 DF,  p-value: 1.997e-07

By including the interaction effect between the two predictors:

Male professors: score = 3.95 - .18 x 1 + .03 x bty_avg + .08 x 1 x
bty_avg = 3.77 + .11 x bty_av

Female professors: score = 3.95 - .18 x 0 + .03 x bty_avg + .08 x 0 x
bty_avg = 3.95 + .03 x bty_avg

According to the functions, for male professor, one point increase in
beauty score will increase 3.88 points increase in overall course
evaluation scores. For female professors, one point increase in beauty
score will increase 3.98 points increase in overall course evaluation
scores.

## Exercise 8

The adjust R squared value for m_bty_gen_new (the one with interaction
effect) is .065, while for m_bty is .033. The R squared value is almost
twice larger after including gender as a predictor of the course
evaluation score. This indicates that the new model explains more
variability in evaluation scores, and that gender is a strong predictor
of evaluation scores beyond what beauty alone can explain.

## Exercise 9

The slopes of bty_avg for m_bty is .67; The slopes of bty_avg for
m_bty_gen_new is .31. Therefore, the slope value has decreased after
adding genedr as a predictor.

## Exercise 10

``` r
m_bty_rank <- lm(score ~ bty_avg * rank, data = evals)
summary(m_bty_rank)
```

    ## 
    ## Call:
    ## lm(formula = score ~ bty_avg * rank, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.8584 -0.3882  0.1211  0.4054  1.0062 
    ## 
    ## Coefficients:
    ##                          Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)               4.09811    0.14959  27.395   <2e-16 ***
    ## bty_avg                   0.04171    0.03138   1.329   0.1844    
    ## ranktenure track         -0.01885    0.23044  -0.082   0.9349    
    ## ranktenured              -0.40910    0.18218  -2.246   0.0252 *  
    ## bty_avg:ranktenure track -0.02640    0.04632  -0.570   0.5690    
    ## bty_avg:ranktenured       0.06586    0.03922   1.679   0.0938 .  
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.5305 on 457 degrees of freedom
    ## Multiple R-squared:  0.05871,    Adjusted R-squared:  0.04841 
    ## F-statistic: 5.701 on 5 and 457 DF,  p-value: 4.089e-05

The intercept represents the predicted professor course evaluation score
when the average beauty rating is 0 and when the professor is not on
tenure track. The bty_avg slope indicates that for one point increase in
average beauty rating, the professor course evaluation score will
increase by about 0.042 points, when the professor’s rank is hold
constant. The rank tenure track slope indicates that professors on
tenure track has a 0.172 point lower evaluation score than a professor
not on tenure track on average, when holding beauty score as constant.
The rank tenured slope suggests that tenured professors has a .41 point
lower evaluation rating than a professor not on a tenured tract, when
holding beauty score constant. ty_avg:ranktenure track slope suggests
that for professors on the tenure track, the relationship between beauty
and evaluation score is 0.03 point lower compared to non-tenure track
professors. The bty_avg:ranktenured slope suggests that for tenured
professors, the relationship between beauty and evaluation score is 0.07
point higher compared to non-tenure track professors.

# Part 3

## Exercise 11

I think cls_perc_eval would be the worst predictor of evaluation scores.
Because I do not think it is related with how students will individually
evaluate the class or the professor.

## Exercise 12

``` r
cls_perc <- lm(score ~ cls_perc_eval, data = evals)
summary(cls_perc)
```

    ## 
    ## Call:
    ## lm(formula = score ~ cls_perc_eval, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.9283 -0.3533  0.1069  0.4026  1.0322 
    ## 
    ## Coefficients:
    ##               Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   3.727419   0.113327  32.891  < 2e-16 ***
    ## cls_perc_eval 0.006010   0.001486   4.046 6.12e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.535 on 461 degrees of freedom
    ## Multiple R-squared:  0.03429,    Adjusted R-squared:  0.03219 
    ## F-statistic: 16.37 on 1 and 461 DF,  p-value: 6.117e-05

According to the output, cls_perc_eval is a statistically significant
predictor of course evaluation rating. This is unexpected and a little
confusing but also potentially make sense??

## Exercise 13

I think I should not include cls_did_eval because it shows the number of
students in class who has completed evaluation, which is the calculation
of the two variables that planned to be included.

## Exercise 14

``` r
everything <- lm(score ~ rank + ethnicity + gender + language + age + cls_perc_eval + cls_students + cls_level + cls_profs + cls_credits + bty_avg, data = evals)
summary(everything)
```

    ## 
    ## Call:
    ## lm(formula = score ~ rank + ethnicity + gender + language + age + 
    ##     cls_perc_eval + cls_students + cls_level + cls_profs + cls_credits + 
    ##     bty_avg, data = evals)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -1.84482 -0.31367  0.08559  0.35732  1.10105 
    ## 
    ## Coefficients:
    ##                         Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            3.5305036  0.2408200  14.660  < 2e-16 ***
    ## ranktenure track      -0.1070121  0.0820250  -1.305 0.192687    
    ## ranktenured           -0.0450371  0.0652185  -0.691 0.490199    
    ## ethnicitynot minority  0.1869649  0.0775329   2.411 0.016290 *  
    ## gendermale             0.1786166  0.0515346   3.466 0.000579 ***
    ## languagenon-english   -0.1268254  0.1080358  -1.174 0.241048    
    ## age                   -0.0066498  0.0030830  -2.157 0.031542 *  
    ## cls_perc_eval          0.0056996  0.0015514   3.674 0.000268 ***
    ## cls_students           0.0004455  0.0003585   1.243 0.214596    
    ## cls_levelupper         0.0187105  0.0555833   0.337 0.736560    
    ## cls_profssingle       -0.0085751  0.0513527  -0.167 0.867458    
    ## cls_creditsone credit  0.5087427  0.1170130   4.348  1.7e-05 ***
    ## bty_avg                0.0612651  0.0166755   3.674 0.000268 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.504 on 450 degrees of freedom
    ## Multiple R-squared:  0.1635, Adjusted R-squared:  0.1412 
    ## F-statistic: 7.331 on 12 and 450 DF,  p-value: 2.406e-12

## Exercise 15

``` r
backward_model <- stats::step(object = everything, direction = "backward", trace = 1)
```

    ## Start:  AIC=-621.66
    ## score ~ rank + ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_students + cls_level + cls_profs + cls_credits + bty_avg
    ## 
    ##                 Df Sum of Sq    RSS     AIC
    ## - rank           2    0.4325 114.74 -623.91
    ## - cls_profs      1    0.0071 114.31 -623.63
    ## - cls_level      1    0.0288 114.34 -623.54
    ## - language       1    0.3501 114.66 -622.24
    ## - cls_students   1    0.3923 114.70 -622.07
    ## <none>                       114.31 -621.66
    ## - age            1    1.1818 115.49 -618.90
    ## - ethnicity      1    1.4771 115.78 -617.71
    ## - gender         1    3.0515 117.36 -611.46
    ## - cls_perc_eval  1    3.4284 117.74 -609.98
    ## - bty_avg        1    3.4287 117.74 -609.97
    ## - cls_credits    1    4.8017 119.11 -604.61
    ## 
    ## Step:  AIC=-623.91
    ## score ~ ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_students + cls_level + cls_profs + cls_credits + bty_avg
    ## 
    ##                 Df Sum of Sq    RSS     AIC
    ## - cls_profs      1    0.0103 114.75 -625.87
    ## - cls_level      1    0.0173 114.76 -625.84
    ## - cls_students   1    0.3645 115.11 -624.44
    ## <none>                       114.74 -623.91
    ## - language       1    0.5568 115.30 -623.67
    ## - age            1    0.8918 115.63 -622.32
    ## - ethnicity      1    1.7046 116.44 -619.08
    ## - gender         1    3.1469 117.89 -613.38
    ## - cls_perc_eval  1    3.5245 118.27 -611.90
    ## - bty_avg        1    3.5642 118.31 -611.75
    ## - cls_credits    1    5.6754 120.42 -603.56
    ## 
    ## Step:  AIC=-625.87
    ## score ~ ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_students + cls_level + cls_credits + bty_avg
    ## 
    ##                 Df Sum of Sq    RSS     AIC
    ## - cls_level      1    0.0162 114.77 -627.80
    ## - cls_students   1    0.3731 115.12 -626.36
    ## <none>                       114.75 -625.87
    ## - language       1    0.5552 115.31 -625.63
    ## - age            1    0.8964 115.65 -624.27
    ## - ethnicity      1    1.8229 116.57 -620.57
    ## - gender         1    3.1375 117.89 -615.38
    ## - cls_perc_eval  1    3.5166 118.27 -613.89
    ## - bty_avg        1    3.5547 118.31 -613.74
    ## - cls_credits    1    5.8278 120.58 -604.93
    ## 
    ## Step:  AIC=-627.8
    ## score ~ ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_students + cls_credits + bty_avg
    ## 
    ##                 Df Sum of Sq    RSS     AIC
    ## - cls_students   1    0.3569 115.12 -628.36
    ## <none>                       114.77 -627.80
    ## - language       1    0.5390 115.31 -627.63
    ## - age            1    0.8828 115.65 -626.25
    ## - ethnicity      1    1.8948 116.66 -622.22
    ## - gender         1    3.1222 117.89 -617.37
    ## - cls_perc_eval  1    3.5266 118.29 -615.79
    ## - bty_avg        1    3.5461 118.31 -615.71
    ## - cls_credits    1    6.2703 121.04 -605.17
    ## 
    ## Step:  AIC=-628.36
    ## score ~ ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_credits + bty_avg
    ## 
    ##                 Df Sum of Sq    RSS     AIC
    ## <none>                       115.12 -628.36
    ## - language       1    0.6192 115.74 -627.88
    ## - age            1    0.9342 116.06 -626.62
    ## - ethnicity      1    1.8997 117.02 -622.79
    ## - cls_perc_eval  1    3.1769 118.30 -617.76
    ## - gender         1    3.4709 118.59 -616.61
    ## - bty_avg        1    4.0096 119.13 -614.51
    ## - cls_credits    1    6.1046 121.23 -606.44

``` r
summary(backward_model)
```

    ## 
    ## Call:
    ## lm(formula = score ~ ethnicity + gender + language + age + cls_perc_eval + 
    ##     cls_credits + bty_avg, data = evals)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -1.9067 -0.3103  0.0849  0.3712  1.0611 
    ## 
    ## Coefficients:
    ##                        Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)            3.446967   0.203191  16.964  < 2e-16 ***
    ## ethnicitynot minority  0.204710   0.074710   2.740 0.006384 ** 
    ## gendermale             0.184780   0.049889   3.704 0.000238 ***
    ## languagenon-english   -0.161463   0.103213  -1.564 0.118427    
    ## age                   -0.005008   0.002606  -1.922 0.055289 .  
    ## cls_perc_eval          0.005094   0.001438   3.543 0.000436 ***
    ## cls_creditsone credit  0.515065   0.104860   4.912 1.26e-06 ***
    ## bty_avg                0.064996   0.016327   3.981 7.99e-05 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 0.503 on 455 degrees of freedom
    ## Multiple R-squared:  0.1576, Adjusted R-squared:  0.1446 
    ## F-statistic: 12.16 on 7 and 455 DF,  p-value: 2.879e-14

According to the output, it seems like that the best model would be:

score = 3.45 + .2 x ethnicity + .18 x gender - .16 x language - .01 x
age + .01 x cls_perc_eval + .52 x cls_credits + .065 x bty_avg

## Exercise 16

For ethnicity as predictor, while holding all other predictors constant,
professors who were not racial minorities were predicted to have .2
point higher course evaluation scores than minority professors on
average.

For age as predictor, while holding all other predictors constant, one
year older in age can predict .01 point lower course evaluation scores
on average.

## Exercise 17

based on the model, a higher evaluation score professor would be a white
male who has recevied education in english, who is relatively younger,
have higher percent of students in class who completed evaluation, and
is rated as more good looking.

## Exercise 18

I am not really comfortable with generalizing this conclusion at any
university. I think the results would depends on the students at
different institutions, even within certain department. I do not think
the sample is representative or generalizable to any universities.
Additionally, the R squared value suggests that all the predictors here
can only explain 15.8% of the variability in the scores, which was not a
lot?

In general, I really like this lab and found it interesting. I think all
the questions are instructions are clear, logical, engaging and helped
me to learn regression model better in R. I do not have much suggestion
or advice on this lab because I think it is a really good one! The only
suggestion is that we can try to add one question to ask the visual
representation? The question can be: Choose one or two predictors from
your model and create a scatterplot or boxplot to visualize their
relationship with evaluation score. What does the visual tell you that
complements (or contrasts with) the regression results?
