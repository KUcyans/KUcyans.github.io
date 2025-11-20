---
layout: post
title: Chi-square method
date: 2025-01-01
permalink: /posts/chi_square/
cover: /assets/img/chi_square.png
---


# Modelling
Say we have a data scattered in $xy$ plane, where each point has some measurement uncertainty, and the errors in $y$ are assumed to be Gaussian. How will you describe the distribution of this data? Finding statistical values – such as median, mean or standard deviation – must be the first step to take. Additional quantiles such as quartiles, deciles or percentiles may also help to understand the distribution better. Ok but what if the distribution of the data doesn't resemble any known nicely peaked distributions? Or if I want to illustrate the data more formally?

This is where modelling comes in: we introduce a hypothesis for the relationship between $x$ and $y$. Only once we have a model does it make sense to quantify how well it fits the data.

# Chi-square fitting
We have a nice and straightforward method of modelling: $\chi^2$-square fitting. It's arguably the most intuitive method to fit a model to data. Eventually you will have a model, with some parameters, and perhaps how nicely does your model fit the data. But you need to have a your opinion: a hypothesis. You should have an idea of what kind of distribution your data should follow. Is it linear, quadratic, exponential, Gaussian, sinusoidal or something else?

Say I chose a linear model to fit my data. Then the relation between $x$ and $y$ is something like this:
![Linear Data](/posts/assets/img/chi_square_data1.png)**Figure 1**: Example of linear data with error bars

$$ y = ax + b $$

where $a$ and $b$ are the parameters to be determined. Once you have your model, you can calculate the expected value of $y$ for each $x$ (thus $ax+b$). Then you can compare the expected value with the observed value. The difference between the two is called the residual. The $\chi^2$ sum is calculated as follows:

$$ \chi^2 = \sum_{i=1}^{n} \frac{(y_i - \hat{y}_i)^2}{\sigma_i^2} $$

where $n$ is the number of data points, $y_i$ is the observed value, $\hat{y}_i$ is the expected value, and $\sigma_i$ is the standard deviation (error) of the observed value. The $\chi^2$ sum is a square sum of the residuals. The smaller the $\chi^2$ sum, the better the fit. So you can try different $a$s and $b$s to find the minimum $\chi^2$ sum. The values of $a$ and $b$ that give the minimum $\chi^2$ sum are the best-fit parameters.
Simple theory isn't it?

![Linear Data](/posts/assets/img/chi_square_data2.png)**Figure 2**: Example of chi-square fitting of linear data with Gaussian noise

---

## ¡Caution!
But there is an important caveat! The $\chi^2$ is only valid if the error distribution is Gaussian and the uncertainties $\sigma_i$ are known or at least well-estimated. If this premise is not satisfied, the $\chi^2$ fitting may lead to misleading results.
$$
y_i = \hat{y}_i(x_i; a, b) + \epsilon_i\\
\epsilon_i \sim N(0, \sigma_i^2)
$$

---

# Goodness of fit
Now we found the best-fit parameters that minimise the $\chi^2$ sum. How do we know if the fit is good enough? We have to do hypothesis testing. The null hypothesis is that the model is a good fit to the data. For this, we need to find the degrees of freedom (dof) first. The degrees of freedom is defined as the number of data points minus the number of fitted parameters. In our linear model example, we have two fitted parameters ($a$ and $b$), so the degrees of freedom is $n - 2$.

If we normalise the $\chi^2$ sum by the degrees of freedom, we get the reduced chi-square:

$$\chi^2_{red} = \frac{\chi^2}{dof}$$

The reduced chi-square should be approximately 1 if the model is a good fit to the data. If $\chi^2_{red} \gg 1$, it indicates that the model does not fit the data well, or that the uncertainties are underestimated. Conversely, if $\chi^2_{red} \ll 1$, it suggests that the model may be overfitting the data, or that the uncertainties are overestimated. 

If your model is correct and the errors are Gaussian, then the (properly normalised) residuals follow a standard normal distribution. The sum of their squares therefore follows a distribution known as $\chi^2$ distribution. Each integer value of the degrees of freedom corresponds to a different $\chi^2$ distribution. 

# p-value
![Linear Data](/posts/assets/img/chi_square_data3.png)**Figure 3**: chi-square distribution for different degrees of freedom

The calculated residual $\chi^2_{red}$ sum can be compared to the $\chi^2$ distribution with the corresponding degrees of freedom. From this comparison, we can calculate the p-value. This p-value represents the probability of obtaining a $\chi^2$ value as extreme as, or more extreme than, the observed value, assuming the null hypothesis is true.

A low p-value (typically less than 0.05) indicates that the null hypothesis can be rejected, suggesting that the model does not fit the data well. Conversely, a high p-value suggests that there is insufficient evidence to reject the null hypothesis, indicating that the model may be a good fit for the data./