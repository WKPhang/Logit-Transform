# What is logit transform?

## Purpose
For transformation of proportion value in the range (0,1) into continuous value in the range (‑∞,∞).

## Description
Proportion (denoted as *p*) may, for example, be used as an outcome measure when we want to examine the prevalence of a disease at a given point in time. The fact that the range of proportion is restricted between 0 and 1 can be problematic. When *p* is close to 0 or close to 1, the standard error is artificially compressed, which leads us to overestimate the precision of the proportion estimate.

Additionally, distribution of *p* will be right-skewed or left-skewed because it is impossible for a random sample to have a calculated proportion outside the 0 to 1 range. This would limit the analysis which required normally distributed data. To avoid this, proportions are commonly logit-transformed. Besides, the Logit transform is often used to correct sigmoid (logistic) relationships between response and explanatory variables.

A logit-transformation first involves calculating the odds. Odds are defined as the proportion of participants which fall into a specific category, divided by the proportion of units which do not fall into that category. The natural logarithm function  is then used to transform the odds into a format where *p* = 0.5 equals a value of 0, and where there is no range restriction. This ensures that the sampling distribution is approximately normal and that standard errors are not biased. The calculation of logit-transformed proportions and their standard errors can be done using these formula.

$$
p_{\text{logit}} = ln \frac{p}{(1-p)}  ,  p\in[0,1]
$$

$$
SE_{p_{\text{logit}}} = \sqrt{\frac{1}{np}+\frac{1}{n(1-p)}}
$$

### Scripts
```
import numpy as np
import matplotlib.pyplot as plt

# Define the logit function
def logit(x):
    return np.log(x / (1 - x))

# Generate x values from 0.001 to 0.999 to avoid division by zero
x = np.linspace(0.001, 0.999, 1000)
y = logit(x)

# Plot the logit curve
plt.figure(figsize=(8, 6))
plt.plot(x, y, label='logit(x)', color='blue')
plt.xlabel('x')
plt.ylabel('ln(x / (1 - x))')
plt.title('Logit Curve')
plt.axhline(0, color='black',linewidth=0.5)
plt.axvline(0, color='black',linewidth=0.5)
plt.grid(True, linestyle='--', linewidth=0.5)
plt.legend()
plt.show()
```

## Inverse transform
An inverse transform of the logit-transformed *p* will produce sigmoid logistic curve and it can be expressed as below.

$$
p = \frac{e^{p_{\text{logit}}}}{1+e^{p_{\text{logit}}} }
$$

```
# Define the logistic function
def logistic(x):
    return 1 / (1 + np.exp(-x))

# Generate x values
z = logistic(y)

# Plot the logistic curve
plt.figure(figsize=(8, 6))
plt.plot(x, y, label='logistic(x)', color='blue')
plt.xlabel('x')
plt.ylabel('1 / (1 + exp(-x))')
plt.title('Logistic Curve')
plt.axhline(0, color='black', linewidth=0.5)
plt.axvline(0, color='black', linewidth=0.5)
plt.grid(True, linestyle='--', linewidth=0.5)
plt.legend()
plt.show()
```
