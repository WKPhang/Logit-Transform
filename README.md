# What is logit transform?

## Purpose
To transform a proportion value in the range (0,1) into a continuous value in the range (‑∞,∞)

## Description
Proportion (denoted as *p*) may, for example, be used as an outcome measure when we want to examine the prevalence of a disease at a given point in time. The fact that the range of proportion is restricted between 0 and 1 can be problematic. When *p* is close to 0 or close to 1, the standard error is artificially compressed, which leads us to overestimate the precision of the proportion estimate.

Additionally, distribution of *p* will be right-skewed or left-skewed because it is impossible for a random sample to have a calculated proportion outside the 0 to 1 range. This would limit the analysis which required normally distributed data. To avoid this, proportions are commonly logit-transformed. Besides, the Logit transform is often used to correct sigmoid (logistic) relationships between response and explanatory variables.

A logit-transformation first involves calculating the odds. Odds are defined as the proportion of participants which fall into a specific category, divided by the proportion of units which do not fall into that category. The natural logarithm function  is then used to transform the odds into a format where *p* = 0.5 equals a value of 0, and where the transformed values have no range restriction as illustrated in Figure 1. This ensures that the sampling distribution is approximately normal and that standard errors are not biased. The calculation of logit-transformed proportions and their standard errors can be done using these formula.

$$
p_{\text{logit}} = ln \frac{p}{(1-p)}  ,  p\in(0,1)
$$

$$
SE_{p_{\text{logit}}} = \sqrt{\frac{1}{np}+\frac{1}{n(1-p)}}
$$

Where,

*p* is proportion

$$*p_logit*$$ is logit-transformed proportion

*n* is sample size

$*SE_p_logit*$ is standard error of $*p_logit*$

<div align="center">
<img src="https://github.com/WKPhang/Logit-Transform/blob/main/assets/Figure%201.png"/>
<p><b>Figure 1:</b> Graph of logit-transformed proportion data.</p>
</div>


## Inverse transform
An inverse transform of the logit-transformed *p* will produce sigmoid logistic curve (Figure 2) and it can be expressed as below.

$$
*p* = \frac{e^{*p_{\text{logit}}*}}{1+e^{*p_{\text{logit}}*} }
$$

<div align="center">
<img src="https://github.com/WKPhang/Logit-Transform/blob/main/assets/Figure%202.png"/>
<p><b>Figure 2:</b> Graph of inverse transform of the logit-transformed *p*.</p>
</div>

## Logit-transformation of skewed data

Lets illustrate the transformation of right-skewed proportion data using a logit function. Here, I generated a proportion data with a right-skewed distribution (Figure 3). This is often encountered when the proportions are close to 0 or 1. By applying a logit transformation, it symmetrize and normalize the distribution of the skewed data, making it more suitable for statistical analysis (Figure 4). Figure 5 represents the relationship between the original proportion values and their logit-transformed counterparts, emphasizing how the transformation moderates the extreme proportions towards a more linear distribution

<div align="center">
<img src="https://github.com/WKPhang/Logit-Transform/blob/main/assets/Figure%203.png"/>
<p><b>Figure 3:</b> Histogram of right-skewed proportion data.</p>
</div>

<div align="center">
<img src="https://github.com/WKPhang/Logit-Transform/blob/main/assets/Figure%204.png"/>
<p><b>Figure 4:</b> Histogram of logit-transformed right-skewed proportion data.</p>
</div>

<div align="center">
<img src="https://github.com/WKPhang/Logit-Transform/blob/main/assets/Figure%205.png"/>
<p><b>Figure 5:</b> Logit curve of right-skewed proportion data.</p>
</div>
