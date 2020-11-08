---
layout: post
title:  "Predicting E-Commerce Seller Performance"
author: alexis
categories: [ga-dsi ]
tags: [e-commerce, regression]
image: assets/images/ecommerce-capstone/ecommerce-seller.jpg
description: "Capstone Project for General Assembly's Data Science Immersive"
featured: true
hidden: false
---

Exploratory data analysis and seller performance prediction leveraging a sample of e-commerce data from Brazilian company Olist. 

Read the code on Github [here](https://github.com/alexislimsh/dsiprojects/tree/master/capstone)

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

## Analysis

###  Data Processing and Cleaning

The data was cleaned and processed before analysis could take place. Our data was provided to us in eight separate datasets.

![datasets]({{ site.baseurl }}/assets/images/ecommerce-capstone/datasets-summary.png)

These datasets needed to be joined along unique customer, order and seller ids to create a master order list that could be aggregated.

![joining]({{ site.baseurl }}/assets/images/ecommerce-capstone/datasets-joining.png)

The processing included removing orders that were cancelled or had ambiguous order statuses, as well as feature engineering to create variables for delivery time and difference in delivery estimates.

We also reduced the number of categories by combining similar category groups together.

```python
# Define a dictionary to help with category renaming. 
# Aggregation is done across categories such as construction tools and books.

cat_rename_dict = {
 'agro_industry_and_commerce':'agro_industry_and_commerce' ,
 'air_conditioning': 'air_conditioning',
 'art': 'art',
 'arts_and_craftmanship': 'art',
 'audio': 'audio',
 'auto': 'auto',
 'baby': 'baby',
 'bed_bath_table': 'bed_bath_table',
 'books_general_interest': 'books',
 'books_imported': 'books',
 'books_technical': 'books',
 'cds_dvds_musicals': 'cds_dvds',
 'christmas_supplies': 'party_supplies',
 'cine_photo': 'cine_photo',
 'computers': 'computers',
 'computers_accessories': 'computers_accessories',
 'consoles_games': 'consoles_games',
 'construction_tools_construction': 'construction',
 'construction_tools_lights': 'construction',
 'construction_tools_safety': 'construction',
 'cool_stuff':'cool_stuff',
 'costruction_tools_garden': 'construction',
 'costruction_tools_tools': 'construction',
 'diapers_and_hygiene': 'baby',
 'drinks': 'food_drink',
 'dvds_blu_ray': 'cds_dvds' ,
 'electronics': 'electronics' ,
 'fashio_female_clothing': 'fashion_clothes_accessories',
 'fashion_bags_accessories': 'fashion_clothes_accessories',
 'fashion_childrens_clothes': 'fashion_clothes_accessories',
 'fashion_male_clothing': 'fashion_clothes_accessories',
 'fashion_shoes': 'fashion_shoes',
 'fashion_sport': 'fashion_clothes_accessories',
 'fashion_underwear_beach': 'fashion_clothes_accessories',
 'fixed_telephony': 'fixed_telephony',
 'flowers': 'flowers',
 'food': 'food_drink',
 'food_drink': 'food_drink',
 'furniture_bedroom': 'home_furniture',
 'furniture_decor': 'home_decor',
 'furniture_living_room': 'home_furniture',
 'furniture_mattress_and_upholstery': 'home_furniture',
 'garden_tools': 'garden_tools',
 'health_beauty': 'health_beauty',
 'home_appliances': 'home_appliances',
 'home_appliances_2': 'home_appliances',
 'home_comfort_2': 'home_comfort',
 'home_confort': 'home_comfort',
 'home_construction': 'construction',
 'housewares': 'housewares',
 'industry_commerce_and_business': 'industry_commerce_and_business',
 'kitchen_dining_laundry_garden_furniture': 'home_furniture',
 'la_cuisine': 'housewares',
 'luggage_accessories': 'luggage_travel_accessories',
 'market_place': 'market_place' ,
 'music': 'music' ,
 'musical_instruments': 'musical_instruments' ,
 'office_furniture': 'office_furniture' ,
 'party_supplies': 'party_supplies' ,
 'perfumery': 'perfumery' ,
 'pet_shop': 'pet_shop' ,
 'security_and_services': 'security_and_services' ,
 'signaling_and_security': 'signaling_and_safety',
 'small_appliances': 'small_appliances' ,
 'small_appliances_home_oven_and_coffee': 'small_appliances' ,
 'sports_leisure': 'sports_leisure',
 'stationery': 'stationery',
 'tablets_printing_image': 'tablets_printing_image',
 'telephony': 'telephony',
 'toys': 'toys',
 'watches_gifts': 'watches_gifts'
}

order_items_master['product_category_name'] = order_items_master['product_category_name'].map(cat_rename_dict)
```

Using the new categories, we are able to see which categories have the highest mean sale prices, total sale orders, total sales value and number of unique products per category. These plots have been combined in the interactive plot here:

{% include posts/product-agg.html %}

Aggregation was also done across sellers to check the most valuable categories to a seller by category.

{% include posts/sellers-agg.html %}

{% include posts/order-values-map.html %}

## Conclusion and Insights

![predictions]({{site.baseurl}}/assets/images/ecommerce-capstone/prediction.png)

We were able to build a predictive model for predicting seller performance with around R$200 of root mean squared error and an adjusted R2 score of 0.93. However, as the data is not completely comprehensive, the model will require additional training on more data to be sufficiently robust and to evaluate its reproducibility.

The model predicts seller performances by taking in the following information:

- Product Category
- State
- Min, Max, Average Product Price
- Number of Products they can sell in a month
- Number of Unique Products

Average products they can sell in a month turned out to be the most predictive factor, along with the minimum, maximum and average product prices. With more data and potentially more inputs from the seller like the size of their company, length of seller relationship to Olist, we may want to also try predicting optimal product volume that can be sold instead, in the long run.

The web app based on the final model is <a href="https://ecommerce-seller-prediction.herokuapp.com/" target="_blank">deployed on Heroku.</a>