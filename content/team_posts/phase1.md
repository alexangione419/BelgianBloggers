---
title: "Project - Phase I"
date: 2025-05-19
draft: false
description: "Our Idea"
slug: "phase1post"
tags: ["project", "Setup"]
authors:
  - "sienna_boos"
  - "alex_angione"
  - "traynabui"
  - "emilymoy"
showAuthorsBadges: false
---

# European Parliament Party Cohesion and MEP Loyalty

In an age of political contention, having transparent and accessible political data is essential to hold Members of the European Parliament accountable regarding their voting actions. Our application aims to visualize MEP party loyalty, identify frequent dissenters, and provide recommendations for party changes and civilian votes.

Due to the high volume of votes that Parliament holds, it can be difficult for both party leaders and members to keep track of cohesion within the group. Currently, there is no interactive system that visualizes and predicts MEP voting patterns and party loyalties.

Our application will provide an interface to view how cohesive a given political party is based on the percentage of MEPs within the party that vote together. It will visualize the hemicycle through the lens of party loyalty and also provide information for the MEPs themselves, specifically by computing a loyalty score for each. This will allow the application to predict future party changes, offer potential recommendations for party changes, and corroborate rhetoric with actual votes. It can also inform citizens how closely their MEP is in alignment with their party’s values so they can make an informed decision on whether to vote for that person again.

With our app, we hope to streamline MEP data by providing clear insights for our user personas. By creating interactive visualizations, predictions, and loyalty scores, we hope to increase transparency and civic engagement across the EU.


# User Personas and Stories

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


## Political Journalist: Identify Surprising Dissenters or Party Fractures

### Persona Description:

**Camila Romero** is a 30 year old political journalist from Spain who specializes in writing about the EU government, notably changes and conflicts within it. She graduated from Universidad de Barcelona and is very knowledgeable about EU politics and party dynamics.

### Story:

Because there are so many votes that happen in Parliament, Camila wishes she had a consistent source to access nuanced parliamentary data and analyze specific MEPs’ voting patterns. She is used to sitting at her desk and parsing through an ocean of numbers that aren't uniform. She desires a consistently updated, consolidated, interactive place to find reliable data for her articles so she can devote more time and energy to actually writing and less to searching for data.

### Why Would Camila Use Our Application?

- "As a journalist, I am writing an article reporting unrest within parties, and I want to see MEPs who frequently dissent so I can write about or interview them."
- "As a journalist, I would like to see if there are any patterns in dissent that could detail potential party overlaps."
- "As a journalist, I am compiling a case study on a specific MEP, and I want to see to what extent their formal party affiliation aligns with how they actually vote."
- "As a journalist, I am exploring whether dissent is growing over time in the European Parliament, after controversial legislation, and I want to quantify whether party cohesion is weakening across sessions to predict future parliamentary trends."
- "As a journalist, I am writing an opinion piece predicting which MEPs will change parties in the coming years. I would like to find accessible, easily interpretable data to inform my research."


## Citizen: Hold MEPs Accountable to their Party Platforms

### Persona Description:

**Greg Gerborg** is 23 years old. He grew up in Switzerland and lived there for his whole life, but he just moved to the EU. In college, Greg studied mechanical engineering at the University of Zurich, and he possesses sparse knowledge of politics. He cares a lot about science, though, and he doesn’t want to lose funding for all of his cool engineering projects. 

### Story:

Greg is unsure of what MEPs he should vote for, so he would like to learn about all the MEPs’ views and what laws Parliament is voting on. He is frustrated because he does not know where to look for voting and party information beyond the basics, and he would like to have one website he can reference to find all the information he needs. Our application provides information to voters like Greg on MEP loyalties and votes so that citizens know which MEPs best align with their political beliefs and how much the MEPs waver from these beliefs.

### Why Would Greg Use Our Application?

- "As a citizen, I want to see how MEPs voted so I can decide who I should vote for, or if I should change my vote."
- "As a citizen, I want to see a list of all my MEPs and profiles for each MEP to learn more about the MEPs' voting actions."
- "As a citizen, I want to learn more about the voting split on individual policies."
- "As a citizen, I want to know more about my country’s voter turnout to see how politically involved my country is."
- "As a citizen, I want to know more about my party’s voter cohesion to see how unified my party is."


# Candidate Data Sources

## HowTheyVote.eu

This data source serves as a record of how each Member of the European Parliment(MEP) voted on a given legisalture discussed at a given plenary session. 
There exist records for 1962 distinct legislature, each with the associated 751/705 (pre/post Brexit) MEP votes. 
Each vote consists of the MEP's name, part affiliation, desicion, and nationality. 

With this information, we will be able to 
- Compute cohesion metrics (percentage of party “for” votes).
- Provide party affiliation recommendations


Note: This API is under development and experimental. If winds up being unreliable, all of the data is available to download seperately. 
![image](successfulHowTheyVoteCall.jpeg)



## European Parliment Open Data API

This data source is the EP’s official API, suppling comprehensive information on MEPs, corporate bodies, events, meetings, and more.


This information will primarily be used to
- Access in depth information about each MEP to be used for individual analysis


![image](successfulMEPCall.jpeg)
