---
title: "Phase 4 Blog Post"
date: 2025-06-13
draft: false
description: "Emily's Phase 4 blog post!"
slug: "phasefouremily"  
tags: ["authors", "config", "docs"]
authors:
  - "emilymoy"
showAuthorsBadges : false
---

# Phase 4 Blog Post
## Contributions
For phase 4, my primary task was to complete the recommender model, develop API routes to connect it to the front end UI, and create the UI page for the model. After taking our phase 3 feedback into consideration, I set the MEP party and country filters to be optional inputs. Additionally, I added in a feature so users could assign “weights” or feature importance values to each inputted criteria. They could put in the percent weight they wanted each feature to hold when coming up with the recommendations, so all of the percents had to add up to 100, whether you had 3 or 5 inputted features. 

In terms of model assumptions, a prime assumption for a recommender system is that all features are normalized when performing the cosine similarity calculations. In the front end for the model, users input values as whole numbers on a scale of 0-100, and those numbers are then divided by 100 so each feature is on a scale of 0-1. This had to be done due to the one-hot encoded categorical features, which are represented with either a 0 or a 1. Regarding predictive checks, I ensured that the model was outputting reasonable predictions by analyzing the results from different variations of inputs. For example, when I entered the Patriots for Europe party, the top 3 recommended MEP recruits were from the Europe of Sovereign Nations or European Conservatives and Reformists parties. In the hemicycle, these parties sit on either side of the Patriots for Europe party, which assured me of the models integrity. 

I created two routes for the model implementation: one to make the full DataFrame of MEP comparison information and one to actually call the recommender code. At first, I tried to pass a full DataFrame through the API route and ran into *many* issues, so Dr. Gerber suggested I create the DataFrame in the same route that calls the recommender itself. Coding is not for the faint of heart; it took a good amount of time to actually be able to implement the model. At one point, I was continuously running into an error because I had a single “/“ somewhere I wasn’t supposed to, and I had forgotten to specify the kwargs variables. After much debugging, I was able to successfully connect the model with our Streamlit UI with an API route. 

For the front end, I implemented numeric slider bars so the user could specify the MEP’s current party alignment, attendance rate, the user’s party alignment, and the optional feature importance weights. Dropdown menus were added so the user could specify their own party, select a party as a criteria, or select a country as a criteria. I added a Streamlit warning box if the weights didn’t add up to 100 and ensured that the user’s party was not included in the dropdown of parties for the input criteria.

All in all, through all the long nights and hours spent on this project, I am proud of what my team and I put together over these 5 weeks. It wasn’t easy at times when we were balancing class work and trips with project work, but between Alex’s impressive technical expertise, Trayna’s positive attitude, and Sienna’s determination to push through even when things went wrong, we truly had a strong team with an even stronger skillset.

## Dialogue Reflection

This dialogue has been amazing experience both academically and personally. Between the guest speakers, trips, classes, the project, and lifelong connections, I know I will be talking about this for years to come. 

I really didn’t know anything about the EU before the dialogue, but now I have a much better grasp on European politics and happenings. Every guest speaker granted us with valuable insights and unique perspectives, which allowed us to have a robust understanding of the topics we learned about. Who knows, maybe in the future I’ll pursue a political/governmental path… 🤭

I’ve also loved the small class size and truly being able to get to know our professors better. Simply taking a professor’s class is one thing, but actually traveling and going out for meals with them has been an enriching experience. I can safely say I have no relationships with professors like the ones I have with Dr. Gerber (shoutout for debugging my code for 40+ mins at 2am 🙏🏻🙏🏻) and Dr. Fontenot (the brains behind this whole dialogue). The fact that they each took time out of their days to write every one of us an individual letter was appreciated beyond words. I had to put mine away when we were all reading them or else I was going to start sobbing.

This dialogue also wouldn’t have been the same without Sydney, our amazing program assistant. She consistently supported us throughout the program, and even when we were discouraged, Sydney was always there as an open, supportive, friendly personality who was truly dedicated to us. I loved getting to know her better over the course of the month, and the superlatives she gave at the end were SO sweet. They were all so personalized, and I know she put a lot of thought into them.

I think it’s safe to say that some of my favorite memories from this dialogue included traveling with my friends on our free days. Sophie, Mahika, and I took a trip to Antwerp, and even just walking around and exploring with them was so much fun. I’ve always said that the people you’re with make or break an experience, and I don’t think I would wake up at 6:30 on the last day to say goodbye to just anyone. I genuinely loved getting to meet everyone on the dialogue, and I cannot wait to have more friendly faces to wave at when we all are in Boston.

Since I’d never been to Belgium or Luxembourg before this trip, it was amazing getting to explore and fall in love with new places. I’m already craving the waffles from Quetzal and Pinocchio. As I write this, I’m on the plane heading back home, already missing Belgium and the friends I made on the dialogue. I hope we can all come back one day and re-live our Belgian experiences. 
