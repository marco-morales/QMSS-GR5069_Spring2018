Interactions and interactive effects
================

From our long running sample dataset, we are seeking to answer two different questions:

1.  **are there more expected deaths when combat is heavier?**
2.  **are there no expected deaths when no weapons are seized?**

We start by computing your full interactive model, including **all terms** that constitute the **interactions**. In this case, we're interested in evaluating the effects of long guns and cartridges on confrontations where each armed force participated.

Note that as long as you include the interactions, R will automatically include the constitutive terms.

``` r
ols_interaction <-
  lm(organized_crime_dead ~ organized_crime_wounded +
       afi*long_guns_seized + 
       army*long_guns_seized + 
       navy*long_guns_seized + 
       federal_police*long_guns_seized +
       afi*cartridge_sezied + 
       army*cartridge_sezied + 
       navy*cartridge_sezied + 
       federal_police*cartridge_sezied +
       small_arms_seized + 
       clips_seized , 
     data = AllData) 
summary(ols_interaction) 
```

    ## 
    ## Call:
    ## lm(formula = organized_crime_dead ~ organized_crime_wounded + 
    ##     afi * long_guns_seized + army * long_guns_seized + navy * 
    ##     long_guns_seized + federal_police * long_guns_seized + afi * 
    ##     cartridge_sezied + army * cartridge_sezied + navy * cartridge_sezied + 
    ##     federal_police * cartridge_sezied + small_arms_seized + clips_seized, 
    ##     data = AllData)
    ## 
    ## Residuals:
    ##     Min      1Q  Median      3Q     Max 
    ## -9.2025 -0.7395 -0.4189  0.1807 27.2183 
    ## 
    ## Coefficients:
    ##                                   Estimate Std. Error t value Pr(>|t|)    
    ## (Intercept)                      4.189e-01  3.366e-02  12.448  < 2e-16 ***
    ## organized_crime_wounded          3.628e-01  2.376e-02  15.267  < 2e-16 ***
    ## afi                             -3.854e-02  5.037e-01  -0.077 0.939015    
    ## long_guns_seized                 1.694e-01  1.724e-02   9.830  < 2e-16 ***
    ## army                             4.180e-01  5.564e-02   7.511 6.83e-14 ***
    ## navy                             2.838e-01  1.567e-01   1.811 0.070146 .  
    ## federal_police                  -1.122e-01  8.013e-02  -1.400 0.161470    
    ## cartridge_sezied                 2.115e-04  9.694e-05   2.182 0.029189 *  
    ## small_arms_seized               -4.687e-02  1.860e-02  -2.520 0.011752 *  
    ## clips_seized                     1.221e-03  4.472e-04   2.730 0.006362 ** 
    ## afi:long_guns_seized             2.354e-02  7.835e-02   0.300 0.763890    
    ## long_guns_seized:army           -4.657e-02  1.813e-02  -2.569 0.010232 *  
    ## long_guns_seized:navy            1.735e-01  4.216e-02   4.115 3.93e-05 ***
    ## long_guns_seized:federal_police -2.379e-02  1.905e-02  -1.249 0.211684    
    ## afi:cartridge_sezied            -5.047e-03  3.121e-03  -1.617 0.105945    
    ## army:cartridge_sezied           -3.809e-04  9.810e-05  -3.882 0.000105 ***
    ## navy:cartridge_sezied           -6.903e-04  1.727e-04  -3.997 6.49e-05 ***
    ## federal_police:cartridge_sezied -1.497e-04  1.102e-04  -1.358 0.174415    
    ## ---
    ## Signif. codes:  0 '***' 0.001 '**' 0.01 '*' 0.05 '.' 0.1 ' ' 1
    ## 
    ## Residual standard error: 1.713 on 5377 degrees of freedom
    ##   (1 observation deleted due to missingness)
    ## Multiple R-squared:   0.16,  Adjusted R-squared:  0.1573 
    ## F-statistic: 60.23 on 17 and 5377 DF,  p-value: < 2.2e-16

### How do we compute interactive effects?

Looking at the coefficients of the interaction - such as `long_guns_seized:federal_police` is not sufficient to get the estimated interactive effects. You need to include all constitutive terms for the particular effect you seek to estimate.

To do that, first, we need to extract the vector with the estimated coefficients from the model, as well as the the corresponding stantard errors from the estimated covariance matrix.

``` r
beta <- coef(ols_interaction)                # extracts a vector of betas
varcov <- as.matrix(vcov(ols_interaction))   # extracts estimated covariance matrix
var <- diag(vcov(ols_interaction))           # extracts a vector with variances
```

