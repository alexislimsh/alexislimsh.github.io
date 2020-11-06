---
layout: post
title:  "Prosocial and Antisocial LifeProTips on Reddit"
author: alexis
categories: [ ga-dsi ]
tags: [nlp, classification]
image: assets/images/lifeprotips/lpt-hero.jpg
featured: true
hidden: true
---

Natural language processing project delving into the subreddit r/LifeProTips and r/UnethicalLifeProTips.

Read the code on Github [here](https://github.com/alexislimsh/dsiprojects/tree/master/dsi-16-project-3)

# NLP and API with Reddit

## Summary

The [LifeProTips subreddit](https://www.reddit.com/r/LifeProTips/) is one of the most popular subreddits in Reddit with over 18.4M members, offering advice, hacks and tips on different aspects of life (family, work, hobbies etc.). It also has multiple offshoots including [UnethicalLifeProTips](https://www.reddit.com/r/UnethicalLifeProTips/), [IllegalLifeProTips](https://www.reddit.com/r/IllegalLifeProTips/) and a satire subreddit [ShittyLifeProTips](https://www.reddit.com/r/ShittyLifeProTips/).

In this project, we want to investigate the differences between LifeProTips and UnethicalLifeProTips. In their own words, the respective definitions are:
- LPT: Tip that improves your life in one way or another.
- ULPT: Tip that improves your life in a meaningful way, perhaps at the expense of others and/or with questionable legality.

## Problem Statement

By building a classification model for the two subreddits, we want to see if we can accurately predict posts for the two subreddits as well as investigate the following:
- We can understand what 'unethical' is defined as by society (using the Reddit community as a proxy).
- We can identify if the tips submitted to each subreddit are significantly different in any way, even though both purport to 'improve lives'.
- As the definition provided by the ULPT subreddit describes anti-social behaviour, we can also seek to understand what constitutes anti-social behaviour.

## Conclusion & Recommendations

Based on our investigations and model, while we managed to create a model that successfully predicts around 80% of all posts. Some things we can conclude are:

- **Unethical == materialism?:** There seems to be a greater focus on purchases and 'gaming' the system, in our ULPT posts, suggesting that people see this behaviour as unethical (but still beneficial to yourself.) Aside from this theme, we can't see any strong indications for the term.

- **Defining unethical:** While there are some themes that stand out for both subreddits, we can't explicitly conclude what 'unethical' or anti-social behaviour is. However, this may come down to the fact that since these posts are written from a 1st person POV and focused on actions, we may not see language that defines negative behaviour. We may be better off examining a different subreddit e.g. AmITheAsshole.

- **What are 'tips'?** We can definitely conclude that the tips submitted to both are quite similar and overlap in language and themes. Many of the tips submitted have to do with wanting to know things, purchases, work, and time.
