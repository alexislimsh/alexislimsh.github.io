---
layout: post
title:  "Predicting E-Commerce Seller Performance"
author: alexis
categories: [ga-dsi ]
tags: [e-commerce, regression]
image: assets/images/ecommerce-capstone/ecommerce-seller.jpg
description: "Capstone Project for General Assembly's Data Science Immersive"
featured: true
hidden: true
---

Exploratory data analysis and seller performance prediction leveraging a sample of e-commerce data from Brazilian company Olist. 

[Github Link](https://github.com/alexislimsh/dsiprojects/tree/master/capstone)

# E-Commerce Seller Performance Prediction

### <a href="https://ecommerce-seller-prediction.herokuapp.com/" target="_blank">Deployed Model</a>


## Summary

We take on a role of a team of data scientists at Olist, an online e-commerce company that connects small businesses from all over Brazil to large online e-commerce marketplaces such as [Mercado Livre](https://www.mercadolivre.com.br/) and [Americanas](https://www.americanas.com.br/).

By listing their products on Olist Store, small business owners are able to sell their products to customers on these marketplaces without the prohibitive costs of maintaining a vendor presence there.

The project focused on how we can use sample e-commerce data to increase the number of sellers and provide recommendations to them. 

The final model predicts seller performance based on seller and product features, where the decision tree-based Random Forest algorithm was leveraged. 

Translation, word tokenization and topic modeling was also performed on the dataset of Portuguese reviews.

## Problem Statement
Based on the data we've gathered from the sales and reviews on the platform, we have been tasked to estimate the sales that a seller can get based on factors such as their product category, average product price and location.

Additionally, we also want to take a look at the reviews to give potential sellers advice on how to increase customer satisfaction.

Our guiding questions are:
- How much can a seller expect to earn on the platform?
- What steps can a seller take to increase their sales?
- What are the prominent topics that feature in our customer reviews?

## Conclusion and Insights

![dataset](assets/images/ecommerce-capstone/ecommerce-seller/prediction.png)

We were able to build a predictive model for predicting seller performance with around R$200 of root mean squared error and an adjusted R2 score of 0.93. However, as the data is not completely comprehensive, the model will require additional training on more data to be sufficiently robust and to evaluate its reproducibility.

The model predicts seller performances by taking in the following information:

- Product Category
- State
- Min, Max, Average Product Price
- Number of Products they can sell in a month
- Number of Unique Products

Average products they can sell in a month turned out to be the most predictive factor, along with the minimum, maximum and average product prices. With more data and potentially more inputs from the seller like the size of their company, length of seller relationship to Olist, we may want to also try predicting optimal product volume that can be sold instead, in the long run.

The web app based on the final model is <a href="https://ecommerce-seller-prediction.herokuapp.com/" target="_blank">deployed on Heroku.</a>