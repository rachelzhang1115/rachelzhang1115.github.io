---
layout: post
title: What is the Financial Value of Public Schools? -- A Spatial Discontinuity Design & Causal Inferences
author: Rachel Zhang
mathjax: true
---


Public education is free in the U.S. But the question we are asking today is: are parents willing to pay more for good public education? We also know that school funding usually comes from property taxes, so how about we assess parents' willingness to pay through house prices?

In most of the cases, good schools are located in good neighborhoods. Both good schools and good neighborhoods could contribute to higher house prices. Given that house prices can be affected by many factors such as house characteristics \(number of bedrooms, bathrooms, square footage, lot size, etc.\), public school ratings, and "niceness" of neighborhoods, if we use the common approach of running a linear regression without any neighborhood features, we could only pick up the correlation, but not the isolated and direct relationship, which we usually call **Causality**, between school ratings and house prices \(For a more detailed Economteric explanation on the regression, please refer to the Appendix\). 

I propose a novel approach to capture the neighborhood effects in our regression. The following graph is an example of two elementary school districts in the city of San Jose, they share a boundary in the middle.
![an image alt text]({{ site.baseurl }}/images/school1.png "an image title")


## Appendix ##
Running a linear regression in the following format:

$$HousePrice_{isb}=\alpha+\beta*X_{isb} +\gamma*SchoolRating_{is}+\epsilon_{isb}$$

where $HousePrice_{isb}$ is the target, $X_{isb}$ captures all household characteristics such as number of bedrooms, bathrooms, square footage, lot size, etc., and $SchoolRating_{is}$ is the assigned elementary school's rating. Since we don't have any features that capture the neighborhood effects in this regression, its effect will be captured by the error term $\epsilon_{isb}$. Thus the error term is both correlated with the target $HousePrice_{isb}$ and one of the features $SchoolRating_{is}$ in our regression, and our regression coefficient $\gamma$ suffers from omitted variable bias, and cannot be interpreted as the causal effect of school rating on house prices.

