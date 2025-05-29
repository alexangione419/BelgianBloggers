---
title: "Project - Phase II"
date: 2025-05-27
draft: false
description: "Our Idea"
slug: "phase2post"
tags: ["project", "data model", "data cleaning"]
authors:
  - "sienna_boos"
  - "alex_angione"
  - "traynabui"
  - "emilymoy"
showAuthorsBadges: false
---

# Project Updates

In our developement on phase two, we made some updates to our user stories. We took in feedback on making our stories more actionable, and fleshed out the features they represent in order to differentiate each persona. The new user stories are as follows. 

## Party Leader: Seeing Unity Within Your Party

### Persona Description:

**Γιάννη Πούλος (Yanni Poulos)** is 59 years old and has served in EU government for his entire career. His most prioritized value in life is loyalty, and he hates when peoples' actions contradict their words. Γιάννη has also always preferred being in charge and does not hesitate to take action when he notices something peculiar. His meticulousness and vehemence have made him a respected party leader.

### Story:

Γιάννη is the leader of, in his opinion, the best EU party. He is frustrated because he has felt that his party has not been as cohesive as it has been in the past, with some members voting against the group. He would like to know which MEPs are not loyal to his party and speak with these individuals to ensure party security and transparency. Our solution will alleviate Γιάννη’s issues by informing him how coherent the party is, which members are not voting with the group, and which MEPs are likely to leave or join the party down the line.

### Why Would Γιάννη Use Our Application?

- "As a party leader, I want to see an objective number for how coherent my party is so that I can make informed decisions about how to lead the group."
- "As a party leader, I want to be able to identify members who are not voting with the group to know if I need to have a conversation with them or pay special attention to their voting patterns."
- "As a party leader, I want to identify MEPs outside of my party that vote very similarly to my own so that I can talk with them and potentially recruit them to my party."
- "As a party leader, I want to identify trends in party loyalty over time so I can address whether cohesion within my group is strengthening or weakening and take proactive steps to address internal divisions before they affect legislative outcomes."
- "As a party leader, I want to see how my party’s cohesion compares against other parties so I can relatively assess our unity and reinforce our credibility with constituents and allies."
- "As a party leader, I want to keep track of all MEPs I take note of and think would be worth speaking with, so I can grow my party and strengthen its connections."

## Political Journalist: Identify Surprising Dissenters or Party Fractures

### Persona Description:

**Camila Romero** is a political journalist from Spain who specializes in writing about the EU government, notably changes and conflicts within it. She is 30 years old and graduated from Universidad de Barcelona. She is very knowledgeable about EU politics and party dynamics. 

### Story:

As a journalist, Camila’s top priority is reporting fresh and factual information to keep her audience engaged. Since there are so many votes that happen in Parliament, she wishes she had a consistent source to access nuanced parliamentary data and analyze specific MEPs’ voting patterns. She wishes she had a consistently updated, consolidated, and interactive place to find reliable data for her articles so she can devote more time and energy to actually writing and less to searching for data. Our application will resolve her matters by providing all the MEP voting data that she needs in one spot. She will also be able to access documents for policies that the EU Parliament votes on so she can fact-check her work.

### Why Would Camila Use Our Application?

- "As a journalist, I want to identify MEPs who frequently dissent so I can write about or interview them about how closely their voting behavior aligns with their formal party affiliation."
- "As a journalist, I want to know if there are any patterns in dissent that could detail potential party overlaps so that I have a better understanding of party ideologies."
- "As a journalist, I want to know if dissent is growing over time in the European Parliament so I can quantify whether party cohesion is weakening and write articles about this topic."
- "As a journalist, I want to be able to access verified records for the policies that were voted on so that I can accurately write about them in my articles."

## Citizen: Hold MEPs Accountable to their Party Platforms

### Persona Description:

**Greg Gerborg** is 23 years old. He grew up in Switzerland and lived there for his whole life, but he just moved to the EU. In college, Greg studied mechanical engineering at the University of Zurich, and he possesses sparse knowledge of politics. He cares a lot about science, though, and he doesn’t want to lose funding for all of his cool engineering projects. 

### Story:

Greg is unsure of what MEPs he should vote for, so he would like to learn about all the MEPs’ views and what laws Parliament is voting on. He is frustrated because he does not know where to look for voting and party information beyond the basics, and he would like to have one website he can reference to find all the information he needs. Our application provides information to voters like Greg on MEP loyalties and votes so that citizens know which MEPs best align with their political beliefs and how much the MEPs waver from these beliefs.

### Why Would Greg Use Our Application?

- "As a citizen, I want to know how MEPs voted on different policies so I can decide where to move based on a country’s political beliefs."
- "As a citizen, I want to see a list of all the MEPs and their profiles to learn more about the MEPs views"
- "As a citizen, I want to learn more about each party and what they stand for to learn about which one aligns most with my political beliefs."
- "As a citizen, I want to know more about my country’s voter turnout to see how politically involved my country is."


