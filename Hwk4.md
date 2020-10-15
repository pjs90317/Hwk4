Homework 4
================
Patrick Sinclair

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
I’ll run several linear regressions on the subset to determine whether
we can find a causal link between college degree and income, or whether
we just observe some sort of correlation.

The first regression looks at the relationship between income and age
and gender. I reduced the number of observations in the random uniform
distribution to 0.05 as the length of the data set is 61,945
observations. To demonstrate the range of incomes at each age more
clearly, the jitter of the plots has been reduced to 1 and the y-limit
has been increased to 250,000 for the same reason. When I tested higher
y-limits, the presentation lost clarity.

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
summary, we see that the intercept of wages is 56373.20. The Ordinary
Least Squares (OLS) coefficient for the age and gender variables is
584.31 and -19921.41 respectively. All three estimators are
statistically significant to the 95% level. This is confirmed when we
examine the t and p values for the estimators; the t-values for all
three betas are well above the absolute critical value (critical
t-value: 1.96) and the p-values are below 0.025; If we look at the
confidence intervals:

    ##                   2.5 %      97.5 %
    ## (Intercept)  53638.8985  59107.5039
    ## AGE            527.6217    640.9965
    ## female      -21273.1315 -18569.6978

We can be 95% confident that if there is in fact a relationship between
income, age and gender, then we would observe values for the estimators
within the boundaries above. All of the estimators we have observed sit
within those intervals, so we have evidence to suggest that the
correlations exist. Yet, when we take the R<sup>2</sup> into
consideration, it suggests that the model does not do very well at
predicting income based on the variables of age and gender. I think this
may be to do with the variables having opposite correlations with
income. I included the plot of the gender variable to illustrate the
conflicting regression lines between the two - I also adjusted the
jitter and opaqueness of the colors on the second graph to highlight the
higher density of large incomes received by men.

Now to compare levels of college education. I’m going to remove the
gender variable, in an attempt to show the impact of earning a degree on
income. Hopefully we see that degree holders earn a higher wage,
regardless of gender.

    ## The following object is masked from package:survival:
    ## 
    ##     veteran

    ## The following objects are masked from dat_use (pos = 10):
    ## 
    ##     AfAm, AGE, Amindian, ANCESTR1, ANCESTR1D, ANCESTR2, ANCESTR2D,
    ##     Asian, below_150poverty, below_200poverty, below_povertyline, BPL,
    ##     BPLD, BUILTYR2, CITIZEN, CLASSWKR, CLASSWKRD, Commute_bus,
    ##     Commute_car, Commute_other, Commute_rail, Commute_subway, COSTELEC,
    ##     COSTFUEL, COSTGAS, COSTWATR, DEGFIELD, DEGFIELD2, DEGFIELD2D,
    ##     DEGFIELDD, DEPARTS, EDUC, educ_advdeg, educ_college, educ_hs,
    ##     educ_nohs, educ_somecoll, EDUCD, EMPSTAT, EMPSTATD, FAMSIZE,
    ##     female, foodstamps, FOODSTMP, FTOTINC, FUELHEAT, GQ,
    ##     has_AnyHealthIns, has_PvtHealthIns, HCOVANY, HCOVPRIV, HHINCOME,
    ##     Hisp_Cuban, Hisp_DomR, Hisp_Mex, Hisp_PR, HISPAN, HISPAND,
    ##     Hispanic, in_Bronx, in_Brooklyn, in_Manhattan, in_Nassau, in_NYC,
    ##     in_Queens, in_StatenI, in_Westchester, INCTOT, INCWAGE, IND,
    ##     LABFORCE, LINGISOL, MARST, MIGCOUNTY1, MIGPLAC1, MIGPUMA1,
    ##     MIGRATE1, MIGRATE1D, MORTGAGE, NCHILD, NCHLT5, OCC, OWNCOST,
    ##     OWNERSHP, OWNERSHPD, POVERTY, PUMA, PWPUMA00, RACE, race_oth,
    ##     RACED, RELATE, RELATED, RENT, ROOMS, SCHOOL, SEX, SSMC, TRANTIME,
    ##     TRANWORK, UHRSWORK, UNITSSTR, unmarried, veteran, VETSTAT,
    ##     VETSTATD, white, WKSWORK2, YRSUSA1

    ## 
    ## Call:
    ## lm(formula = INCWAGE ~ AGE + educ_nohs + educ_hs + educ_somecoll + 
    ##     educ_college + educ_advdeg)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -139520  -34236  -12350   11330  611330 
    ## 
    ## Coefficients: (1 not defined because of singularities)
    ##                Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)    80677.28    1443.19   55.90   <2e-16 ***
    ## AGE              840.61      27.75   30.30   <2e-16 ***
    ## educ_nohs     -85109.74    1647.70  -51.65   <2e-16 ***
    ## educ_hs       -72879.58     952.35  -76.53   <2e-16 ***
    ## educ_somecoll -62905.54    1009.73  -62.30   <2e-16 ***
    ## educ_college  -28637.00     963.59  -29.72   <2e-16 ***
    ## educ_advdeg          NA         NA      NA       NA    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 80990 on 61939 degrees of freedom
    ## Multiple R-squared:  0.1188, Adjusted R-squared:  0.1187 
    ## F-statistic:  1670 on 5 and 61939 DF,  p-value: < 2.2e-16

