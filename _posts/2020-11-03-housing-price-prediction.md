---
layout: post
title:  "Predicting House Sale Prices in Boston"
author: alexis
categories: [ ga-dsi ]
tags: [regression]
image: assets/images/housing-boston-prediction/housing-hero.jpg
---

Based on the Boston, Ames housing dataset, I predicted sale price by shortlisting top explanatory variables from over 80 categorical, ordinal, discrete and continuous variables using correlation.

Read the code on Github [here](https://github.com/alexislimsh/dsiprojects/tree/master/dsi-16-project-2)

# Model Prediction of Housing Sale Price

## Executive Summary

When it comes to housing prices, we often have access to extensive past data around housing features and the eventual sale price. Being able to predict future sale prices within a reasonable margin would be incredibly useful to many stakeholders, including housing agents, governing bodies and even residents themselves.

In this project, we process the Ames train and test datasets obtained via the [Kaggle competition](https://www.kaggle.com/c/dsi-us-6-project-2-regression-challenge) hosted by General Assembly to find a robust model based on 25-30 variables for prediction of house sale price. We look at which features affect sale price the most through data cleaning and exploratory data analysis, and build and refine our model using various regression techniques.

The data documentation for the original dataset can be viewed [here](http://jse.amstat.org/v19n3/decock/DataDocumentation.txt).

## Problem Statement

What features of a house contribute most significantly to its eventual sale price, and with knowledge of these features, how can we predict future sale price? Can the model that we build be generalised to other cities, states and countries?

We approach the problem statement from the POV of a team of housing agents in Ames, Iowa, as it’s likely that agents will have access to this level of detail about a property. Having a model will help agents to consistently valuate properties and negotiate better between buyers and sellers. If successful, this model could also then be marketed to both governing bodies and housing agents who would be interested in such a tool.

## Conclusion & Recommendations

We have successfully built a model with a relatively good RMSE based on the training dataset provided, and our examination has indicated that while the top influencing factor appears to be area (total square feet of the house and individual areas), variables across different aspects of the house were also picked out by the model to be significant.

*Recommendations*

### Recommendations

If we had additional time and resources, we may want to consider the following to improve on and continually iterate on our model:

- The frequency distribution of the log of sale prices follows a normal distribution. By building our linear regression model with the log of sale prices, we can better fit and predict the sale prices of houses in the higher price range.

- For features with many different categories, we can combine and regroup them so that each category becomes more significant. For eg: Neighborhood has 28 categories, we can regroup them into 5 categories based on their mean sale prices.

- We can also look into other external factors affecting housing prices like economic factors and demographic data of the community.

While we see that the model built has limitations, it is also true that the process of putting together the model is informative and a similar process can be conducted for other datasets in other cities or with different variables collected. Our process is as follows:

- Clean and process data
- Exploratory data analysis
- Feature engineering
- Feature selection (by judgement and RFE and lasso techniques)
- Model iteration and optimisation

The last step should be ongoing if there is a stream of new data. Any model will have its limitations, but with the right set of assumptions and understanding of suitable use cases, we're able to predict meaningfully.