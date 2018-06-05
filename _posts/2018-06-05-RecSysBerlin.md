---
layout: post
title: Food Recommendations at Delivery Hero
excerpt_separator:  <!--more-->
comments: true
tags: ['Berlin RecSys Meetup', 'Recommender Systems']
---

Notes from an excellent talk by [Gugulethu Ncube](http://www.guguncube.com/) from Delivery Hero at the [Berlin RecSys Meetup](https://www.meetup.com/RecSys-Berlin/events/250148996) tonight on how they work with food recommendation. Rephrased in my words and with my thoughts interspersed, _so anything crazy-sounding should with all likelihood be attributed to me._

**Goals for recommendations:**
- Provide users with new restaurants to order from as ordering from multiple restaurants makes customers more loyal

**Collaborative vs. Content-based:**
> "Collaborative filtering produces very strange results"

- Seems to end up giving quite uninteresting recommendations, such as very popular chains.
- Reason behind is the extreme sparsity of data, and the distribution of data that is very tied to geographical location of restaurants.
- This also explains why chains ends up in top, as they have so much more data from their different locations.

## FoodRank - Content based
In a nutshell; ranking how good restaurants are at _your favourite food_.

<!--more-->

Focuses on what customer actually eats, i.e. type of dishes, ingredients and other metadata. From this they create unique preference footprints for each customer.

This footprint means they can calculate customer scores for various attributes tied to the dishes, and then predict new dishes scores based on these.

One reason to do this probably falls back on the sparsity of the data for the actual products, and using metadata features instead as a workaround is something I've seen [mentioned before ](https://www.youtube.com/watch?v=EgE0DUrYmo8) by Maciej Kula.

### Expectations and Ratings
> "Everyone knows McDonalds. When you order from there, you know what you get, so you won't rate it bad."

McDonalds is very popular and get very good ratings, which doesn't necessarily reflect how people actually view the quality of their food relative other restaurants. _Familiarity means you don't get negative surprises often, which is reflected in the ratings._

**Getting a good measure for quality is a really hard problem**, learning personal affinities is much easier.

### Rankings and Click-throughs
What is the best place to bury a dead body? On the second page of Google results. Classic SEO joke. Similar holds true for rankings in general.

The top ranking in a filtered list gets by far the most clicks and checkouts. Roughly 25% of all orders goes to top position in list and the top ten ranked restaurants gets two thirds of all orders.

This means that the sales data gathered is very biased based on existing ranking, and review data as well.

Having multivariate tests to switch the order of rankings helps get more unbiased data.

### Testing
Web interface with affinity checker to see customer recommendations and what they are based on. Can display recommendations based on different algorithms for comparison.

## Q&A
* Listings and recommendations are separate for historic reasons. A side effect from this though should be that it helps avoid a complete feedback loop where the top recommended restaurants keeps getting better scores due to ending up high in list. For an existing business it's also a fast way to get started implementing recommendations, as a new recommended widget can be implemented without refactoring a complex existing codebase.

* Ten people (mostly engineers) working in the team. For one year now in DeliveryHero, but the team has longer background of working together on search and discovery.

* Serendipity is hard in food recommendation; how do you give a vegetarian a surprise? Recommend a meat dish!

* Moving away from saying "this is recommended for you" as it implies they know very much about the users. Which might not be true (and with GDPR here it might be sensitive).

* In Germany, everyone will sooner or later order Italian, so that might say more about the culture as a whole than about specific individuals and their preferences.

* Menu data and ingredients are manually entered, about 70% is considered good quality. Foodora in Germany has fully correct, varying in other markets.

* Relevant tags are contextual, pasta is considered 'western' in Asia for example, whereas that tag doesn't make sense in Europe.

## Takeaways
- Geographically widespread stores with non standard products might not be a good fit for collaborative filtering methods due to extreme sparsity of data, and purchase patterns very geographically based.
- The non-standard nature of the products also means that looking at the metadata features might tell you much more as you will have much less sparsity in data on that level.
- When implementing recommendations, there's a risk of getting a positive feedback loop, where the most highly rated items always ends up on top and thus (since people usually choose the top items) end up becoming more popular - cementing its position in the top.
- Finding a good way to estimate quality is both key and a really hard problem. Engineered features such as repeat purchases and metadata information such as ingredients might contain useful information missed by popularity and ratings.