![](Hwk4_files/figure-gfm/unnamed-chunk-6-1.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-6-2.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-6-3.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-6-4.png)<!-- -->

    ## 
    ## ================================================
    ##                         Dependent variable:     
    ##                     ----------------------------
    ##                               INCWAGE           
    ## ------------------------------------------------
    ## AGE                          840.608***         
    ##                               (27.746)          
    ##                                                 
    ## educ_nohs                  -85,109.740***       
    ##                             (1,647.698)         
    ##                                                 
    ## educ_hs                    -72,879.580***       
    ##                              (952.348)          
    ##                                                 
    ## educ_somecoll              -62,905.540***       
    ##                             (1,009.726)         
    ##                                                 
    ## educ_college               -28,637.000***       
    ##                              (963.586)          
    ##                                                 
    ## educ_advdeg                                     
    ##                                                 
    ##                                                 
    ## Constant                   80,677.280***        
    ##                             (1,443.191)         
    ##                                                 
    ## ------------------------------------------------
    ## Observations                   61,945           
    ## R2                             0.119            
    ## Adjusted R2                    0.119            
    ## Residual Std. Error   80,992.050 (df = 61939)   
    ## F Statistic         1,669.641*** (df = 5; 61939)
    ## ================================================
    ## Note:                *p<0.1; **p<0.05; ***p<0.01

    ## Warning in predict.lm(age_degree, newdata = predicteddeg): prediction from a
    ## rank-deficient fit may be misleading

![](Hwk4_files/figure-gfm/unnamed-chunk-8-1.png)<!-- --> In the above
regression, education levels have been included as individual dummy
variables - R did not include Advance Degree as a variable. All of the
slope coefficient estimates for education levels are negative however,
as educational attainment increases, the slope coefficients become less
negative. This suggests that as one’s level of education increases, they
potentially earn higher income.

To double check this, I ran another regression, this time creating a
factor to include the educational levels. On this occasion, R excluded
No High School as a variable.

    ## The following object is masked from package:survival:
    ## 
    ##     veteran

    ## The following objects are masked from dat_use (pos = 10):
    ## 
    ##     AfAm, AGE, Amindian, ANCESTR1, ANCESTR1D, ANCESTR2, ANCESTR2D,
    ##     Asian, below_150poverty, below_200poverty, below_povertyline, BPL,
    ##     BPLD, BUILTYR2, CITIZEN, CLASSWKR, CLASSWKRD, Commute_bus,
    ##     Commute_car, Commute_other, Commute_rail, Commute_subway, COSTELEC,
    ##     COSTFUEL, COSTGAS, COSTWATR, DEGFIELD, DEGFIELD2, DEGFIELD2D,
    ##     DEGFIELDD, DEPARTS, EDUC, educ_advdeg, educ_college, educ_hs,
    ##     educ_nohs, educ_somecoll, EDUCD, EMPSTAT, EMPSTATD, FAMSIZE,
    ##     female, foodstamps, FOODSTMP, FTOTINC, FUELHEAT, GQ,
    ##     has_AnyHealthIns, has_PvtHealthIns, HCOVANY, HCOVPRIV, HHINCOME,
    ##     Hisp_Cuban, Hisp_DomR, Hisp_Mex, Hisp_PR, HISPAN, HISPAND,
    ##     Hispanic, in_Bronx, in_Brooklyn, in_Manhattan, in_Nassau, in_NYC,
    ##     in_Queens, in_StatenI, in_Westchester, INCTOT, INCWAGE, IND,
    ##     LABFORCE, LINGISOL, MARST, MIGCOUNTY1, MIGPLAC1, MIGPUMA1,
    ##     MIGRATE1, MIGRATE1D, MORTGAGE, NCHILD, NCHLT5, OCC, OWNCOST,
    ##     OWNERSHP, OWNERSHPD, POVERTY, PUMA, PWPUMA00, RACE, race_oth,
    ##     RACED, RELATE, RELATED, RENT, ROOMS, SCHOOL, SEX, SSMC, TRANTIME,
    ##     TRANWORK, UHRSWORK, UNITSSTR, unmarried, veteran, VETSTAT,
    ##     VETSTATD, white, WKSWORK2, YRSUSA1

    ## 
    ## Call:
    ## lm(formula = INCWAGE ~ AGE + educ_indx)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -139520  -34236  -12350   11330  611330 
    ## 
    ## Coefficients:
    ##                 Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)     -4432.46    1971.15  -2.249   0.0245 *  
    ## AGE               840.61      27.75  30.296  < 2e-16 ***
    ## educ_indxHS     12230.16    1606.03   7.615 2.67e-14 ***
    ## educ_indxSmColl 22204.20    1642.23  13.521  < 2e-16 ***
    ## educ_indxBach   56472.74    1616.80  34.929  < 2e-16 ***
    ## educ_indxAdv    85109.74    1647.70  51.654  < 2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 80990 on 61939 degrees of freedom
    ## Multiple R-squared:  0.1188, Adjusted R-squared:  0.1187 
    ## F-statistic:  1670 on 5 and 61939 DF,  p-value: < 2.2e-16

