---
title: "Project - Phase III"
date: 2025-06-05
draft: false
description: "Our Idea"
slug: "phase3post"
tags: ["project", "data model", "data cleaning"]
authors:
  - "sienna_boos"
  - "alex_angione"
  - "traynabui"
  - "emilymoy"
showAuthorsBadges: false
---

# Project Updates

Our project plan has remained the same for the most part since our Phase II submission. Our user stories are unchanged, with the party leader having the goal of seeing potential recruits and at-risk MEPs as well as cohesion over time. The journalist can compare cohesion in parties and view individual MEP loyalty scores. The citizen can see a general overview of the parties, MEPs from his country, and statistics/visualizations relating to these entities.

# ML Models

In terms of our machine learning models, their goals have not shifted, but we had to alter the execution of the models a bit to increase complexity and better align them with the way our data is structured. For the cosine similarity model, we originally wanted to rank the top 5 MEPs relative to the “average profile” of a party, seeing who from outside a party is agreeing with the majority of that party most often. However, we realized that the execution of this at its core was just number crunching and did not really involve machine learning. We shifted the model to analyze the similarity of one MEP to another based on features that are inputted, such as the MEP’s party, country, alignment rate with their current party, and attendance rate for votes. The alignment rate with the inputter’s party is also taken into account. This also makes the model more personalized for the users; for instance, the party leader can see MEPs whose traits are most similar to their inputs, and the journalist can conduct a case study on any specific MEP. This model is now fully functional and built into the application.

For the time series model, we were originally attempting to use a traditional linear regression model, but we realized that we needed a slightly different, more specialized approach with time series data. Now we are using a moving averages time series model to visualize and forecast the percentage of dissenters in each party over time. The party leader can utilize it to see how unified their party is compared to others and how these trends are projected to change in the future, and the journalist can use it to compare parties on a holistic level. The information we are using is voting data from the past 5 years. We had to merge multiple different data files that were called from the API, filter the dataframe down to what we needed, and group individual MEP votes by party. Then we added new columns representing the majority vote for each party for each policy (for, against, abstain, no vote), filter out rows where no vote was the majority, then calculate the percent of dissenters for each row. We now have this cleaned and prepared dataframe with all the information we need and are ready to implement the actual machine learning part of the model as we move into Phase IV.

# Modifications to Data Model

# Tables

# REST API Matrix

provide screenshots of the mocked up app and results of the implemented functionality, including calling the ML model
