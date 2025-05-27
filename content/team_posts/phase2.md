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



# First Pass ML Model



# Data Models

## Party Leader Data Model 

![image](partyLeader.png)

## Political Journalist Data Model

![image](politicalJournalist.png)

## Citizen Data Model

![image](citizen.png)

## Global Data Model

![image](gloabl.png)

## ER Diagram

![image](ERDiagram.png)

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
