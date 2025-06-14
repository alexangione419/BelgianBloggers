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

The final iteration of our project brought along some updates and changes to our original design plan:

- We removed the idea of showing legislature and reference documents to the Political Journalist in order to decrease scope and keep the app contained to its main goals. We also added a line graph vizualization to this persona showing dissent overtime by party, as we did not end up using this data in our ML model for prediction but still wanted to include it in the app.

- We pivoted the country comparison page to a country matching page, which allows the user to identify the country with MEPs who align most with their political preferences.


## Final State of Models

### Cosine Similarity Recommender Model

### Logistic Regression Model

The final model uses party and procedure types to predict the percentage of dissenting MEPs within the included parties on votes within those procedure types. We used logistic regression (as opposed to linear) because the output domain ranges from 0 - 1, which is suitable for predicting a percent. Its r-squared value was 0.33, which could definitely be improved, but given the context, it is performing reasonably well. The model is predicting how individuals will vote on policies. It attempts to capture their _opinions_, something distinctly human and therefore distinctly volatile. Both of the input variables are also categorical, which limits the performance of the model. Our data did not contain any numerical features relevant to predicting dissent, but to improve the model in the future we could find another data source that does add a numeric feature in order to capture more meaningful results.

**Assumptions of Logistic Regression:**


- **Autocorrelation:** Observations are not dependent based on time.

Our model passes the no autocorrelation assumption because the value of the residuals or their variance do not experience a trend in relating to when the data points were collected relative to one another. This is precisely the reason we had to scrap the time series model. It is shown in the residuals versus order plot:

![Residuals vs Order](resids_order.png)


- **Multicollinearity:** Independent variables should not be too highly correlated with each other.

To evaluate multicollinearity, we checked to see if there were specific features highly correlated with others in the data set. Since the variables are categorical, we used the variance inflation factor. While most of the VIFs were low, a few were abnormally high, such as procedure_type_COD and procedure_type_INI. All of the parties had low VIF values.

- **Requires a large sample size:** 

We didn't talk about this in class, but upon researching logistic regression evaluation a but, we found that in general you need at least 10 cases with the least frequent outcome for each independent variable in your model. Our sample size met this guideline.


## Software Arcitecture 

Our arcitecture is a fairly standard for a web app connected to a db in the backend. A key aspect is that our front end never directly talks to our database or any external data source; all communication transpires over the api layer. 

![image](arcitecture.jpeg)



## Data Model

As mentioned earlier, we removed the idea of a Political Journalist being able to view legislature being voted on. This meant the removal of two of the tables in our original data model, "Legislature" and "Reference Document". We also added attributes to MEP to store more information about their voting cohesion with respect to their party. For the watchlist, we realized there was no real need for each entry to have its own Id. Now, the watchlist is set up sort of as a bridge table between MEP and User, allowing for a many to many relationship that we interpret as a watchlist. 

![image](finalDataModel.jpeg)