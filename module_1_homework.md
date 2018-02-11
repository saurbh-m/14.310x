Exercise 1
================
Saurabh Mishra
11 February 2018

### Question 16

We have asked the age of a group of 12 students. While 10 of them provided us with this information, 2 of them did not. We have constructed the vector age that captures this information. If we were interested in getting the vector without the missing values, which of the following lines of code would be useful to achieve this purpose?(Select all that apply)

``` r
age <- c(12, 28, 35, 27, NA, 25, 32, 45, 31, 23, NA, 34)

age[-c(5, 11)]
```

    ##  [1] 12 28 35 27 25 32 45 31 23 34

``` r
age[c(-5, -11)]
```

    ##  [1] 12 28 35 27 25 32 45 31 23 34

``` r
age[c(1, 2, 3, 4, 6, 7, 8, 9, 10, 12)]
```

    ##  [1] 12 28 35 27 25 32 45 31 23 34

``` r
age[!is.na(age)] 
```

    ##  [1] 12 28 35 27 25 32 45 31 23 34

``` r
x <- list(values=sin(1:3), ids=letters[1:3], sub=list(foo=42,bar=13))
print(x)
```

    ## $values
    ## [1] 0.8414710 0.9092974 0.1411200
    ## 
    ## $ids
    ## [1] "a" "b" "c"
    ## 
    ## $sub
    ## $sub$foo
    ## [1] 42
    ## 
    ## $sub$bar
    ## [1] 13

### Question 18

Download the data "CitesforSara.csv" into RStudio. This dataset includes paper-level citations from 1969 to 1998. First, read the CSV file into R

``` r
library(tidyverse)
```

    ## ── Attaching packages ────────────────────────────────────────── tidyverse 1.2.1 ──

    ## ✔ ggplot2 2.2.1     ✔ purrr   0.2.4
    ## ✔ tibble  1.4.1     ✔ dplyr   0.7.4
    ## ✔ tidyr   0.7.2     ✔ stringr 1.2.0
    ## ✔ readr   1.1.1     ✔ forcats 0.2.0

    ## ── Conflicts ───────────────────────────────────────────── tidyverse_conflicts() ──
    ## ✖ dplyr::filter() masks stats::filter()
    ## ✖ dplyr::lag()    masks stats::lag()

``` r
papers <- read.csv("CitesforSara.csv")
papers_select <- select(papers, journal, year, cites, title, au1)
head(papers_select)
```

    ##                    journal year cites
    ## 1 American-Economic-Review 1993    31
    ## 2 American-Economic-Review 1993     4
    ## 3 American-Economic-Review 1993    28
    ## 4 American-Economic-Review 1993    10
    ## 5 American-Economic-Review 1993     5
    ## 6 American-Economic-Review 1993    21
    ##                                                                               title
    ## 1 Jeux Sans Frontieres:  Tax Competition and Tax Coordination When Countries  Diffe
    ## 2                           Changes in Economic Instability in 19th-Century America
    ## 3                                    Factor Shares and Savings in Endogenous Growth
    ## 4 Strategic Discipline in Monetary Policy with Private Information:  Optimal  Targe
    ## 5                  Will Affirmative-Action Policies Eliminate Negative Stereotypes?
    ## 6                     Mergers and Market Power:  Evidence from the Airline Industry
    ##                      au1
    ## 1           Kanbur,-Ravi
    ## 2         James,-John-A.
    ## 3      Bertola,-Giuseppe
    ## 4 Garfinkel,-Michelle-R.
    ## 5         Coate,-Stephen
    ## 6            Kim,-E.-Han

