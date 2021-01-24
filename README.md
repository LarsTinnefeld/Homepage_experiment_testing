# A/B Testing Case Study: Homepage Experiment
**A test process to analyze the impact of an experiment.**

By Lars Tinnefeld, 2021-01-23

![Gauss](https://cdn.pixabay.com/photo/2020/04/11/10/05/chart-5029714_960_720.png)

*Image by [Maky Orel](https://pixabay.com/users/maky_orel-436253/) on Pixabay*

## Table of content
1. [Inroduction](#business_understanding)
2. [Objectives](#objectives)
3. [Data](#data)
4. [Building a funnel](#funnel)
6. [Deciding on metrics](#metrics)
7. [Invariant Metrics](#invariance)
8. [Calculating the sample size](#sizing)
9. [Evaluating the experiment results](#evaluation)

## Introduction <a name="business_understanding"></a>
A software company is looking for ways to increase the purchase rate of their product. Currently, there is a 7-day trial where users can use the software for free. After these seven days the user would need to pay for a license to further use the application. One suggestion to archieve this is to upgrade the homepage by emphasizing the 7-day-trial advertisement more prominently, so that there is a lower chance that visitors of the webpage are overlooking this option.

## Objectives <a name="objectives"></a>
One objective is to estimate how long the sample gathering must be in order to have enough sample sizes to validate the test results. The other goal of this case study is to analyze if the webpage upgrade has enough impact and statistical significance to call a success and therefore deploy the change.

## Data <a name="data"></a>
The data were provided by Udacity.
| Field | Dtype | Records | Description |
| --- | --- | --- | --- |
| Day | int64 | 29 non-null | Day of data collection period |
| Control Cookies | int64 | 29 non-null | Collected Cookies at unchanged webpage |
| Control Downloads	 | int64 | 29 non-null | Software downloads through unchanged webpage |
| Control Licenses	 | int64 | 29 non-null | License purchases through unchanged webpage |
| Experiment  Cookies | int64 | 29 non-null | Collected Cookies at new webpage |
| Experiment  Downloads	 | int64 | 29 non-null | Software downloads through new webpage |
| Experiment  Licenses	 | int64 | 29 non-null | License purchases through new webpage |

## Building a funnel <a name="funnel"></a>
The expected steps a typical user takes from inital visit to a license purchase:
- Visit homepage
- Visit download page
- Sign up for an account
- Download software
- After 7-day trial, software takes user to license-purchase page
- Purchase license

## Deciding on metrics <a name="metrics"></a>
The metrics to base the statistical evaluation on are:
- Number of cookies that hit the homepage (one for each visitor)
- Number of downloads of the software
- Number of sold licenses

For the A/B testing rates were introduced:
- Download rate = Number of downloads / Number of cookies
- License purchase rate = Number of licenses / Number of cookies

These rates were generated for the experiment- and control group.

## Invariance metrics <a name="invariance"></a>
A dataset which contains many more instances of the positive target group of the negative instances (or vice versa) will potentially lead to wrong results in the analysis. This is why a check is performed.

Visual check:
![Distribution_chart](https://github.com/LarsTinnefeld/Homepage_experiment_testing/blob/main/Dist_bar.png?raw=true)

Statistical validation:
![Invariant_metric](https://github.com/LarsTinnefeld/Homepage_experiment_testing/blob/main/Inv_metr_code.PNG?raw=true)

Sample is balanced enough to perform the analysis.

## Calculating the sample size <a name="sizing"></a>
- Visitors per day: 3250
- Current downloads per day: 520
- Current licenses per day: 65

- Target downloads per day: 570
- Target licenses per day: 75

- Type I error rate: 0.05
- With Bonferroni correction: 0.025
- Power: 80% (Type II error: 20%)

Sample size based on download rate: 6 days (5.55)
Sample size based on license purchase rate: 21 days (21.44)

## Evaluating the experiment results <a name="evaluation"></a>

![Download_rate](https://github.com/LarsTinnefeld/Homepage_experiment_testing/blob/main/Downl_sample.PNG?raw=true)

![License_rate](https://github.com/LarsTinnefeld/Homepage_experiment_testing/blob/main/License_sample.PNG?raw=true)
