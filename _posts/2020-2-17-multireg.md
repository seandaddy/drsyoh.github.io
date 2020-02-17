Multiple Regression
================

## Analysis and Interpretation

Pair Plot

``` r
pairs(attitude)
```

![](https://seandaddy.github.io/images/attitude-1.png)<!-- -->

## Find the best model

``` r
out=lm(rating~., data=attitude)
out2=lm(rating~complaints+learning+advance, data=attitude)
out3=lm(rating~complaints+learning, data=attitude)
anova(out3, out2, out)
```

    ## Analysis of Variance Table
    ##
    ## Model 1: rating ~ complaints + learning
    ## Model 2: rating ~ complaints + learning + advance
    ## Model 3: rating ~ complaints + privileges + learning + raises + critical +
    ##     advance
    ##   Res.Df    RSS Df Sum of Sq      F Pr(>F)
    ## 1     27 1254.7                           
    ## 2     26 1179.1  1    75.540 1.5121 0.2312
    ## 3     23 1149.0  3    30.109 0.2009 0.8947

Attitude is the data from RStudio. We can get some valuable example to
find out the best model by following the step. Using ANOVA, anova(small
model, large model), we can compare each model through the F-stat.

``` r
summary(out3)
```

    ##
    ## Call:
    ## lm(formula = rating ~ complaints + learning, data = attitude)
    ##
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max
    ## -11.5568  -5.7331   0.6701   6.5341  10.3610
    ##
    ## Coefficients:
    ##             Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)   9.8709     7.0612   1.398    0.174    
    ## complaints    0.6435     0.1185   5.432 9.57e-06 ***
    ## learning      0.2112     0.1344   1.571    0.128    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ##
    ## Residual standard error: 6.817 on 27 degrees of freedom
    ## Multiple R-squared:  0.708,  Adjusted R-squared:  0.6864
    ## F-statistic: 32.74 on 2 and 27 DF,  p-value: 6.058e-08

In this example, the regression model 3, (rating=complaints+learning) is
the best among three models.
