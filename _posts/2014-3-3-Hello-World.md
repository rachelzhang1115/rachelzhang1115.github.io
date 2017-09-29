---
layout: post
title: What is the Financial Value of Public Schools? -- A Spatial Discontinuity Design & Causal Inferences
author: Rachel Zhang
mathjax: true
comments: true
---


Public education is free in the U.S. But the question we are asking today is: are parents willing to pay more for good public education? We also know that school funding usually comes from property taxes, so how about we assess parents' willingness to pay through house prices?

In most of the cases, good schools are located in good neighborhoods. Both good schools and good neighborhoods could contribute to higher house prices. Given that house prices can be affected by many factors such as house characteristics \(number of bedrooms, bathrooms, square footage, lot size, etc.\), public school ratings, and "niceness" of neighborhoods, if we use the common approach of running a linear regression without any neighborhood features, we could only pick up the correlation, but not the isolated and direct relationship, which we usually call **Causality**, between school ratings and house prices \(For a more detailed Economteric explanation on the regression, please refer to the Appendix\). 

## A Novel Approach ##
I propose a novel approach to capture the neighborhood effects in our regression.The following graph is an example of two elementary school districts in the city of San Jose, they share a boundary in the middle.
![](/images/school1.png)

The grey dots are recently sold houses within the past 1.5 years within these two school districts.
![](/images/school2.png)

The yellow shaded region incudes areas that are within 0.35 miles away from the school district boundary.
![](/images/school3.png)

If we only look at houses that are within this region, we could say that these houses share similar neighborhood characteristics.
![](/images/school4.png)

The following picture is an example of the city of San Jose with all its elementary school districts and the houses that are located within 0.35 miles away from the boundaries.
![](/images/school5.png)

While this picture here demonstrates the locations of a 68,000 houses I scraped from Zillow, and 854 elementary school districts I scraped from GreatSchools.org in the Bay Area.
![](/images/shcool6.png)

I used Python's Geopandas Shapely library to perform geometric manipulations in order to allocate thousands of houses onto hundreds of school boundaries, and visualized this entire process using Geopandas geometric plotting tools.

## Results ##
After successfully allocating and selecting houses within 0.35 miles from the school district boundaries, I was able to run a Regression Discontinuity Model on the sampled data \( Refer to Appendix for a detailed explanation on the Regression Discontinuity Model\). The major result I got from my model includes: if elementary school rating increases by 1 unit, it causes average house prices to increase by 1.7%. Given the average housing price in the Bay Area to be close to \\$1 million, this is an increase of \\$17,000 in property values. 

The result has several implications: given a 1 point increase in elementary school rating
1. Parents are willing to pay \$17,000 more for their kids to go to that better school
2. Property owners can expect an increase of \$17,000 in their property values
3. For policy makers, taking the city of San Jose as an example: there are a total of 313,000 housing units in the city, multiplied by the marginal increase of \\\$17,000 in house prices, then multiplied by the property tax rate of \0.95, the San Jose government should expect an increase in property tax of about \\\$50 million. Due to the complicated nature of the California Property Tax, this number is just an estimate of the true effect of a 1 point increase in elementary school rating on tax revenues. However, the magnitude of this number conveys a clear story: investing in public education is not only beneficial for the well-being of our next generations, it also generates tax revenues that could potentially cover the investment itself.

## Next Steps ##
There are several options I'd like to explore as I progress into this project further. 
1. Remove all boundaries that are major railways, highways, parks, rivers, etc as these boundaries may define distinct neighborhoods.
2. Decrease the distance from the boundaries when selecting houses into my sample. Currently, I have the distance set to be 0.35 miles, when I further decrease this distance, selected houses are closer to each other, and thus the neighborhood characteristics will be more similar. If the results stay stable, then our coefficient is capturing the true causal effect between school rating and house prices, not the progression of neighborhoods.


## Econometrics Appendix ##
Running a linear regression in the following format:

$$HousePrice_{isb}=\alpha+\beta*X_{isb} +\gamma*SchoolRating_{is}+\epsilon_{isb}$$

where $HousePrice_{isb}$ is the target, $X_{isb}$ captures all household characteristics such as number of bedrooms, bathrooms, square footage, lot size, etc., and $SchoolRating_{is}$ is the assigned elementary school's rating. Since we don't have any features that capture the neighborhood effects in this regression, its effect will be captured by the error term $\epsilon_{isb}$. Thus the error term is both correlated with the target $HousePrice_{isb}$ and one of the features $SchoolRating_{is}$ in our regression, and our regression coefficient $\gamma$ suffers from omitted variable bias, and cannot be interpreted as the causal effect of school rating on house prices.

However, houses located on either side within 0.35 miles from the school district boundaries actually share similar neighborhood characteristics. So the neighborhood effect progresses smoothly across the boundaries. Given this asuumption, we could run the following regression with boundary Fixed Effects, which would enable us to draw causal inferences from the coefficient $\gamma$:
$$HousePrice_{isb}=\alpha+\beta*X_{isb} +\gamma*SchoolRating_{is}+\Psi_{ib}+\epsilon_{isb}$$

## Comments? ##
I'd appreciate any comments on how I could carry the project further :smile:



