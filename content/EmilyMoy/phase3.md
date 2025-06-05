---
title: "Phase 3 Blog Post"
date: 2025-06-05
draft: false
description: "Emily's Phase 3 blog post!"
slug: "phasethreeemily"  
tags: ["authors", "config", "docs"]
authors:
  - "emilymoy"
showAuthorsBadges : false
---

# Phase 3 Blog Post
## Contributions

For phase 3, my primary task was to work on the cosine similarity recommender model. At first, we wanted to have the model predict the alignment rate of any MEP with any party, but we realized that we already had the information needed to perform calculations and come up with the number mathematically. So, after discussing this with our professor, we decided to structure it so that a user (ex: Party Leader) could enter criteria for various MEP features, and the model would tell them which MEPs most closely matched their criteria.

First, we had to decide exactly which features were going to be used in the model and then figure out how to extract the necessary data. The features used were the MEP’s current party, country, alignment rate with their current party, attendance rate for votes, and the alignment rate with the inputter’s party. The most time-consuming part of this process was calculating each MEP’s alignment rate for each party—this required adding over 15 columns to an existing DataFrame of member data and one-hot encoding the categorical variables, but afterwards, calculations were performed to get the alignment rates for each MEP for each party. From there, I created the cosine similarity recommender model. Since this is an unsupervised learning model, I do not have any weights or training/testing data for it, only inputs. 

Right now, the only recommender we have is framed for the purposes of the party leader, but I am planning on adding more functionality and refining the model so it can be of use for the journalist as well.

## Activities

This week, we took a weekend trip to Luxembourg! It was so fun exploring a new place, and my friend and I went into these pods and got a beautiful view of the city at night.

![lux_night](em_p3_lux_night.jpeg)

The valley in Luxembourg was beautiful; we had to take an elevator to go down and also got to ride a funicular, which I thought was super cool.

![lux_valley](em_p3_lux_valley.jpeg)

While in Luxembourg, we visited Eurostat, the European statistical office. As a data science major, I was especially interested in hearing about their processes of collecting and analyzing data. I loved the second speaker we had — she was incredibly engaging!

Luxembourg is a beautiful city, but it wasn't super wallet-friendly for college students. I did love how the public transport was free and the trams were SO clean. At the end of the trip, I did have a minor scare when I thought I lost my wallet, but I found it quickly. 🙏🏻🙏🏻

Once we got back to Belgium, we visited the Wilfried Martens Centre for European Studies in Brussels for a talk on EU Tech Policy and Regulation, which was definitely interesting to hear about. Afterwards, we stopped by the Lindt store and got some chocolates, did some shopping, and then had DELICIOUS Indonesian food! 😋

![lindt](em_p3_lindt.jpeg)

![food](em_p3_food.jpeg)

Another fun little thing that happened this week was getting this Belgian soccer banner from Dr. Gerber for building a successful linear regression model to predict Belgian GDP! I'm going to hang it in my room as a little reminder of Belgium. 🇧🇪 ⚽️

![prize](em_p3_prize.jpeg)