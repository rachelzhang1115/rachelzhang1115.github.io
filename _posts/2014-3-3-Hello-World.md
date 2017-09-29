---
layout: post
title: What is the Financial Value of Public Schools? -- A Spatial Discontinuity Design & Causal Inferences
author: Rachel Zhang
use_math: true
---


Public education is free in the U.S. But the question we are asking today is: are parents willing to pay more for good public education? We also know that school funding usually comes from property taxes, so how about we assess parents' willingness to pay through house prices?

In most of the cases, good schools are located in good neighborhoods. Both good schools and good neighborhoods could contribute to higher house prices. Given that house prices can be affected by many factors such as house characteristics \(number of bedrooms, bathrooms, square footage, lot size, etc \), public school ratings, and "niceness" of neighborhoods, if we use the common approach of running a linear regression without any neighborhood features, we could only pick up the correlation, but not the isolated and direct relationship, which we usually call **Causality** between school ratings and house prices \(For a more detailed Economteric explanation on the regression, please refer to the Appendix \). 

In order to capture the neighborhood effects, I propose a novel approach demonstrated below:

This is an example of two elementary school districts in the city of San Jose:


## Appendix ##
(i.e. running a regression in this form: $HousePrice_{isb}=\alpha+\beta*X_{isb} +\gamma*SchoolRating_{s}+\epsilon_{isb}$)
then the coefficient of interest here \gamma
