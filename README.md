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
7. [Calculating the experiment size](#sizing)
8. [Evaluating the experiment results](#evaluation)

## Introduction <a name="business_understanding"></a>
A software company is looking for ways to increase the purchase rate of their product. Currently, there is a 7-day trial where users can use the software for free. After these seven days the user would need to pay for a license to further use the application. One suggestion to archieve this is to upgrade the homepage by emphasizing the 7-day-trial advertisement more prominently, so that there is a lower chance that visitors of the webpage are overlooking this option.

## Objectives <a name="objectives"></a>
The goal of this case study is to analyze if the webpage upgrade has enough impact and statistical significance to call a success.

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
