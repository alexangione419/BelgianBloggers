---
title: "Sienna - Phase I"
date: 2025-05-27
draft: false
description: "Sienna's Phase II Blog Post"
slug: "phaseIIsienna"
tags: ["authors", "configs", "docs"]
authors:
  - "sienna_boos"
showAuthorsBadges: false
---

# Project Phase II

For the Phase II Deliverable, I contributed to **data collection and cleaning, creating wireframes, and developing a proof of concept ML model.** One of the relationships we are analyzing is party cohesion over time, so I wrote code to gather the relevant data from the API, store it in a dataframe that I saved as a csv, and add the necessary columns for calculating percent dissenters. I then visualized this relationship for all parties so I could make the linear regression model.

However, an issue I ran into is that the trends are not linear. Upon visualization and calculating r squared values, I realized that there was essentially no correlation between date of vote and percent dissenters for any of the parties. I would like to try again in a few days, as I was only able to get data from the last 1000 votes as the API was being overloaded and timing out. I built a skeleton model for performing linear regression, and when I visualized the line for each party, I saw that a lot of the votes happen on the same day with large gaps between votes. This led to tall vertical lines of points on the graph. In Phase III, I would like to adjust this and try visualizing the trend with more data to see if any linear trends are possible given enough data. If not, we can use the linear regression model to predict another relationship.

I also designed the UI wireframes for the Party Leader’s app view to best fit our user stories as they were evolving.

This week in Belgium, I really enjoyed the most recent speaker who discussed public service values in recommender algorithms. I found his views on ethical data very fascinating, and the debrief with our class probed me to think deeper about what my own values are.

![Bruges Canal](bruges.jpeg)