``` r
# Let’s take a look at some of the most popular papers. Using the filter() method, how many records exist where there are greater than or equal to 100 citations?

filter(papers, cites >= 100)
```

    ##                                journal year cites
    ## 1             American-Economic-Review 1994   117
    ## 2                         Econometrica 1971   149
    ## 3                         Econometrica 1971   170
    ## 4                         Econometrica 1971   155
    ## 5                         Econometrica 1971   139
    ## 6                         Econometrica 1971   108
    ## 7                         Econometrica 1972   164
    ## 8                         Econometrica 1972   150
    ## 9                         Econometrica 1973   361
    ## 10                        Econometrica 1973   107
    ## 11                        Econometrica 1973   238
    ## 12                        Econometrica 1973   211
    ## 13                        Econometrica 1973   107
    ## 14                        Econometrica 1973   527
    ## 15                        Econometrica 1973   171
    ## 16                        Econometrica 1973   123
    ## 17                        Econometrica 1973   173
    ## 18                        Econometrica 1974   339
    ## 19                        Econometrica 1974   123
    ## 20                        Econometrica 1975   223
    ## 21                        Econometrica 1975   168
    ## 22                        Econometrica 1976   157
    ## 23                        Econometrica 1976   174
    ## 24                        Econometrica 1976   106
    ## 25                        Econometrica 1977   194
    ## 26                        Econometrica 1977   156
    ## 27                        Econometrica 1977   117
    ## 28                        Econometrica 1977   157
    ## 29                        Econometrica 1978   147
    ## 30                        Econometrica 1978   190
    ## 31                        Econometrica 1978   108
    ## 32                        Econometrica 1978   266
    ## 33                        Econometrica 1978   104
    ## 34                        Econometrica 1978   134
    ## 35                        Econometrica 1978   123
    ## 36                        Econometrica 1978   117
    ## 37                        Econometrica 1978   236
    ## 38                        Econometrica 1978  1217
    ## 39                        Econometrica 1978   197
    ## 40                        Econometrica 1978   249
    ## 41                        Econometrica 1978   431
    ## 42                        Econometrica 1978   230
    ## 43                        Econometrica 1979   189
    ## 44                        Econometrica 1979   182
    ## 45                        Econometrica 1979   108
    ## 46                        Econometrica 1979   215
    ## 47                        Econometrica 1979   301
    ## 48                        Econometrica 1979   135
    ## 49                        Econometrica 1979  1602
    ## 50                        Econometrica 1979  2227
    ## 51                        Econometrica 1979   246
    ## 52                        Econometrica 1979   391
    ## 53                        Econometrica 1980   864
    ## 54                        Econometrica 1980   107
    ## 55                        Econometrica 1980   113
    ## 56                        Econometrica 1980   106
    ## 57                        Econometrica 1980   141
    ## 58                        Econometrica 1980  2251
    ## 59                        Econometrica 1980   100
    ## 60                        Econometrica 1981   222
    ## 61                        Econometrica 1981  1031
    ## 62                        Econometrica 1981   101
    ## 63                        Econometrica 1981   128
    ## 64                        Econometrica 1981   116
    ## 65                        Econometrica 1981   112
    ## 66                        Econometrica 1981   124
    ## 67                        Econometrica 1981   195
    ## 68                        Econometrica 1981   150
    ## 69                        Econometrica 1981   102
    ## 70                        Econometrica 1981   102
    ## 71                        Econometrica 1981   455
    ## 72                        Econometrica 1982   213
    ## 73                        Econometrica 1982   199
    ## 74                        Econometrica 1982   379
    ## 75                        Econometrica 1982   111
    ## 76                        Econometrica 1982   203
    ## 77                        Econometrica 1982   140
    ## 78                        Econometrica 1982  1077
    ## 79                        Econometrica 1982   504
    ## 80                        Econometrica 1982   516
    ## 81                        Econometrica 1982   348
    ## 82                        Econometrica 1982   983
    ## 83                        Econometrica 1982   563
    ## 84                        Econometrica 1982   148
    ## 85                        Econometrica 1982   269
    ## 86                        Econometrica 1982   117
    ## 87                        Econometrica 1982   549
    ## 88                        Econometrica 1982   263
    ## 89                        Econometrica 1982   421
    ## 90                        Econometrica 1982   123
    ## 91                        Econometrica 1982   225
    ## 92                        Econometrica 1983   268
    ## 93                        Econometrica 1983   119
    ## 94                        Econometrica 1983   109
    ## 95                        Econometrica 1983   140
    ## 96                        Econometrica 1983   185
    ## 97                        Econometrica 1983   311
    ## 98                        Econometrica 1984   111
    ## 99                        Econometrica 1984   245
    ## 100                       Econometrica 1984   115
    ## 101                       Econometrica 1984   108
    ## 102                       Econometrica 1984   183
    ## 103                       Econometrica 1984   139
    ## 104                       Econometrica 1984   214
    ## 105                       Econometrica 1984   158
    ## 106                       Econometrica 1984   332
    ## 107                       Econometrica 1984   178
    ## 108                       Econometrica 1984   106
    ## 109                       Econometrica 1984   124
    ## 110                       Econometrica 1985   118
    ## 111                       Econometrica 1985   446
    ## 112                       Econometrica 1985   191
    ## 113                       Econometrica 1985   102
    ## 114                       Econometrica 1985   247
    ## 115                       Econometrica 1985   354
    ## 116                       Econometrica 1985   120
    ## 117                       Econometrica 1986   312
    ## 118                       Econometrica 1986   105
    ## 119                       Econometrica 1986   274
    ## 120                       Econometrica 1987   147
    ## 121                       Econometrica 1987  2164
    ## 122                       Econometrica 1987   171
    ## 123                       Econometrica 1987   136
    ## 124                       Econometrica 1987   205
    ## 125                       Econometrica 1987   240
    ## 126                       Econometrica 1987   553
    ## 127                       Econometrica 1987   164
    ## 128                       Econometrica 1987   317
    ## 129                       Econometrica 1987   110
    ## 130                       Econometrica 1987   143
    ## 131                       Econometrica 1988   137
    ## 132                       Econometrica 1988   225
    ## 133                       Econometrica 1989   198
    ## 134                       Econometrica 1989   149
    ## 135                       Econometrica 1989   126
    ## 136                       Econometrica 1989   494
    ## 137                       Econometrica 1989   290
    ## 138                       Econometrica 1989   119
    ## 139                       Econometrica 1989   142
    ## 140                       Econometrica 1990   236
    ## 141                       Econometrica 1990   114
    ## 142                       Econometrica 1990   199
    ## 143                       Econometrica 1990   133
    ## 144                       Econometrica 1990   141
    ## 145                       Econometrica 1991   182
    ## 146                       Econometrica 1991   259
    ## 147                       Econometrica 1991   214
    ## 148                       Econometrica 1991   490
    ## 149                       Econometrica 1992   148
    ## 150                       Econometrica 1992   125
    ## 151                       Econometrica 1993   157
    ## 152                       Econometrica 1993   109
    ## 153                       Econometrica 1993   119
    ## 154                       Econometrica 1993   140
    ## 155       Journal-of-Political-Economy 1992   118
    ## 156       Journal-of-Political-Economy 1993   125
    ## 157     Quarterly-Journal-of-Economics 1973   359
    ## 158     Quarterly-Journal-of-Economics 1974   118
    ## 159     Quarterly-Journal-of-Economics 1974   162
    ## 160     Quarterly-Journal-of-Economics 1976   105
    ## 161     Quarterly-Journal-of-Economics 1977   254
    ## 162     Quarterly-Journal-of-Economics 1977   110
    ## 163     Quarterly-Journal-of-Economics 1980   143
    ## 164     Quarterly-Journal-of-Economics 1985   250
    ## 165     Quarterly-Journal-of-Economics 1985   158
    ## 166     Quarterly-Journal-of-Economics 1990   126
    ## 167     Quarterly-Journal-of-Economics 1993   103
    ## 168         Review-of-Economic-Studies 1969   259
    ## 169         Review-of-Economic-Studies 1970   168
    ## 170         Review-of-Economic-Studies 1971   388
    ## 171         Review-of-Economic-Studies 1971   105
    ## 172         Review-of-Economic-Studies 1971   166
    ## 173         Review-of-Economic-Studies 1972   127
    ## 174         Review-of-Economic-Studies 1973   131
    ## 175         Review-of-Economic-Studies 1974   151
    ## 176         Review-of-Economic-Studies 1974   181
    ## 177         Review-of-Economic-Studies 1974   158
    ## 178         Review-of-Economic-Studies 1974   343
    ## 179         Review-of-Economic-Studies 1974   201
    ## 180         Review-of-Economic-Studies 1975   159
    ## 181         Review-of-Economic-Studies 1975   380
    ## 182         Review-of-Economic-Studies 1975   160
    ## 183         Review-of-Economic-Studies 1977   131
    ## 184         Review-of-Economic-Studies 1978   125
    ## 185         Review-of-Economic-Studies 1981   175
    ## 186         Review-of-Economic-Studies 1982   112
    ## 187         Review-of-Economic-Studies 1982   134
    ## 188         Review-of-Economic-Studies 1983   133
    ## 189         Review-of-Economic-Studies 1983   110
    ## 190         Review-of-Economic-Studies 1984   386
    ## 191         Review-of-Economic-Studies 1985   187
    ## 192         Review-of-Economic-Studies 1986   127
    ## 193         Review-of-Economic-Studies 1986   122
    ## 194         Review-of-Economic-Studies 1988   109
    ## 195         Review-of-Economic-Studies 1990   213
    ## 196         Review-of-Economic-Studies 1991   127
    ## 197 Review-of-Economics-and-Statistics 1972   110
    ## 198 Review-of-Economics-and-Statistics 1972   131
    ## 199 Review-of-Economics-and-Statistics 1973   483
    ## 200 Review-of-Economics-and-Statistics 1974   141
    ## 201 Review-of-Economics-and-Statistics 1975   354
    ## 202 Review-of-Economics-and-Statistics 1978   162
    ## 203 Review-of-Economics-and-Statistics 1978   148
    ## 204 Review-of-Economics-and-Statistics 1979   141
    ## 205 Review-of-Economics-and-Statistics 1979   114
    ##                                                                                 title
    ## 1                                                   Is Inequality Harmful for Growth?
    ## 2   Further Evidence on the Estimation of Dynamic Economic Relations from a Time  Ser
    ## 3   The Use of Variance Components Models in Pooling Cross Section and Time  Series D
    ## 4                                                        Investment Under Uncertainty
    ## 5    Some Statistical Models for Limited Dependent Variables with Application to  the
    ## 6                                                 Identification in Parametric Models
    ## 7                                 Methods of Estimation for Markets in Disequilibrium
    ## 8    Existence of Equilibrium of Plans, Prices, and Price Expectations in a  Sequence
    ## 9                                    Manipulation of Voting Schemes: A General Result
    ## 10                             On a Class of Equilibrium Conditions for Majority Rule
    ## 11                Regression Analysis when the Dependent Variable is Truncated Normal
    ## 12  A Subordinated Stochastic Process Model with Finite Variance for Speculative  Pri
    ## 13                                  Path Independence, Rationality, and Social Choice
    ## 14                                       An Intertemporal Capital Asset Pricing Model
    ## 15  Alternative Tests of Independence Between Stochastic Regressors and  Disturbances
    ## 16                 The Stability of Models of Money and Growth with Perfect Foresight
    ## 17                                                                Incentives in Teams
    ## 18                                      Shadow Prices, Market Wages, and Labor Supply
    ## 19                 Maximum Likelihood Methods for Models of Markets in Disequilibrium
    ## 20                                       Other Solutions to Nash's Bargaining Problem
    ## 21  Estimation and Hypothesis Testing in Singular Equation Systems with  Autoregressi
    ## 22  Rational Expectations and the Natural Rate Hypothesis: Some Consistent  Estimates
    ## 23                                        Poverty: An Ordinal Approach to Measurement
    ## 24                Estimating Regression Models with Multiplicative Heteroscedasticity
    ## 25                                                                 Free Rider Problem
    ## 26                                             Social Choice Theory: A Re-examination
    ## 27                                               Temporary General Equilibrium Theory
    ## 28                   The Estimation of Choice Probabilities from Choice Based Samples
    ## 29                                     Testing Non-Nested Nonlinear Regression Models
    ## 30   Testing against General Autoregressive and Moving Average Error Models When  the
    ## 31  Testing for Higher Order Serial Correlation in Regression Equations When the  Reg
    ## 32                       Dummy Endogenous Variables in a Simultaneous Equation System
    ## 33                       Temporal Resolution of Uncertainty and Dynamic Choice Theory
    ## 34                    On the Time Consistency of Optimal Policy in a Monetary Economy
    ## 35   Bayesian Estimates of Equation System Parameters: An Application of  Integration
    ## 36                                                Dynamic Aspects of Earning Mobility
    ## 37                               On the Pooling of Time Series and Cross Section Data
    ## 38                                                Specification Tests in Econometrics
    ## 39  A Conditional Probit Model for Qualitative Choice: Discrete Decisions  Recognizin
    ## 40           A Maximum Likelihood Procedure for Regression with Autocorrelated Errors
    ## 41                                                Asset Prices in an Exchange Economy
    ## 42                                                               Regression Quantiles
    ## 43                                                          Informational Equilibrium
    ## 44             General Conditions for Global Intransitivities in Formal Voting Models
    ## 45  Rational Expectations Equilibrium: Generic Existence and the Information  Reveale
    ## 46                                                           Stability in Competition
    ## 47                                 Incentive Compatibility and the Bargaining Problem
    ## 48                                 Estimating the Probability of Leaving Unemployment
    ## 49                                     Sample Selection Bias as a Specification Error
    ## 50                                Prospect Theory: An Analysis of Decision under Risk
    ## 51                               Econometric Methods for the Duration of Unemployment
    ## 52              A Simple Test for Heteroscedasticity and Random Coefficient Variation
    ## 53                                                         Macroeconomics and Reality
    ## 54                            A Capital Market in an Equilibrium Business Cycle Model
    ## 55             Approximating a Truncated Normal Regression with the Method of Moments
    ## 56                           The Class of Additively Decomposable Inequality Measures
    ## 57                   Econometric Implications of the Rational Expectations Hypothesis
    ## 58  A Heteroskedasticity-Consistent Covariance Matrix Estimator and a Direct  Test fo
    ## 59                    Advertising and Aggregate Consumption: An Analysis of Causality
    ## 60                                     Panel Data and Unobservable Individual Effects
    ## 61        Likelihood Ratio Statistics for Autoregressive Time Series with a Unit Root
    ## 62       Monitoring Cooperative Agreements in a Repeated Principal-Agent Relationship
    ## 63                              Applied Welfare Economics with Discrete Choice Models
    ## 64                                                          Testing for Unit Roots: 1
    ## 65                      Spurious Periodicity in Inappropriately Detrended Time Series
    ## 66                                           Demographic Variables in Demand Analysis
    ## 67                                   Resource Allocation under Asymmetric Information
    ## 68                 The Present-Value Relation: Tests Based on Implied Variance Bounds
    ## 69                                        Biases in Dynamic Models with Fixed Effects
    ## 70               What Do Economists Know? An Empirical Study of Experts' Expectations
    ## 71   Several Tests for Model Specification in the Presence of Alternative  Hypotheses
    ## 72                                            Selection and the Evolution of Industry
    ## 73  The Sensitivity of Consumption to Transitory Income: Estimates from Panel  Data o
    ## 74                           Expected Utility Analysis without the Independence Axiom
    ## 75                               On the Estimation of Structural Hedonic Price Models
    ## 76     Limit Pricing and Entry under Incomplete Information: An Equilibrium  Analysis
    ## 77  The Economic Theory of Index Numbers and the Measurement of Input, Output,  and P
    ## 78   Autoregressive Conditional Heteroscedasticity with Estimates of the Variance  of
    ## 79                               Maximum Likelihood Estimation of Misspecified Models
    ## 80                                          Perfect Equilibrium in a Bargaining Model
    ## 81                                       A Theory of Auctions and Competitive Bidding
    ## 82                Large Sample Properties of Generalized Method of Moments Estimators
    ## 83                                           Time to Build and Aggregate Fluctuations
    ## 84                                                 Strategic Information Transmission
    ## 85                                         Regulating a Monopolist with Unknown Costs
    ## 86                    Instrumental Variables Regression with Independent Observations
    ## 87                                                              Sequential Equilibria
    ## 88                    Tobin's Marginal q and Average q: A Neoclassical Interpretation
    ## 89  Generalized Instrumental Variables Estimation of Nonlinear Rational  Expectations
    ## 90                                      The Nonparametric Approach to Demand Analysis
    ## 91  Theoretical Restrictions on the Parameters of Indirect Addilog Demand  Equations-
    ## 92                                         An Analysis of the Principal-Agent Problem
    ## 93                   The Price Variability-Volume Relationship on Speculative Markets
    ## 94                   Efficient and Durable Decision Rules with Incomplete Information
    ## 95  A Generalization of the Quasilinear Mean with Applications to the  Measurement of
    ## 96  Testing Residuals from Least Squares Regression for Being Generated by the  Gauss
    ## 97                                                                         Exogeneity
    ## 98                  Pseudo Maximum Likelihood Methods: Applications to Poisson Models
    ## 99                         Noncooperative Collusion under Imperfect Price Information
    ## 100           Involuntary Unemployment as a Perfect Equilibrium in a Bargaining Model
    ## 101                               Specification Tests for the Multinomial Logit Model
    ## 102                   Rationalizable Strategic Behavior and the Problem of Perfection
    ## 103 Investment and Wages in the Absence of Binding Contracts: A Nash Bargining  Appro
    ## 104 Econometric Models for Count Data with an Application to the Patents-R&D  Relatio
    ## 105                                         Pseudo Maximum Likelihood Methods: Theory
    ## 106  A Method for Minimizing the Impact of Distributional Assumptions in  Econometric
    ## 107                                                 Rationalizable Strategic Behavior
    ## 108                                                         Testing for Unit Roots: 2
    ## 109 An Econometric Analysis of Residential Electric Appliance Holdings and  Consumpti
    ## 110             Maximum Likelihood Specification Testing and Conditional Moment Tests
    ## 111                                  A Theory of the Term Structure of Interest Rates
    ## 112                                         On Endogenous Competitive Business Cycles
    ## 113  A Profitable Approach to Labor Supply and Commodity Demands over the Life- Cycle
    ## 114                        An Intertemporal General Equilibrium Model of Asset Prices
    ## 115                                           Continuous Auctions and Insider Trading
    ## 116 Money, Real Interest Rates, and Output: A Reinterpretation of Postwar U.S.   Data
    ## 117 The Folk Theorem in Repeated Games with Discounting or with Incomplete  Informati
    ## 118  The Encompassing Principle and Its Application to Testing Non-nested  Hypotheses
    ## 119                                          On the Strategic Stability of Equilibria
    ## 120            Aggregation and Linearity in the Provision of Intertemporal Incentives
    ## 121      Co-integration and Error Correction: Representation, Estimation, and Testing
    ## 122                         Flexible Functional Forms and Global Curvature Conditions
    ## 123                                          Equilibrium Selection in Signaling Games
    ## 124       Estimating Time Varying Risk Premia in the Term Structure: The Arch-M Model
    ## 125                                              The Dual Theory of Choice under Risk
    ## 126                                           Time Series Regression with a Unit Root
    ## 127                   Correlated Equilibrium as an Expression of Bayesian Rationality
    ## 128        Asymptotic Properties of Least Squares Estimators of Cointegrating Vectors
    ## 129                                   Money and Interest in a Cash-in-Advance Economy
    ## 130 The Sensitivity of an Empirical Model of Married Women's Hours of Work to  Econom
    ## 131                       On the Theory of Infinitely Repeated Games with Discounting
    ## 132                            Efficiency Wages and the Inter-industry Wage Structure
    ## 133                    Subjective Probability and Expected Utility without Additivity
    ## 134 A Method of Simulated Moments for Estimation of Discrete Response Models  without
    ## 135  Substitution, Risk Aversion, and the Temporal Behavior of Consumption and  Asset
    ## 136                The Great Crash, the Oil Price Shock, and the Unit Root Hypothesis
    ## 137 A New Approach to the Economic Analysis of Nonstationary Time Series and the  Bus
    ## 138                         Simulation and the Asymptotics of Optimization Estimators
    ## 139            Bayesian Inference in Econometric Models Using Monte Carlo Integration
    ## 140                   Asymptotic Properties of Residual Based Tests for Cointegration
    ## 141 Rationalizability, Learning, and Equilibrium in Games with Strategic  Complementa
    ## 142                       Inference in Linear Time Series Models with Some Unit Roots
    ## 143                                Precautionary Saving in the Small and in the Large
    ## 144                                    Unemployment Insurance and Unemployment Spells
    ## 145                                         Optimal Inference in Cointegrated Systems
    ## 146   Heteroskedasticity and Autocorrelation Consistent Covariance Matrix  Estimation
    ## 147                  Conditional Heteroskedasticity in Asset Returns:  A New Approach
    ## 148 Estimation and Hypothesis Testing of Cointegration Vectors in Gaussian  Vector Au
    ## 149                                    A Model of Growth through Creative Destruction
    ## 150 Bond Pricing and the Term Structure of Interest Rates: A New Methodology for  Con
    ## 151                              Learning, Mutation, and Long Run Equilibria in Games
    ## 152                                                                  Making a Miracle
    ## 153  Tests for Parameter Instability and Structural Change with Unknown Change  Point
    ## 154   A Simple Estimator of Cointegrating Vectors in Higher Order Integrated  Systems
    ## 155 A Theory of Fads, Fashion, Custom, and Cultural Change in Informational  Cascades
    ## 156                                  Wage Inequality and the Rise in Returns to Skill
    ## 157                                                              Job Market Signaling
    ## 158  Alternative Theories of Wage Determination and Unemployment in LDC'S: The  Labor
    ## 159                      Environmental Preservation, Uncertainty, and Irreversibility
    ## 160                                     Commodity Bundling and the Burden of Monopoly
    ## 161 From Entry Barriers to Mobility Barriers: Conjectural Decisions and  Contrived De
    ## 162   The Demand for Insurance and Protection: The Case of Irreplaceable  Commodities
    ## 163                                             Experience, Performance, and Earnings
    ## 164               The Optimal Degree of Commitment to an Intermediate Monetary Target
    ## 165         A Near-rational Model of the Business Cycle, with Wage and Price Intertia
    ## 166                                   Threshold Externalities in Economic Development
    ## 167                                    Finance and Growth:  Schumpeter Might Be Right
    ## 168                                 The Efficiency Analysis of Choices Involving Risk
    ## 169                                     The Effect of Uncertainty on Saving Decisions
    ## 170                           An Exploration in the Theory of Optimum Income Taxation
    ## 171                                          Choice Functions and Revealed Preference
    ## 172                                      A Non-cooperative Equilibrium for Supergames
    ## 173                                         A Theory of Monopolistic Price Adjustment
    ## 174 The Internal Structure of Functional Relationships: Separability,  Substitution a
    ## 175                                                  Pigou, Taxation and Public Goods
    ## 176                                                             Prices vs. Quantities
    ## 177                                         On the General Problem of Model Selection
    ## 178                                       Wages and Employment under Uncertain Demand
    ## 179                                      Incentives and Risk Sharing in Sharecropping
    ## 180                         Neo-Keynesian Disequilibrium Theory in a Monetary Economy
    ## 181                                                      The Political Business Cycle
    ## 182  The Principle of Minimum Differentiation Reconsidered: Some New Developments  in
    ## 183                                           Inflation and Costs of Price Adjustment
    ## 184                                               Instability of Simple Dynamic Games
    ## 185               Debt with Potential Repudiation: Theoretical and Empirical Analysis
    ## 186                                                         A Theory of Wage Dynamics
    ## 187                        Relaxing Price Competition through Product Differentiation
    ## 188            Optimal Labour Contracts under Asymmetric Information: An Introduction
    ## 189                               International R & D Rivalry and Industrial Strategy
    ## 190                                 Financial Intermediation and Delegated Monitoring
    ## 191                       Incentive-Compatible Debt Contracts: The One-Period Problem
    ## 192           The Existence of Equilibrium in Discontinuous Economic Games, I: Theory
    ## 193                               Non-cooperative Bargaining Theory:  An Introduction
    ## 194                                         Elections and Macroeconomic Policy Cycles
    ## 195   Statistical Inference in Instrumental Variables Regression with I(1)  Processes
    ## 196 Some Tests of Specification for Panel Data: Monte Carlo Evidence and an  Applicat
    ## 197                                 The Estimation of the Lorenz Curve and Gini Index
    ## 198                                                  The Elements of Market Structure
    ## 199                                   Transcendental Logarithmic Production Frontiers
    ## 200           The Effect of Income Instability on Farmers' Consumption and Investment
    ## 201                             Technology, Prices, and the Derived Demand for Energy
    ## 202                              The Effect of Economic Events on Votes for President
    ## 203          An Empirical Study of Politico-Economic Interaction in the United States
    ## 204                        The Structure within Industries and Companies' Performance
    ## 205 The Casual Causal Relationship between Money and Income: Some Caveats for  Time S
    ##                         au1                         au2
    ## 1          Persson,-Torsten            Tabellini,-Guido
    ## 2          Nerlove,-Marc-L.                            
    ## 3            Maddala,-G.-S.                            
    ## 4     Lucas,-Robert-E., Jr.         Prescott,-Edward-C.
    ## 5            Cragg,-John-G.                            
    ## 6     Rothenberg,-Thomas-J.                            
    ## 7              Fair,-Ray-C.           Jaffee,-Dwight-M.
    ## 8               Radner,-Roy                            
    ## 9            Gibbard,-Allan                            
    ## 10        Kramer,-Gerald-H.                            
    ## 11         Amemiya,-Takeshi                            
    ## 12          Clark,-Peter-K.                            
    ## 13        Plott,-Charles-R.                            
    ## 14        Merton,-Robert-C.                            
    ## 15               Wu,-De-Min                            
    ## 16       Sargent,-Thomas-J.               Wallace,-Neil
    ## 17         Groves,-Theodore                            
    ## 18        Heckman,-James-J.                            
    ## 19           Maddala,-G.-S.          Nelson,-Forrest-D.
    ## 20              Kalai,-Ehud           Smorodinsky,-Meir
    ## 21         Berndt,-Ernst-R.            Savin,-N.-Eugene
    ## 22     McCallum,-Bennett-T.                            
    ## 23          Sen,-Amartya-K.                            
    ## 24            Harvey,-A.-C.                            
    ## 25         Groves,-Theodore            Ledyard,-John-O.
    ## 26          Sen,-Amartya-K.                            
    ## 27  Grandmont,-Jean-Michele                            
    ## 28       Manski,-Charles-F.           Lerman,-Steven-R.
    ## 29       Pesaran,-M.-Hashem            Deaton,-Angus-S.
    ## 30       Godfrey,-Lesley-G.                            
    ## 31       Godfrey,-Lesley-G.                            
    ## 32        Heckman,-James-J.                            
    ## 33          Kreps,-David-M.            Porteus,-Evan-L.
    ## 34      Calvo,-Guillermo-A.                            
    ## 35              Kloek,-Tuen         van-Dijk,-Herman-K.
    ## 36          Lillard,-Lee-A.           Willis,-Robert-J.
    ## 37            Mundlak,-Yair                            
    ## 38        Hausman,-Jerry-A.                            
    ## 39        Hausman,-Jerry-A.              Wise,-David-A.
    ## 40        Beach,-Charles-M.         MacKinnon,-James-G.
    ## 41    Lucas,-Robert-E., Jr.                            
    ## 42        Koenker,-Roger-W.    Bassett,-Gilbert-W., Jr.
    ## 43           Riley,-John-G.                            
    ## 44     McKelvey,-Richard-D.                            
    ## 45              Radner,-Roy                            
    ## 46      d'Aspremont,-Claude    Jaskold-Gabszewicz,-Jean
    ## 47        Myerson,-Roger-B.                            
    ## 48      Nickell,-Stephen-J.                            
    ## 49        Heckman,-James-J.                            
    ## 50         Kahneman,-Daniel               Tversky,-Amos
    ## 51          Lancaster,-Tony                            
    ## 52       Breusch,-Trevor-S.                Pagan,-A.-R.
    ## 53     Sims,-Christopher-A.                            
    ## 54         Barro,-Robert-J.                            
    ## 55        Olsen,-Randall-J.                            
    ## 56    Shorrocks,-Anthony-F.                            
    ## 57       Wallis,-Kenneth-F.                            
    ## 58           White,-Halbert                            
    ## 59       Ashley,-Richard-A.        Granger,-Clive-W.-J.
    ## 60        Hausman,-Jerry-A.          Taylor,-William-E.
    ## 61         Dickey,-David-A.            Fuller,-Wayne-A.
    ## 62              Radner,-Roy                            
    ## 63        Small,-Kenneth-A.            Rosen,-Harvey-S.
    ## 64          Evans,-G.-B.-A.            Savin,-N.-Eugene
    ## 65       Nelson,-Charles-R.               Kang,-Heejoon
    ## 66        Pollak,-Robert-A.          Wales,-Terrence-J.
    ## 67            Harris-Milton         Townsend,-Robert-M.
    ## 68        LeRoy,-Stephen-F.          Porter,-Richard-D.
    ## 69      Nickell,-Stephen-J.                            
    ## 70          Brown,-Bryan-W.              Maital,-Shlomo
    ## 71        Davidson,-Russell         MacKinnon,-James-G.
    ## 72         Jovanovic,-Boyan                            
    ## 73          Hall,-Robert-E.        Mishkin,-Frederic-S.
    ## 74         Machina,-Mark-J.                            
    ## 75          Brown,-James-N.            Rosen,-Harvey-S.
    ## 76         Milgrom,-Paul-R.            Roberts,-John-M.
    ## 77        Caves,-Douglas-W.     Christensen,-Laurits-R.
    ## 78    Engle,-Robert-F., III                            
    ## 79           White,-Halbert                            
    ## 80        Rubinstein,-Ariel                            
    ## 81         Milgrom,-Paul-R.            Weber,-Robert-J.
    ## 82       Hansen,-Lars-Peter                            
    ## 83         Kydland,-Finn-E.         Prescott,-Edward-C.
    ## 84     Crawford,-Vincent-P.                 Sobel,-Joel
    ## 85          Baron,-David-P.           Myerson,-Roger-B.
    ## 86           White,-Halbert                            
    ## 87          Kreps,-David-M.           Wilson,-Robert-B.
    ## 88           Hayashi,-Fumio                            
    ## 89       Hansen,-Lars-Peter       Singleton,-Kenneth-J.
    ## 90           Varian,-Hal-R.                            
    ## 91             Murty,-K.-N.                            
    ## 92     Grossman,-Sanford-J.             Hart,-Oliver-D.
    ## 93       Tauchen,-George-E.                 Pitts,-Mark
    ## 94      Holmstrom,-Bengt-R.           Myerson,-Roger-B.
    ## 95           Chew,-Soo-Hong                            
    ## 96       Sargan,-John-Denis              Bhargava,-Alok
    ## 97    Engle,-Robert-F., III            Hendry,-David-F.
    ## 98    Gourieroux,-Christian              Monfort,-Alain
    ## 99         Green,-Edward-J.           Porter,-Robert-H.
    ## 100           Shaked,-Avner                Sutton,-John
    ## 101       Hausman,-Jerry-A.         McFadden,-Daniel-L.
    ## 102        Pearce,-David-G.                            
    ## 103          Grout,-Paul-A.                            
    ## 104       Hausman,-Jerry-A.            Hall,-Bronwyn-H.
    ## 105   Gourieroux,-Christian              Monfort,-Alain
    ## 106       Heckman,-James-J.              Singer,-Burton
    ## 107     Berheim,-B.-Douglas                            
    ## 108         Evans,-G.-B.-A.            Savin,-N.-Eugene
    ## 109       Dubin,-Jeffrey-A.         McFadden,-Daniel-L.
    ## 110       Newey,-Whitney-K.                            
    ## 111            Cox,-John-C. Ingersoll,-Jonathan-E., Jr.
    ## 112 Grandmont,-Jean-Michele                            
    ## 113     Browning,-Martin-J.            Deaton,-Angus-S.
    ## 114            Cox,-John-C. Ingersoll,-Jonathan-E., Jr.
    ## 115         Kyle,-Albert-S.                            
    ## 116    Litterman,-Robert-B.          Weiss,-Laurence-M.
    ## 117         Fudenberg,-Drew             Maskin,-Eric-S.
    ## 118       Mizon,-Grayham-E.      Richard,-Jean-Francois
    ## 119          Kohlberg,-Elon      Mertens,-Jean-Francois
    ## 120     Holmstrom,-Bengt-R.            Milgrom,-Paul-R.
    ## 121   Engle,-Robert-F., III        Granger,-Clive-W.-J.
    ## 122   Diewert,-Walter-Erwin          Wales,-Terrence-J.
    ## 123       Banks,-Jeffrey-S.                 Sobel,-Joel
    ## 124   Engle,-Robert-F., III            Lilien,-David-M.
    ## 125       Yaari,-Menahem-E.                            
    ## 126   Phillips,-Peter-C.-B.                            
    ## 127       Aumann,-Robert-J.                            
    ## 128         Stock,-James-H.                            
    ## 129   Lucas,-Robert-E., Jr.            Stokey,-Nancy-L.
    ## 130         Mroz,-Thomas-A.                            
    ## 131            Abreu,-Dilip                            
    ## 132        Krueger,-Alan-B.        Summers,-Lawrence-H.
    ## 133       Schmeidler,-David                            
    ## 134     McFadden,-Daniel-L.                            
    ## 135       Epstein,-Larry-G.             Zin,-Stanley-E.
    ## 136          Perron,-Pierre                            
    ## 137      Hamilton,-James-D.                            
    ## 138         Pakes,-Ariel-S.              Pollard,-David
    ## 139         Geweke,-John-F.                            
    ## 140   Phillips,-Peter-C.-B.               Ouliaris,-Sam
    ## 141        Milgrom,-Paul-R.            Roberts,-John-M.
    ## 142    Sims,-Christopher-A.             Stock,-James-H.
    ## 143       Kimball,-Miles-S.                            
    ## 144         Meyer,-Bruce-D.                            
    ## 145   Phillips,-Peter-C.-B.                            
    ## 146   Andrews,-Donald-W.-K.                            
    ## 147       Nelson,-Daniel-B.                            
    ## 148         Johansen,-Soren                            
    ## 149        Aghion,-Philippe            Howitt,-Peter-W.
    ## 150            Heath,-David              Jarrow,-Robert
    ## 151      Kandori,-Michihiro          Mailath,-George-J.
    ## 152   Lucas,-Robert-E., Jr.                            
    ## 153   Andrews,-Donald-W.-K.                            
    ## 154         Stock,-James-H.             Watson,-Mark-W.
    ## 155    Bikhchandani,-Sushil          Hirshleifer,-David
    ## 156           Juhn,-Chinhui            Murphy,-Kevin-M.
    ## 157      Spence,-A.-Michael                            
    ## 158     Stiglitz,-Joseph-E.                            
    ## 159       Arrow,-Kenneth-J.          Fisher,-Anthony-C.
    ## 160    Adams,-William-James            Yellen,-Janet-L.
    ## 161       Caves,-Richard-E.          Porter,-Michael-E.
    ## 162         Cook,-Philip-J.           Graham,-Daniel-A.
    ## 163        Medoff,-James-L.       Abraham,-Katharine-G.
    ## 164      Rogoff,-Kenneth-S.                            
    ## 165      Akerlof,-George-A.            Yellen,-Janet-L.
    ## 166       Azariadis,-Costas               Drazen,-Allan
    ## 167         King,-Robert-G.                Levine,-Ross
    ## 168           Hanoch,-Giora                  Levy,-Haim
    ## 169           Sandmo,-Agnar                            
    ## 170      Mirrlees,-James-A.                            
    ## 171         Sen,-Amartya-K.                            
    ## 172      Friedman,-James-W.                            
    ## 173        Barro,-Robert-J.                            
    ## 174        Berndt,-Ernst-R.     Christensen,-Laurits-R.
    ## 175    Atkinson,-Anthony-B.                Stern,-N.-H.
    ## 176     Weitzman,-Martin-L.                            
    ## 177      Pesaran,-M.-Hashem                            
    ## 178      Baily,-Martin-Neil                            
    ## 179     Stiglitz,-Joseph-E.                            
    ## 180    Benassy,-Jean-Pascal                            
    ## 181    Nordhaus,-William-D.                            
    ## 182        Eaton,-B.-Curtis          Lipsey,-Richard-G.
    ## 183       Sheshinski,-Eytan                Weiss,-Yoram
    ## 184       Schofield,-Norman                            
    ## 185         Eaton,-Jonathan             Gersovitz,-Mark
    ## 186          Harris,-Milton             Holstrom,-Bengt
    ## 187           Shaked,-Avner                Sutton,-John
    ## 188         Hart,-Oliver-D.                            
    ## 189     Spencer,-Barbara-J.           Brander,-James-A.
    ## 190     Diamond,-Douglas-W.                            
    ## 191        Gale,-Douglas-M.          Hellwig,-Martin-F.
    ## 192     Dasgupta,-Partha-S.             Maskin,-Eric-S.
    ## 193            Sutton,-John                            
    ## 194      Rogoff,-Kenneth-S.             Sibert,-Anne-C.
    ## 195   Phillips,-Peter-C.-B.            Hansen,-Bruce-E.
    ## 196        Arellano,-Manuel               Bond,-Stephen
    ## 197    Gastwirth,-Joseph-L.                            
    ## 198    Shepherd,-William-G.                            
    ## 199 Christensen,-Laurits-R.          Jorgenson,-Dale-W.
    ## 200            GirAo,-J.-A.                Tomek,-W.-G.
    ## 201        Berndt,-Ernst-R.              Wood,-David-O.
    ## 202            Fair,-Ray-C.                            
    ## 203          Frey,-Bruno-S.        Schneider,-Friedrich
    ## 204      Porter,-Michael-E.                            
    ## 205         Feige,-Edgar-L.          Pearce,-Douglas-K.
    ##                        au3 female1 female2 female3 page order nauthor
    ## 1                                0       0      NA   22    14       2
    ## 2                                0      NA      NA   24    10       1
    ## 3                               NA      NA      NA   18     9       1
    ## 4                                0       0      NA   23     1       2
    ## 5                                0      NA      NA   16    12       1
    ## 6                                0      NA      NA   15    11       1
    ## 7                                0       0      NA   18     5       2
    ## 8                                0      NA      NA   15     5       1
    ## 9                                0      NA      NA   15     1       1
    ## 10                               0      NA      NA   13     5       1
    ## 11                               0      NA      NA   20     1       1
    ## 12                               0      NA      NA   21    11       1
    ## 13                               0      NA      NA   17     7       1
    ## 14                               0      NA      NA   21     5       1
    ## 15                               0      NA      NA   18    11       1
    ## 16                               0       0      NA    6     4       2
    ## 17                               0      NA      NA   15     3       1
    ## 18                               0      NA      NA   16     5       1
    ## 19                              NA       0      NA   18     3       2
    ## 20                               0       0      NA    6     9       2
    ## 21                               0       0      NA   21    10       2
    ## 22                               0      NA      NA   10     3       1
    ## 23                               0      NA      NA   13     1       1
    ## 24                              NA      NA      NA    5     3       1
    ## 25                               0       0      NA   27     1       2
    ## 26                               0      NA      NA   37     3       1
    ## 27                               0      NA      NA   38     1       1
    ## 28                               0       0      NA   12    14       2
    ## 29                               0       0      NA   18    14       2
    ## 30                               0      NA      NA    9     3       1
    ## 31                               0      NA      NA    8     4       1
    ## 32                               0      NA      NA   29    11       1
    ## 33                               0       0      NA   16    16       2
    ## 34                               0      NA      NA   18    10       1
    ## 35                               0       0      NA   19     1       2
    ## 36                               0       0      NA   28     1       2
    ## 37                               0      NA      NA   17     6       1
    ## 38                               0      NA      NA   21     1       1
    ## 39                               0       0      NA   24    10       2
    ## 40                               0       0      NA    8     4       2
    ## 41                               0      NA      NA   17    11       1
    ## 42                               0       0      NA   18     3       2
    ## 43                               0      NA      NA   29     3       1
    ## 44                               0      NA      NA   28     2       1
    ## 45                               0      NA      NA   24     9       1
    ## 46           Thisse,-J.-F.       0       0      NA    6     6       3
    ## 47                               0      NA      NA   13     4       1
    ## 48                               0      NA      NA   18    12       1
    ## 49                               0      NA      NA    9    10       1
    ## 50                               0       0      NA   29     1       2
    ## 51                               0      NA      NA   18     9       1
    ## 52                               0      NA      NA    8    14       2
    ## 53                               0      NA      NA   48     1       1
    ## 54                               0      NA      NA   25     5       1
    ## 55                               0      NA      NA    7     2       1
    ## 56                               0      NA      NA   13     5       1
    ## 57                               0      NA      NA   25     2       1
    ## 58                               0      NA      NA   22     1       1
    ## 59    Schmalensee,-Richard       0       0       0   19     5       3
    ## 60                               0       0      NA   22     2       2
    ## 61                               0       0      NA   16    13       2
    ## 62                               0      NA      NA   22     2       1
    ## 63                               0       0      NA   26     6       2
    ## 64                              NA       0      NA   27    10       2
    ## 65                               0       0      NA   11     9       2
    ## 66                               0       0      NA   19    12       2
    ## 67                               0       0      NA   32     2       2
    ## 68                               0       0      NA   20     1       2
    ## 69                               0      NA      NA   10     4       1
    ## 70                               0       0      NA   14    11       2
    ## 71                               0       0      NA   13    11       2
    ## 72                               0      NA      NA   22     7       1
    ## 73                               0       0      NA   21     8       2
    ## 74                               0      NA      NA   47     1       1
    ## 75                               0       0      NA    4    15       2
    ## 76                               0       0      NA   17     7       2
    ## 77   Diewert,-Walter-Erwin       0       0       0   22     3       3
    ## 78                               0      NA      NA   21     8       1
    ## 79                               0      NA      NA   25     1       1
    ## 80                               0      NA      NA   13     6       1
    ## 81                               0       0      NA   34     1       2
    ## 82                               0      NA      NA   26    10       1
    ## 83                               0       0      NA   26     1       2
    ## 84                               0       0      NA   21     5       2
    ## 85                               0       0      NA   20     4       2
    ## 86                               0      NA      NA   17     9       1
    ## 87                               0       0      NA   32     2       2
    ## 88                               0      NA      NA   12    13       1
    ## 89                               0       0      NA   18     9       2
    ## 90                               0      NA      NA   29     6       1
    ## 91                              NA      NA      NA    3    14       1
    ## 92                               0       0      NA   39     2       2
    ## 93                               0       0      NA   21    13       2
    ## 94                               0       0      NA   21     9       2
    ## 95                               0      NA      NA   28    11       1
    ## 96                               0       0      NA   22     8       2
    ## 97  Richard,-Jean-Francois       0       0       0   28     1       3
    ## 98          Trognon,-Alain       0       0       0   20     9       3
    ## 99                               0       0      NA   14     5       2
    ## 100                              0       0      NA   14     2       2
    ## 101                              0       0      NA   22     9       2
    ## 102                              0      NA      NA   22    13       1
    ## 103                              0      NA      NA   12     8       1
    ## 104         Griliches,-Zvi       0       1       0   30     7       3
    ## 105         Trognon,-Alain       0       0       0   20     8       3
    ## 106                              0       0      NA   50     1       2
    ## 107                              0      NA      NA   22    12       1
    ## 108                             NA       0      NA   29    10       2
    ## 109                              0       0      NA   18     3       2
    ## 110                              0      NA      NA   24     2       1
    ## 111       Ross,-Stephen-A.       0       0       0   23     8       3
    ## 112                              0      NA      NA   51     1       1
    ## 113        Irish,-Margaret       0       0       1   41     1       3
    ## 114       Ross,-Stephen-A.       0       0       0   22     7       3
    ## 115                              0      NA      NA   21     4       1
    ## 116                              0       0      NA   28     8       2
    ## 117                              0       0      NA   22     2       2
    ## 118                              0       0      NA   22     8       2
    ## 119                              0       0      NA   35     1       2
    ## 120                              0       0      NA   26     3       2
    ## 121                              0       0      NA   26     1       2
    ## 122                              0       0      NA   26     3       2
    ## 123                              0       0      NA   15     8       2
    ## 124     Robins,-Russell-P.       0       0       0   17     7       3
    ## 125                              0      NA      NA   21     5       1
    ## 126                              0      NA      NA   25     2       1
    ## 127                              0      NA      NA   18     1       1
    ## 128                              0      NA      NA   22     2       1
    ## 129                              0       1      NA   23     1       2
    ## 130                              0      NA      NA   35     2       1
    ## 131                              0      NA      NA   14     6       1
    ## 132                              0       0      NA   35     1       2
    ## 133                              0      NA      NA   17     4       1
    ## 134                              0      NA      NA   32     1       1
    ## 135                              0       0      NA   33     8       2
    ## 136                              0      NA      NA   41     6       1
    ## 137                              0      NA      NA   28     4       1
    ## 138                              0       0      NA   31     2       2
    ## 139                              0      NA      NA   23     4       1
    ## 140                              0       0      NA   29     8       2
    ## 141                              0       0      NA   23     1       2
    ## 142        Watson,-Mark-W.       0       0       0   32     6       3
    ## 143                              0      NA      NA   21     3       1
    ## 144                              0      NA      NA   26     1       1
    ## 145                              0      NA      NA   24     1       1
    ## 146                              0      NA      NA   42    10       1
    ## 147                              0      NA      NA   24     3       1
    ## 148                              0      NA      NA   30     2       1
    ## 149                              0       0      NA   29     4       2
    ## 150         Morton,-Andrew       0       0       0   29     4       3
    ## 151            Rob,-Rafael       0       0       0   28     2       3
    ## 152                              0      NA      NA   22     1       1
    ## 153                              0      NA      NA   36     3       1
    ## 154                              0       0      NA   38     2       2
    ## 155             Welch,-Ivo       0       0       0   35     5       3
    ## 156         Pierce,-Brooks       1       0       0   33     2       3
    ## 157                              0      NA      NA   20     2       1
    ## 158                              0      NA      NA   34     2       1
    ## 159                              0       0      NA    8     7       2
    ## 160                              0       1      NA   24     8       2
    ## 161                              0       0      NA   21     4       2
    ## 162                              0       0      NA   14     8       2
    ## 163                              0       1      NA   34     6       2
    ## 164                              0      NA      NA   21     4       1
    ## 165                              0       1      NA   16     1       2
    ## 166                              0       0      NA   26    11       2
    ## 167                              0       0      NA   21     7       2
    ## 168                              1       0      NA   12     5       2
    ## 169                              0      NA      NA    8     3       1
    ## 170                              0      NA      NA   34     3       1
    ## 171                              0      NA      NA   11     4       1
    ## 172                              0      NA      NA   12     1       1
    ## 173                              0      NA      NA   10     2       1
    ## 174                              0       0      NA    8     8       2
    ## 175                              0      NA      NA   10     9       2
    ## 176                              0      NA      NA   15     3       1
    ## 177                              0      NA      NA   19     1       1
    ## 178                              0      NA      NA   14     3       1
    ## 179                              0      NA      NA   37     5       1
    ## 180                              0      NA      NA   21     2       1
    ## 181                              0      NA      NA   22     1       1
    ## 182                              0       0      NA   23     3       2
    ## 183                              0       0      NA   17     7       2
    ## 184                              0      NA      NA   20    18       1
    ## 185                              0       0      NA   21     8       2
    ## 186                              0       0      NA   19     1       2
    ## 187                              0       0      NA   11     1       2
    ## 188                              0      NA      NA   33     1       1
    ## 189                              1       0      NA   16    10       2
    ## 190                              0      NA      NA   22     3       1
    ## 191                              0       0      NA   17     8       2
    ## 192                              0       0      NA   26     1       2
    ## 193                              0      NA      NA   16     1       1
    ## 194                              0       1      NA   16     1       2
    ## 195                              0       0      NA   27     6       2
    ## 196                              0       0      NA   21     5       2
    ## 197                              0      NA      NA   11    13       1
    ## 198                              0      NA      NA   13     3       1
    ## 199       Lau,-Lawrence-J.       0       0       0   18     5       3
    ## 200      Mount,-Timothy-D.      NA      NA       0    9     2       3
    ## 201                              0       0      NA   10     1       2
    ## 202                              0      NA      NA   15     1       1
    ## 203                              0       0      NA   10     2       2
    ## 204                              0      NA      NA   14     7       1
    ## 205                              0       0      NA   13     5       2
    ##          past5   aflpn90 spage field subfld   aulpn90    aulpn80
    ## 1    1.9166670  3.083333   600     5      2 3.5000000  1.2500000
    ## 2    1.0000000  3.000000   359    12      2 0.0000000  1.6666670
    ## 3    0.5000000  3.000000   341    12      2 0.0000000  0.0000000
    ## 4    1.5000000  3.000000   659     2      1 1.5000000  1.7500000
    ## 5    2.3333330  3.000000   829    12      1 0.0000000  1.0000000
    ## 6    0.0000000  3.000000   577    12      1 0.3333333  2.0000000
    ## 7    1.2500000  3.000000   497    12      1 0.5000000  2.1666670
    ## 8    2.0000000  3.000000   289     2     10 1.0000000  3.8333330
    ## 9    0.0000000  3.000000   587    15      1 0.0000000  0.0000000
    ## 10   0.0000000  3.000000   285     2      4 0.0000000  0.0000000
    ## 11   0.0000000  3.000000   997    12      1 0.0000000  1.5000000
    ## 12   0.0000000  3.000000   135    12      1 0.0000000  1.0000000
    ## 13   0.5000000  3.000000  1075     2      4 1.6666670  3.6666670
    ## 14   0.0000000  3.000000   867     4      1 0.0000000  0.0000000
    ## 15   0.5000000  3.000000   733    12      1 0.0000000  0.0000000
    ## 16   1.2500000  3.000000  1043     5      1 1.2500000  3.0000000
    ## 17   0.0000000  3.000000   617     4      2 1.2500000  2.0000000
    ## 18   0.0000000  3.000000   679    11      1 1.5000000  2.5000000
    ## 19   2.5000000  3.000000  1013     2      1 0.2500000  0.5000000
    ## 20   0.0000000  3.000000   513     3      1 0.2500000  0.5000000
    ## 21   1.0000000  3.000000   937    12      1 0.2500000  1.1666670
    ## 22   2.0000000  3.000000    43     2      1 1.0000000  1.0000000
    ## 23   1.0000000  3.000000   219     2      2 2.0000000  1.0000000
    ## 24   0.0000000  3.000000   461    12      1 0.0000000  0.5000000
    ## 25   0.5000000  3.000000   783     2     10 0.8750000  1.2500000
    ## 26   2.0000000  3.000000    53     2      4 2.0000000  1.0000000
    ## 27   2.5000000  3.000000   535     2     10 0.0000000  1.0000000
    ## 28   0.0000000  3.000000  1977    12      1 1.2500000  1.0000000
    ## 29   2.0000000  3.000000   677     5      1 1.5000000  3.0000000
    ## 30   1.0000000  3.000000  1293    12      1 0.3333333  2.5000000
    ## 31   1.0000000  3.000000  1303    12      2 0.3333333  2.5000000
    ## 32   2.0000000  3.000000   931    12      1 1.5000000  2.5000000
    ## 33   0.0000000  3.000000   185     2      9 0.1666667  1.2500000
    ## 34   2.5000000  3.000000  1411     5      1 1.0000000  4.5000000
    ## 35   0.5000000  3.000000     1    12      1 0.0000000  0.2500000
    ## 36   0.2500000  3.000000   985    11      1 0.0000000  0.1666667
    ## 37   0.0000000  3.000000    69    12      2 0.0000000  0.5000000
    ## 38   1.5000000  3.000000  1251    12      1 0.5000000  4.1666670
    ## 39   2.0000000  3.000000   403    12      1 0.7500000  2.3333330
    ## 40   0.0000000  3.000000    51    12      2 0.2500000  1.0000000
    ## 41   3.0000000  3.000000  1429     2     10 1.5000000  1.5000000
    ## 42   0.0000000  3.000000    33    12      1 0.2500000  1.5000000
    ## 43   0.0000000  3.000000   331     2     10 0.0000000  4.0000000
    ## 44   1.0000000  3.000000  1085    15      1 1.5000000  1.3333330
    ## 45   0.6666667  3.000000   655     2     10 1.0000000  3.8333330
    ## 46   0.5000000  3.000000  1145     2      1 0.1111111  0.1666667
    ## 47   1.0000000  3.000000    61     2      4 0.0000000  5.3333330
    ## 48   2.5000000  3.000000  1249    11      1 2.0000000  4.3333330
    ## 49   3.0000000  3.000000   153    12      1 1.5000000  2.5000000
    ## 50   0.2500000  3.000000   263     2      9 1.8333330  0.0000000
    ## 51   0.0000000  3.000000   939    11      1 0.5000000  1.0000000
    ## 52   0.5000000  3.000000  1287    12      1 0.0000000  0.1666667
    ## 53   0.0000000  3.000000     1     5      1 0.8333334  1.5000000
    ## 54   3.0000000  3.000000  1393     5      1 2.3333330  4.5000000
    ## 55   0.0000000  3.000000  1099    12      1 0.0000000  1.8333330
    ## 56   2.0000000  3.000000   613     2      2 0.5000000  5.5000000
    ## 57   1.0000000  3.000000    49     5      1 0.0000000  1.0000000
    ## 58   0.8333334  3.000000   817    12      1 2.3333330  4.5000000
    ## 59   1.0000000  3.000000  1149    12      2 0.3333333  2.5000000
    ## 60   3.0000000  3.000000  1377    12      1 0.2500000  2.7500000
    ## 61   0.5000000  3.000000  1057    12      2 0.0000000  0.5000000
    ## 62   1.5000000  3.000000  1127     2     10 1.0000000  3.8333330
    ## 63   2.0000000  3.000000   105     2      2 0.5833334  2.9166670
    ## 64   1.2500000  3.000000   753    12      2 0.2500000  1.7500000
    ## 65   0.7500000  3.000000   741    12      2 0.2500000  0.5000000
    ## 66   3.3333330  3.000000  1533    11      1 0.7500000  2.1666670
    ## 67   1.2500000  3.000000    33     2     10 1.2500000  3.2500000
    ## 68   0.0000000  3.000000   555     4      1 0.4166667  1.0000000
    ## 69   2.5000000  3.000000  1417    12      1 2.0000000  4.3333330
    ## 70   0.0000000  3.000000   491     5      1 0.2500000  1.5000000
    ## 71   0.5000000  3.000000   781    12      1 0.5000000  2.1666670
    ## 72   2.5000000  3.000000   649     2      1 3.5000000  7.5000000
    ## 73   1.7500000  3.000000   461     5      1 0.2500000  3.0000000
    ## 74   0.0000000  3.000000   277     2      1 0.5000000  2.5000000
    ## 75   1.5000000  3.000000   765     2      1 0.5833334  2.1666670
    ## 76   1.6666670  3.000000   443     3      1 3.3333330  3.6666670
    ## 77   2.7222220  3.000000  1393    12      1 0.0000000  2.6666670
    ## 78   1.0000000  3.000000   987     5      1 0.8333334  2.5000000
    ## 79   2.3333330  3.000000     1    12      1 2.3333330  4.5000000
    ## 80   0.0000000  3.000000    97     2      4 4.3333330  4.0000000
    ## 81   1.0000000  3.000000  1089     2      6 2.3333330  2.5000000
    ## 82   0.5000000  3.000000  1029    12      1 1.0000000  3.8333330
    ## 83   1.0000000  3.000000  1345     5      1 1.0833330  1.4166670
    ## 84   3.0000000  3.000000  1431     2      1 2.0000000  6.4166670
    ## 85   1.7500000  3.000000   911     3      1 0.0000000  3.6666670
    ## 86   2.3333330  3.000000   483    12      1 2.3333330  4.5000000
    ## 87   3.4166670  3.000000   863     2      1 0.6666667  3.0833330
    ## 88   0.0000000  3.000000   213     2      1 2.5000000  4.5000000
    ## 89   0.7500000  3.000000  1269    12      1 0.7500000  3.0833330
    ## 90   1.0000000  3.000000   945     2      9 1.0000000  5.0000000
    ## 91   0.0000000  3.000000   225     2      9 0.0000000  1.0000000
    ## 92   3.7500000  3.000000     7     2      7 1.5833330  6.5833330
    ## 93   0.5000000  3.000000   485     4      1 0.4166667  1.2500000
    ## 94   1.7500000  3.000000  1799     2      2 1.3333330  4.1666670
    ## 95   0.0000000  3.000000  1065     2      2 0.0000000  1.0000000
    ## 96   1.6666670  3.000000   153    12      1 0.7500000  4.1666670
    ## 97   0.6666667  3.000000   277    12      1 1.0000000  1.2222220
    ## 98   1.5555560  3.000000   701    12      1 0.1111111  2.5555560
    ## 99   0.0000000  3.000000    87     3      1 1.6666670  1.5000000
    ## 100  2.0000000  3.000000  1351     5      1 0.1666667  3.3333330
    ## 101  1.2500000  3.000000  1219    12      1 0.5000000  3.0833330
    ## 102  0.0000000  3.000000  1029     2      5 0.6666667  1.0000000
    ## 103  1.0000000  3.000000   449     4      2 0.0000000  2.0000000
    ## 104  0.8333333  3.000000   909    12      1 0.6111111  1.7777780
    ## 105  1.5555560  3.000000   681    12      1 0.1111111  2.5555560
    ## 106  0.7500000  3.000000   271    12      1 0.7500000  1.7500000
    ## 107  0.0000000  3.000000  1007     2      5 0.0000000  1.0000000
    ## 108  1.0000000  3.000000  1241    12      2 0.2500000  1.7500000
    ## 109  0.0000000  3.000000   345    10      1 0.6666667  1.2500000
    ## 110  0.0000000  3.000000  1047    12      1 4.5000000  2.1666670
    ## 111  0.6666667  3.000000   385     4      1 0.0000000  1.9444440
    ## 112  0.0000000  3.000000   995     5      1 0.0000000  1.0000000
    ## 113  1.0000000  3.000000   503     2      9 1.8611110  2.6111110
    ## 114  0.6666667  3.000000   363     2     10 0.0000000  1.9444440
    ## 115  0.0000000  3.000000  1315     2      6 0.5000000  2.5000000
    ## 116  2.5000000  3.000000   129     5      1 0.0000000  3.5000000
    ## 117  1.1666670  3.000000   533     2      5 4.1666670  4.4166670
    ## 118  0.1666667  3.000000   657    12      1 0.6666667  0.6666667
    ## 119  0.0000000  3.000000  1003     2      5 0.0000000  0.5000000
    ## 120  2.0000000  3.000000   303     2      7 3.6666670  3.7500000
    ## 121  0.6666667  3.000000   251    12      2 0.9166667  1.6666670
    ## 122  0.1666667  3.000000    43    12      1 0.0000000  3.0833330
    ## 123  2.1666670  3.000000   647     2      5 1.7500000  3.5833330
    ## 124  0.7777778  3.000000   391    12      2 0.2777778  1.5555560
    ## 125  0.0000000  3.000000    95     2      9 0.0000000  1.0000000
    ## 126  4.0000000  3.000000   277    12      2 6.5000000  8.0000000
    ## 127  1.8333330  3.000000     1     2      5 0.5000000  2.5000000
    ## 128  0.0000000  3.000000  1035    12      2 2.1666670  2.3333330
    ## 129  1.0000000  3.000000   491     5      1 2.5000000  2.7500000
    ## 130  0.0000000  3.000000   765    12      1 0.0000000  1.0000000
    ## 131  0.0000000  3.000000   383     2      5 1.6666670  1.5000000
    ## 132  1.3333330  3.000000   259    11      1 3.5000000  3.0000000
    ## 133  0.0000000  3.000000   571     2      1 1.0000000  2.3333330
    ## 134  1.0000000 96.750000   995    12      1 0.5000000  2.0000000
    ## 135  1.0000000 21.583330   937     2      1 1.9166670  4.5000000
    ## 136  0.0000000 62.583330  1361    12      2 2.0000000  1.0000000
    ## 137  2.0000000  3.000000   357     5      1 3.5000000  4.0000000
    ## 138  1.2500000 43.666670  1027    12      1 0.6666667  2.0000000
    ## 139  1.3333330 16.166670  1317    12      1 0.0000000  3.3333330
    ## 140  2.5000000 43.666670   165    12      2 3.5000000  4.0000000
    ## 141  2.2500000 61.083330  1255     2      5 3.3333330  3.6666670
    ## 142  0.7777777 69.888890   113    12      2 1.9444440  1.2777780
    ## 143  0.5000000 30.666670    53     2      9 2.0000000  0.5000000
    ## 144  0.0000000 84.166660   757    11      1 2.3333330  0.0000000
    ## 145  5.0000000 43.666670   283    12      2 6.5000000  8.0000000
    ## 146  4.5000000 43.666670   817    12      2 9.0000000  4.5000000
    ## 147  0.0000000 93.250000   347    12      1 3.0000000  0.0000000
    ## 148  0.0000000  1.000000  1551    12      2 1.0000000  0.0000000
    ## 149  1.5000000  5.916667   323     5      2 2.5416670  2.2500000
    ## 150  0.0000000 12.333330    77     4      1 0.3333333  0.0000000
    ## 151  2.7777780 39.444440    29     2      5 3.0000000  1.6666670
    ## 152  0.5000000 93.250000   251     5      2 1.5000000  1.5000000
    ## 153  4.5000000 43.666670   821    12      2 9.0000000  4.5000000
    ## 154  0.7500001 93.500000   783    12      2 2.5000000  1.1666670
    ## 155  0.8333333 33.500000   992     2      4 1.3333330  0.3333333
    ## 156  1.4444450 37.250000   410    11      1 1.8888890  0.3888889
    ## 157  0.0000000  3.000000   355    11      1 0.0000000  2.5000000
    ## 158 10.3333300  3.000000   194     7      1 1.0000000 11.0000000
    ## 159  1.3333330  3.000000   312     2      2 0.0000000  0.2500000
    ## 160  0.0000000  3.000000   475     3      1 0.4166667  0.7500000
    ## 161  0.0000000  3.000000   241     3      1 0.0000000  0.6666667
    ## 162  1.0000000  3.000000   143     2      9 0.6666667  0.7500000
    ## 163  0.7500000  3.000000   703     4      2 0.0000000  1.7500000
    ## 164  0.8333334  3.000000  1169     5      1 2.0000000  2.8333330
    ## 165  2.7500000  3.000000   823     5      1 1.3333330  5.0000000
    ## 166  1.5000000 41.750000   501     5      2 1.7500000  3.2500000
    ## 167  0.7500000 18.958330   717     4      2 1.6250000  1.0000000
    ## 168  0.5000000  3.000000   335     2      9 0.0000000  0.6666667
    ## 169  1.0000000  3.000000   353     2      9 0.0000000  0.0000000
    ## 170  2.0000000  3.000000   175    10      1 0.0000000  0.0000000
    ## 171  6.0000000  3.000000   307     2      9 2.0000000  1.0000000
    ## 172  3.0000000  3.000000     1     3      1 0.0000000  0.0000000
    ## 173  2.0000000  3.000000    17     3      1 2.3333330  4.5000000
    ## 174  0.5000000  3.000000   403     2     10 0.0000000  1.0000000
    ## 175  2.0000000  3.000000   119     2      2 0.0000000  0.7500000
    ## 176  5.0000000  3.000000   477     7      1 5.0000000  4.5000000
    ## 177  1.0000000  3.000000   153    12      1 0.0000000  1.3333330
    ## 178  1.0000000  3.000000    37     5      1 0.0000000  1.0000000
    ## 179 10.3333300  3.000000   219     7      1 1.0000000 11.0000000
    ## 180  0.0000000  3.000000   503     2     10 0.0000000  2.0000000
    ## 181  1.0000000  3.000000   169    11      1 0.8333334  1.0000000
    ## 182  0.0000000  3.000000    27     8      1 0.5000000  0.0000000
    ## 183  3.1666670  3.000000   287     3      1 0.6666667  2.5000000
    ## 184  0.0000000  3.000000   575     2      4 0.0000000  1.5000000
    ## 185  0.7500000  3.000000   289     6      2 0.5000000  5.2500000
    ## 186  1.0000000  3.000000   315    11      1 0.0000000  1.2500000
    ## 187  1.0000000  3.000000     3     3      1 0.1666667  3.3333330
    ## 188  3.5000000  3.000000     3     2      1 2.3333330  7.3333330
    ## 189  0.0000000  3.000000   707     2      5 0.5000000  1.0000000
    ## 190  0.5000000  3.000000   393     5      1 3.0000000  2.5000000
    ## 191  1.0000000  3.000000   647     2      1 3.0000000  3.2500000
    ## 192  1.2500000  3.000000     1     2     10 1.8333330  3.7500000
    ## 193  2.0000000  3.000000   709     2      5 0.0000000  4.3333330
    ## 194  1.4166670  3.000000     1     5      1 1.0000000  2.1666670
    ## 195  2.5000000 43.666670    99    12      2 4.5000000  4.0000000
    ## 196  0.7500000 18.250000   277    12      2 1.7500000  0.0000000
    ## 197  0.0000000  3.000000   306     5      1 0.0000000  0.5000000
    ## 198  0.0000000  3.000000    25     3      1 0.0000000  1.0000000
    ## 199  1.3888890  3.000000    28    13      1 0.3333333  0.7222223
    ## 200  0.0000000  3.000000   141     5      1 0.0000000  0.0000000
    ## 201  0.5000000  3.000000   259     2      1 0.0000000  0.1666667
    ## 202  0.5000000  3.000000   159    15      1 1.0000000  4.3333330
    ## 203  0.0000000  3.000000   174    17      1 0.1666667  0.2500000
    ## 204  0.5000000  3.000000   214     3      1 0.0000000  0.0000000
    ## 205  0.5000000  3.000000   521    12      2 0.0000000  0.2500000
    ##        aulpn70   lcites
    ## 1    0.0000000 4.762174
    ## 2    4.5000000 5.003946
    ## 3    8.0000000 5.135798
    ## 4    3.5000000 5.043425
    ## 5    2.5000000 4.934474
    ## 6    1.5000000 4.682131
    ## 7    4.2500000 5.099866
    ## 8    3.1666670 5.010635
    ## 9    3.0000000 5.888878
    ## 10   1.5000000 4.672829
    ## 11   5.0000000 5.472270
    ## 12   1.0000000 5.351858
    ## 13   3.6666670 4.672829
    ## 14   2.0000000 6.267200
    ## 15   3.5000000 5.141664
    ## 16   4.4166670 4.812184
    ## 17   1.5000000 5.153292
    ## 18   4.5000000 5.826000
    ## 19   4.5000000 4.812184
    ## 20   1.4166670 5.407172
    ## 21   3.6666670 5.123964
    ## 22   7.0000000 5.056246
    ## 23   6.0000000 5.159055
    ## 24   1.0000000 4.663439
    ## 25   2.0000000 5.267858
    ## 26   6.0000000 5.049856
    ## 27   4.5000000 4.762174
    ## 28   0.5000000 5.056246
    ## 29   3.5000000 4.990433
    ## 30   3.0000000 5.247024
    ## 31   3.0000000 4.682131
    ## 32   4.5000000 5.583496
    ## 33   1.7500000 4.644391
    ## 34   6.5000000 4.897840
    ## 35   0.5000000 4.812184
    ## 36   1.5000000 4.762174
    ## 37   2.0000000 5.463832
    ## 38   4.0000000 7.104144
    ## 39   3.9166670 5.283204
    ## 40   0.7500000 5.517453
    ## 41   3.5000000 6.066108
    ## 42   0.5000000 5.438079
    ## 43   1.0000000 5.241747
    ## 44   2.0000000 5.204007
    ## 45   3.1666670 4.682131
    ## 46   0.8333334 5.370638
    ## 47   2.0000000 5.707110
    ## 48   3.5000000 4.905275
    ## 49   4.5000000 7.379008
    ## 50   0.7500000 7.708411
    ## 51   1.0000000 5.505332
    ## 52   1.0000000 5.968708
    ## 53   2.0000000 6.761573
    ## 54   8.5000000 4.672829
    ## 55   0.0000000 4.727388
    ## 56   2.0000000 4.663439
    ## 57   2.0000000 4.948760
    ## 58   0.8333334 7.719130
    ## 59   2.0000000 4.605170
    ## 60   3.5000000 5.402678
    ## 61   0.5000000 6.938284
    ## 62   3.1666670 4.615120
    ## 63   1.5000000 4.852030
    ## 64   2.0000000 4.753590
    ## 65   2.5000000 4.718499
    ## 66   5.3333330 4.820282
    ## 67   1.0000000 5.273000
    ## 68   0.0000000 5.010635
    ## 69   3.5000000 4.624973
    ## 70   0.0000000 4.624973
    ## 71   0.5000000 6.120297
    ## 72   2.0000000 5.361292
    ## 73   3.0000000 5.293305
    ## 74   0.0000000 5.937536
    ## 75   1.2500000 4.709530
    ## 76   1.0000000 5.313206
    ## 77   3.2777780 4.941642
    ## 78   2.5000000 6.981935
    ## 79   0.8333334 6.222576
    ## 80   0.0000000 6.246107
    ## 81   0.5000000 5.852202
    ## 82   0.0000000 6.890609
    ## 83   2.0000000 6.333280
    ## 84   2.0000000 4.997212
    ## 85   3.2500000 5.594711
    ## 86   0.8333334 4.762174
    ## 87   3.2500000 6.308098
    ## 88   0.0000000 5.572154
    ## 89   0.0000000 6.042633
    ## 90   1.0000000 4.812184
    ## 91   0.0000000 5.416101
    ## 92   2.7500000 5.590987
    ## 93   0.0000000 4.779123
    ## 94   1.5000000 4.691348
    ## 95   0.0000000 4.941642
    ## 96   2.2500000 5.220356
    ## 97   1.3333330 5.739793
    ## 98   0.0000000 4.709530
    ## 99   0.0000000 5.501258
    ## 100  0.5000000 4.744932
    ## 101  2.5000000 4.682131
    ## 102  0.0000000 5.209486
    ## 103  1.0000000 4.934474
    ## 104  2.1666670 5.365976
    ## 105  0.0000000 5.062595
    ## 106  2.2500000 5.805135
    ## 107  0.0000000 5.181784
    ## 108  2.0000000 4.663439
    ## 109  0.5000000 4.820282
    ## 110  0.0000000 4.770685
    ## 111  1.0000000 6.100319
    ## 112  4.5000000 5.252274
    ## 113  1.5000000 4.624973
    ## 114  1.0000000 5.509388
    ## 115  0.0000000 5.869297
    ## 116  1.0000000 4.787492
    ## 117  0.5000000 5.743003
    ## 118  1.0000000 4.653960
    ## 119  0.5000000 5.613128
    ## 120  1.0000000 4.990433
    ## 121  1.2500000 7.679714
    ## 122  4.6666670 5.141664
    ## 123  0.0000000 4.912655
    ## 124  1.0000000 5.323010
    ## 125  2.0000000 5.480639
    ## 126  5.5000000 6.315358
    ## 127  1.5000000 5.099866
    ## 128  0.0000000 5.758902
    ## 129  2.2500000 4.700480
    ## 130  0.0000000 4.962845
    ## 131  0.0000000 4.919981
    ## 132  0.2500000 5.416101
    ## 133  3.1666670 5.288267
    ## 134  1.0000000 5.003946
    ## 135  1.0000000 4.836282
    ## 136  0.0000000 6.202536
    ## 137  0.0000000 5.669881
    ## 138  0.0000000 4.779123
    ## 139  1.0000000 4.955827
    ## 140  2.7500000 5.463832
    ## 141  1.0000000 4.736198
    ## 142  0.6666667 5.293305
    ## 143  0.0000000 4.890349
    ## 144  0.0000000 4.948760
    ## 145  5.5000000 5.204007
    ## 146  0.0000000 5.556828
    ## 147  0.0000000 5.365976
    ## 148  0.0000000 6.194406
    ## 149  0.7500000 4.997212
    ## 150  0.0000000 4.828314
    ## 151  0.0000000 5.056246
    ## 152  3.5000000 4.691348
    ## 153  0.0000000 4.779123
    ## 154  0.0000000 4.941642
    ## 155  0.0000000 4.770685
    ## 156  0.0000000 4.828314
    ## 157  1.5000000 5.883322
    ## 158 12.8333300 4.770685
    ## 159  3.1666670 5.087596
    ## 160  1.2500000 4.653960
    ## 161  0.5000000 5.537334
    ## 162  1.5000000 4.700480
    ## 163  0.7500000 4.962845
    ## 164  0.0000000 5.521461
    ## 165  3.0000000 5.062595
    ## 166  1.5000000 4.836282
    ## 167  0.0000000 4.634729
    ## 168  3.1666670 5.556828
    ## 169  5.0000000 5.123964
    ## 170  4.3333330 5.961005
    ## 171  6.0000000 4.653960
    ## 172  3.0000000 5.111988
    ## 173  8.5000000 4.844187
    ## 174  3.0833330 4.875197
    ## 175  1.5000000 5.017280
    ## 176  7.0000000 5.198497
    ## 177  2.5000000 5.062595
    ## 178  4.0000000 5.837730
    ## 179 12.8333300 5.303305
    ## 180  2.0000000 5.068904
    ## 181  2.0000000 5.940171
    ## 182  1.2500000 5.075174
    ## 183  6.5000000 4.875197
    ## 184  1.0000000 4.828314
    ## 185  0.0000000 5.164786
    ## 186  0.2500000 4.718499
    ## 187  0.5000000 4.897840
    ## 188  5.0000000 4.890349
    ## 189  0.0000000 4.700480
    ## 190  0.0000000 5.955837
    ## 191  1.2500000 5.231109
    ## 192  1.4166670 4.844187
    ## 193  0.0000000 4.804021
    ## 194  0.0000000 4.691348
    ## 195  2.7500000 5.361292
    ## 196  0.0000000 4.844187
    ## 197  2.5000000 4.700480
    ## 198  0.0000000 4.875197
    ## 199  3.1111110 6.180017
    ## 200  0.1666667 4.948760
    ## 201  1.9166670 5.869297
    ## 202  7.0000000 5.087596
    ## 203  0.0000000 4.997212
    ## 204  0.5000000 4.948760
    ## 205  1.0000000 4.736198