# Data Visualization
This visualization shows how well a certain MEP is aligned with their political party since a significant part of our project involves analyzing individual MEP alignment with their formal party. This bar plot clearly labels the percentage of votes where an MEP either agreed with their party, dissented from their party, or did not vote. In the example shown, MEP Roberto Vannacci is strongly aligned with the Patriots for Europe party, agreeing with almost 80% of the party's votes.
![data_viz_one](initial_data_viz)


# First Pass ML Model

Our planned models are as follows:

- A recommender model using cosine similarity to identify MEPs that are likely to/should change parties based on their voting actions.

- A linear regression model predicting party cohesion overtime for each party.

We attempted to create the linear regression model, but there was essentially no correlation between date of vote and percent dissenters for any of the parties. We plan to try add more features to predict party cohesion, such as average age of MEP, country demographics of the party, etc. to see if there is a correlation. A lot of the votes happen on the same day with large gaps between votes, which led to tall vertical lines of points on the graph. This indicates that time is not a sufficient measure to be the only feature examined. We would also like to use data from more than just the last 1000 votes, which we had to resort to as the API was being overloaded and timing out. We will make these changes when fully implementing the ML model.

# Data Models

## Party Leader Data Model 

![image](partyLeader.jpeg)

## Political Journalist Data Model

![image](politicalJournalist.jpeg)

## Citizen Data Model

![image](citizen.jpeg)

## Global Data Model

![image](global.jpeg)

## ER Diagram

![image](ERDiagram.jpeg)


## First Pass SQL DDL

```sql
  DROP DATABASE IF EXISTS plp;
  CREATE DATABASE IF NOT EXISTS plp;

  USE plp;


  CREATE TABLE IF NOT EXISTS political_party (
      partyID INT PRIMARY KEY,
      partyCohesionScore INT,
      partyName VARCHAR(255)
  );

  CREATE TABLE IF NOT EXISTS mep (
      mepID INT PRIMARY KEY,
      name VARCHAR(255),
      countryOfOrigin VARCHAR(255),
      partyID INT,
      recommendedParty INT,
      FOREIGN KEY (partyID) REFERENCES political_party(partyID),
      FOREIGN KEY (recommendedParty) REFERENCES political_party(partyID)
  );


  CREATE TABLE IF NOT EXISTS watchList (
      watchListID INT PRIMARY KEY
  );

  CREATE TABLE IF NOT EXISTS mepToWatchList (
      watchListID INT,
      mepID INT,
      PRIMARY KEY (watchListID, mepID),
      FOREIGN KEY (watchListID) REFERENCES watchList(watchListID),
      FOREIGN KEY (mepID) REFERENCES mep(mepID)
  );

  CREATE TABLE IF NOT EXISTS user (
      userID INT PRIMARY KEY,
      age INT,
      countryOfOrigin VARCHAR(255),
      firstName VARCHAR(255),
      lastName VARCHAR(255),
      partyID INT,
      watchListID INT,
      headOfParty INT,
      FOREIGN KEY (partyID) REFERENCES political_party(partyID),
      FOREIGN KEY (watchListID) REFERENCES watchList(watchListID),
      FOREIGN KEY (headOfParty) REFERENCES political_party(partyID)
  );


  CREATE TABLE IF NOT EXISTS legislation (
      legislationID INT PRIMARY KEY,
      title VARCHAR(255),
      dateOfVote DATE
  );

  CREATE TABLE IF NOT EXISTS referenceDocument (
      legislationID INT,
      referenceID INT,
      PRIMARY KEY (legislationID, referenceID),
      FOREIGN KEY (legislationID) REFERENCES legislation(legislationID)
  );

  CREATE TABLE IF NOT EXISTS vote (
      mepID INT,
      legislationID INT,
      description VARCHAR(255),
      PRIMARY KEY (mepID, legislationID),
      FOREIGN KEY (mepID) REFERENCES mep(mepID),
      FOREIGN KEY (legislationID) REFERENCES legislation(legislationID)
  );

```
### Wireframes

![image](citizien.jpeg)
*Citizen: Designed to guide users like Greg through key features such as MEP profiles, party overviews, and country comparisons to help inform relocation decisions based on political alignment.*


![image](homepage_wireframe.jpeg)
*Homepage: Designed to guide users personas and give an overview about how voting works in the EP*

![image](party_leader.jpeg)
*Party Leader: Shows the user how cohesive their party is compared to other parties over a chosen time period, provides recommendations for potential party recruits, and shows information about these MEPs.*

![journalist_wireframe_meps](journalist_wireframe_meps.jpeg)
*Journalist: This is the page for accessing individual MEP party loyalty records — Camila can choose an MEP and see how well their votes align with their party’s.*

![journalist_wireframe_policies](journalist_wireframe_policies.jpeg)
*On this page, Camila can access records for policies that the European Parliament votes on.*