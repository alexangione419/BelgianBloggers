---
title: "Project - Phase IV"
date: 2025-06-13
draft: false
description: "Our Execution"
slug: "phase4post"
tags: ["project", "data model", "data cleaning"]
authors:
  - "sienna_boos"
  - "alex_angione"
  - "traynabui"
  - "emilymoy"
showAuthorsBadges: false
---


# Project Updates

The final iteration of our project brought along some updates and changes to our original design plan
- We removed the idea of showing legislature and reference documents to the Political Journalist, to decrease scope and keep the app contained to its main goals




## Final State of Models




## Software Arcitecture 

Our arcitecture is a fairly standard for a web app connected to a db in the backend. A key aspect is that our front end never directly talks to our database or any external data source; all communication transpires over the api layer. 

![image](arcitecture.jpeg)



## Data Model

As mentioned earlier, we removed the idea of a Political Journalist being able to view legislature being voted on. This meant the removal of two of the tables in our original data model, "Legislature" and "Reference Document". We also added attributes to MEP to store more information about their voting cohesion with respect to their party. For the watchlist, we realized there was no real need for each entry to have its own Id. Now, the watchlist is set up sort of as a bridge table between MEP and User, allowing for a many to many relationship that we interpret as a watchlist. 

![image](finalDataModel.jpeg)