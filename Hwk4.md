Homework 4
================

#### How important is a college degree in determining an individual’s wages?

A question that is even more relevant in the current economic climate
than usual, it is one that seems particularly susceptible to the impact
of external variables. Quality of tertiary institution, financial
standing of family during one’s upbringing, relevance to actual career
path are potential confounding variables that immediately spring to
mind.

To approach the problem, the subset has been expanded to include people
in the workforce, between 25 and 70 (to account for the ever increasing
retirement age), working full time hours at least 48 weeks of the year.

The first regression looks at the correlation between income and age and
gender.

    ## 
    ## Call:
    ## lm(formula = INCWAGE ~ AGE + female)
    ## 
    ## Residuals:
    ##    Min     1Q Median     3Q    Max 
    ## -97275 -40016 -18510  12513 586940 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)  56373.20    1395.05   40.41   <2e-16 ***
    ## AGE            584.31      28.92   20.20   <2e-16 ***
    ## female      -19921.41     689.65  -28.89   <2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 85420 on 61942 degrees of freedom
    ## Multiple R-squared:  0.01984,    Adjusted R-squared:  0.01981 
    ## F-statistic: 626.9 on 2 and 61942 DF,  p-value: < 2.2e-16

![](Hwk4_files/figure-gfm/unnamed-chunk-1-1.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-1-2.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-1-3.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-1-4.png)<!-- -->

    ## 
    ## ===============================================
    ##                         Dependent variable:    
    ##                     ---------------------------
    ##                               INCWAGE          
    ## -----------------------------------------------
    ## AGE                         584.309***         
    ##                              (28.922)          
    ##                                                
    ## female                    -19,921.420***       
    ##                              (689.651)         
    ##                                                
    ## Constant                   56,373.200***       
    ##                             (1,395.051)        
    ##                                                
    ## -----------------------------------------------
    ## Observations                  61,945           
    ## R2                             0.020           
    ## Adjusted R2                    0.020           
    ## Residual Std. Error   85,415.510 (df = 61942)  
    ## F Statistic         626.851*** (df = 2; 61942) 
    ## ===============================================
    ## Note:               *p<0.1; **p<0.05; ***p<0.01

![](Hwk4_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->
![](Hwk4_files/figure-gfm/unnamed-chunk-4-1.png)<!-- --> From the