![](Hwk4_files/figure-gfm/unnamed-chunk-9-1.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-9-2.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-9-3.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-9-4.png)<!-- -->

    ## 
    ## ================================================
    ##                         Dependent variable:     
    ##                     ----------------------------
    ##                               INCWAGE           
    ## ------------------------------------------------
    ## AGE                          840.608***         
    ##                               (27.746)          
    ##                                                 
    ## educ_indxHS                12,230.160***        
    ##                             (1,606.032)         
    ##                                                 
    ## educ_indxSmColl            22,204.200***        
    ##                             (1,642.235)         
    ##                                                 
    ## educ_indxBach              56,472.740***        
    ##                             (1,616.799)         
    ##                                                 
    ## educ_indxAdv               85,109.740***        
    ##                             (1,647.698)         
    ##                                                 
    ## Constant                    -4,432.460**        
    ##                             (1,971.150)         
    ##                                                 
    ## ------------------------------------------------
    ## Observations                   61,945           
    ## R2                             0.119            
    ## Adjusted R2                    0.119            
    ## Residual Std. Error   80,992.050 (df = 61939)   
    ## F Statistic         1,669.641*** (df = 5; 61939)
    ## ================================================
    ## Note:                *p<0.1; **p<0.05; ***p<0.01

![](Hwk4_files/figure-gfm/unnamed-chunk-10-1.png)<!-- --> All slope
coefficients were estimated as positive, all with t-values and p-values
that confirm statistical significance. Again referring to the confidence
intervals:

    ##                      2.5 %     97.5 %
    ## (Intercept)     -8295.9183  -569.0013
    ## AGE               786.2256   894.9909
    ## educ_indxHS      9082.3299 15377.9814
    ## educ_indxSmColl 18985.4178 25422.9856
    ## educ_indxBach   53303.8061 59641.6664
    ## educ_indxAdv    81880.2469 88339.2323

None of the intervals contain 0 as a value, so we can be 95% confident
that there is evidence to reject the H<sub>0</sub> of no relationship.
Again, all of the absolute t-values exceed the critical value of 1.96,
the closest being the intercept, which at an absolute value of 2.249
still exceeds the required value to deem it statistically significant.

Up to this point, we have assumed that the variables are homoskedastic.
That is, the variance in the errors in the observed values of the
dependent variable remain constant. It is reasonable to assume that due
to other influences such as career choices, location and other lifestyle
factors, the variance of errors in income will not remain constant as
our independent variables change. For instance, whether a young academic
takes a role in a tertiary institution or trades the books for a
corporate role, the difference in income may not be as drastic as a PhD
holder who trades their academic position for a high end role in a
banking or technology firm. In this case, the variables are
heteroskedastic. If we adjust for heteroskedasticity, we observe the
following:

    ## 
    ## t test of coefficients:
    ## 
    ##               Estimate Std. Error t value  Pr(>|t|)    
    ## (Intercept)  56373.201   1182.709  47.664 < 2.2e-16 ***
    ## AGE            584.309     26.528  22.026 < 2.2e-16 ***
    ## female      -19921.415    661.420 -30.119 < 2.2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

    ## 
    ## t test of coefficients:
    ## 
    ##                  Estimate Std. Error t value  Pr(>|t|)    
    ## (Intercept)     -4432.460   1447.636 -3.0619  0.002201 ** 
    ## AGE               840.608     26.379 31.8662 < 2.2e-16 ***
    ## educ_indxHS     12230.156    856.811 14.2740 < 2.2e-16 ***
    ## educ_indxSmColl 22204.202    898.104 24.7234 < 2.2e-16 ***
    ## educ_indxBach   56472.736   1077.609 52.4056 < 2.2e-16 ***
    ## educ_indxAdv    85109.740   1375.636 61.8694 < 2.2e-16 ***
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1

Comparing these to our initial values, we notice that our coefficient
estimates have remained the same. However, for the first regression run,
the standard error (se) increased for the intercept and age
coefficients, the t-values both increased and the p-values decreased.
For the female (gender) coefficient, the se decreased, as did the
t-value and p-value (this is due to the slope being negative, so the t
and p-values were already situated in the left tail). The confidence
interval would remain the same, as our estimator is consistent but the
values have even less probability of falling within the 95% interval.

Up to now, we’ve looked at overall changes in the raw data. If we take a
log of the y variable, we can look at percentage change of the dependent
variable in response to changes in the independent variables.

    ## 
    ## Call:
    ## lm(formula = log(income) ~ AGE + female)
    ## 
    ## Residuals:
    ##      Min       1Q   Median       3Q      Max 
    ## -10.5378  -0.0887   0.3982   0.8764   2.9560 
    ## 
    ## Coefficients:
    ##              Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept) 10.592407   0.037770 280.447  < 2e-16 ***
    ## AGE         -0.002605   0.000783  -3.326  0.00088 ***
    ## female       0.010488   0.018672   0.562  0.57432    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 2.313 on 61942 degrees of freedom
    ## Multiple R-squared:  0.0001843,  Adjusted R-squared:  0.000152 
    ## F-statistic: 5.708 on 2 and 61942 DF,  p-value: 0.00332

![](Hwk4_files/figure-gfm/unnamed-chunk-13-1.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-13-2.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-13-3.png)<!-- -->![](Hwk4_files/figure-gfm/unnamed-chunk-13-4.png)<!-- -->

    ## 
    ## ===============================================
    ##                         Dependent variable:    
    ##                     ---------------------------
    ##                             log(income)        
    ## -----------------------------------------------
    ## AGE                          -0.003***         
    ##                               (0.001)          
    ##                                                
    ## female                         0.010           
    ##                               (0.019)          
    ##                                                
    ## Constant                     10.592***         
    ##                               (0.038)          
    ##                                                
    ## -----------------------------------------------
    ## Observations                  61,945           
    ## R2                            0.0002           
    ## Adjusted R2                   0.0002           
    ## Residual Std. Error     2.313 (df = 61942)     
    ## F Statistic          5.708*** (df = 2; 61942)  
    ## ===============================================
    ## Note:               *p<0.1; **p<0.05; ***p<0.01

Now we are viewing a log-linear model. Comparing these coefficients to
our original coefficients, we can see they are much smaller. Converting
the Y into logarithms allows us to smooth the impact of outliers in the
data.

    ##  (Intercept)          AGE       female 
    ## 10.592407234 -0.002604686  0.010487952

    ## (Intercept)         AGE      female 
    ##  56373.2012    584.3091 -19921.4146

**Conclusions** Based on the two regression run in this homework, there
is evidence to suggest that age, education and gender do have an impact
on the level of wage that someone earns. While age and education both
have a positive correlation with income earned, being female has a
negative correlation with income earned. Whether we can make the leap to
suggest each of these variables alone CAUSES high or low income is
beyond the scope of this exercise. However, it would be remiss to ignore
the confounding variables and externalities that would contribute to
one’s income, on top of gender, age and level of education.

Other variables I would like to pursue are linguistic ability. This
could be particularly pertinent for highly educated immigrants who are
not fluent in English or work predominantly in communities that are have
low levels of English fluency. Including race or ancestry as a variable
would be another important path to pursue. One variable that crossed my
mind was family size - do people try to earn more to sustain larger
families? Do they have larger families because they earn more? Or do we
see the contrary?

Some restrictions that might be placed upon the data is to target degree
fields in conjunction with relevant career fields. Many college
graduates pursue roles in industry not directly related to their college
major - discerning whether entering career fields that differ from
studies has a positive, negative or neutral relationship on income is an
interesting question (especially as a BA in History graduate\!) Another
change I would impose is to change the catergorization of wages to
income total; this would capture more people pursuing multiple jobs -
for example those whose chosen degrees allow them to work freelance and
take second jobs.
