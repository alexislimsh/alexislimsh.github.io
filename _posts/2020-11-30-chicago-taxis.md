---
layout: post
title:  "Fares and Routes of Chicago Public Taxis (2019-2020)"
author: alexis
categories: [personal]
tags: [transport, tableau]
image: assets/images/taxi-hero.jpg
description: "Route Analysis for Chicago's Public Taxis"
featured: true
hidden: false
---

Exploratory data analysis and Tableau visualisation of Chicago public taxis data, obtained from Google BigQuery.

View and download the workbook on Tableau [here](https://public.tableau.com/shared/RY887TZ4Y?:display_count=y&:origin=viz_share_link)

# Chicago Public Taxi Data (2019-2020)

## Summary

Using Google BigQuery's dataset of Chicago's public taxi trips, we examine all trips taken in 2019 and 2020 to determine trends in fares and routes based on pickup locations. 

We see a drastic drop in taxi trips from March onwards, corresponding to the pandemic's effect in the U.S. and in Chicago in particular. As positive news of successful vaccines have emerged in the past month, we should anticipate a return to normalcy and determine which pickup points and routes taxi drivers should prioritise when the U.S. makes its return to recovery.

## Approach

### 1. Data Processing and Cleaning

As the full dataset on BigQuery is around 70GB of data spanning several years, filtering and cleaning was done to obtain the data from 2019 onwards. Rows with null values for all location features were filtered out, whilst rows with obviously inaccurate values e.g. (>$1,000 for a trip of 0.0 miles) were also removed.

Overall, the data covered records for approximately 1.4M trips taken across the two years, with data from 5.2K taxis and 59 taxi companies.

### 2. Visualisation Techniques on Tableau

Tableau Public was leveraged for this analysis. We applied parameter filtering to allow for user interaction with the graphs, where users can select which parameter they are interested in e.g. total trips, sum of fares, sum of tips and see which location has the highest metrics for each. 

We also leveraged on route analysis using Tableau's path visualisations to chart out all routes from each pickup point and evaluate which are the most popular routes.

### 3. Tableau Story & Insights

{% include posts/chicago-taxis-tableau.html %}

View and download the workbook on Tableau [here](https://public.tableau.com/shared/RY887TZ4Y?:display_count=y&:origin=viz_share_link)