``` r
beta
```

    ##                     (Intercept)         organized_crime_wounded 
    ##                    0.4189268109                    0.3628101488 
    ##                             afi                long_guns_seized 
    ##                   -0.0385406129                    0.1694121549 
    ##                            army                            navy 
    ##                    0.4179517384                    0.2837890749 
    ##                  federal_police                cartridge_sezied 
    ##                   -0.1122026584                    0.0002114655 
    ##               small_arms_seized                    clips_seized 
    ##                   -0.0468722324                    0.0012207446 
    ##            afi:long_guns_seized           long_guns_seized:army 
    ##                    0.0235362609                   -0.0465711583 
    ##           long_guns_seized:navy long_guns_seized:federal_police 
    ##                    0.1734778193                   -0.0237947688 
    ##            afi:cartridge_sezied           army:cartridge_sezied 
    ##                   -0.0050465643                   -0.0003808827 
    ##           navy:cartridge_sezied federal_police:cartridge_sezied 
    ##                   -0.0006903354                   -0.0001496627

``` r
var
```

    ##                     (Intercept)         organized_crime_wounded 
    ##                    1.132679e-03                    5.647411e-04 
    ##                             afi                long_guns_seized 
    ##                    2.537341e-01                    2.970470e-04 
    ##                            army                            navy 
    ##                    3.096353e-03                    2.454697e-02 
    ##                  federal_police                cartridge_sezied 
    ##                    6.420084e-03                    9.396511e-09 
    ##               small_arms_seized                    clips_seized 
    ##                    3.458590e-04                    2.000092e-07 
    ##            afi:long_guns_seized           long_guns_seized:army 
    ##                    6.138997e-03                    3.286794e-04 
    ##           long_guns_seized:navy long_guns_seized:federal_police 
    ##                    1.777494e-03                    3.628867e-04 
    ##            afi:cartridge_sezied           army:cartridge_sezied 
    ##                    9.740755e-06                    9.624213e-09 
    ##           navy:cartridge_sezied federal_police:cartridge_sezied 
    ##                    2.982664e-08                    1.213990e-08

### Are there more expected deaths when combat is heavier?

To address the first question, we have to assume that a high number of long guns seized is a proxy for heavy combat. That is, we need to assume that it is more likely that more long guns are **used and seized** when heavy combat takes place. Therefore, we'll compute the marginal effect of 5 seized long guns on the expected number of dead on events that involve the Navy.

We begin by defining an appropriate quantity for our conditioning variable `long_guns_seized`

``` r
long_guns <- 5 
```

Then, we use our known formula to compute the appropriate marginal effect:

``` r
mfx_1 <- as.numeric(beta["navy"]) + 
         as.numeric(beta["long_guns_seized:navy"])*long_guns
mfx_1
```

    ## [1] 1.151178

Similarly, we use our known formula to compute the appropriate standard errors, per the variance formula:

``` r
mfx_1_se <- sqrt(
            var["navy"] + 
            long_guns^2*var["long_guns_seized:navy"] +
            2*long_guns*varcov["navy", "long_guns_seized:navy"]
            )
mfx_1_se
```

    ##     navy 
    ## 0.210302

It is now easy to compute the lower and higher bounds of the marginal effect:

``` r
mfx_1_lo_se <- mfx_1 - 1.96* mfx_1_se  # computing a lower bound se
mfx_1_hi_se <- mfx_1 + 1.96* mfx_1_se  # computing the higher bound se

print(paste0(long_guns, " seized long guns increase the expected number of dead in events that involve the Navy by ",
             round(mfx_1, 2), " [", round(mfx_1_lo_se, 2), ", ", round(mfx_1_hi_se, 2), "]."
             ))
```

    ## [1] "5 seized long guns increase the expected number of dead in events that involve the Navy by 1.15 [0.74, 1.56]."

### Are there no expected deaths when no weapons are seized?

To address the second question, we repeat the exercise and compute the marginal effect on the expected number of dead of events that involve the Army when no long guns (zero) are seized. This value is now assigned to our conditioning variable `long_guns_seized`.

``` r
long_guns_null <- 0
```

Again, we use our known formula to compute the appropriate marginal effect. Note that the second term is effectively dropped as the value of `long_guns_seized` is zero (0).

``` r
mfx_2 <- as.numeric(beta["army"]) + 
  as.numeric(beta["long_guns_seized:army"])*long_guns_null
mfx_2
```

    ## [1] 0.4179517

We compute the appropriate standard errors, per the variance formula, with the same caveat as above:

``` r
mfx_2_se <- sqrt(
            var["army"] + 
            long_guns_null^2*var["long_guns_seized:army"] +
            2*long_guns_null*varcov["army", "long_guns_seized:army"]
            )
mfx_2_se
```

    ##       army 
    ## 0.05564488

We can now compute the lower and higher bounds of the marginal effect:

``` r
mfx_2_lo_se <- mfx_2 - 1.96* mfx_2_se  # computing a lower bound se
mfx_2_hi_se <- mfx_2 + 1.96* mfx_2_se  # computing the higher bound se

print(paste0(long_guns_null, " seized long guns produce an expected number of dead in events that involve the Army of ",
             round(mfx_2, 2), " [", round(mfx_2_lo_se, 2), ", ", round(mfx_2_hi_se, 2), "]."
             ))
```

    ## [1] "0 seized long guns produce an expected number of dead in events that involve the Army of 0.42 [0.31, 0.53]."
