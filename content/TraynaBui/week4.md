---
title: "Phase III Individual"
date: 2025-06-06
draft: false
description: "Phase 3 individual post"
slug: "week4trayna"
tags: ["authors", "config", "docs"]
authors: 
    - "traynabui"
showAuthorsBadges : false
---
# Phase IV – Wrapping Up the Dialogue

As this dialogue comes to an end, I’m genuinely amazed at how much we’ve accomplished in just a few weeks. From learning new tools and frameworks to applying machine learning in a real-world political context, this experience has been both challenging and rewarding. Phase IV was all about tying everything together, and I’m proud of the role I played in shaping our final product.

## My Individual Contributions

### 🧠 Recommender System Integration
I focused heavily on implementing our machine learning model in both the backend and frontend:
- Created the API route for our **cosine similarity-based MEP recommender system** (`recommendation_routes.py`) and registered it with a new route prefix.
- Verified the underlying assumptions of our model outside of the app:
  - Ensured that all input vectors were properly normalized.
  - Conducted manual checks of similarity outputs for edge cases (e.g., neutral or extreme users).
  - Visualized similarity score distributions to validate the model’s predictive behavior.

### 🖥️ Frontend Quiz + MEP Match
I worked on the **“Find Your MEP Match”** page, where users answer a few policy questions and get matched with MEPs based on their responses:
- Built the Streamlit UI for the quiz and result page.
- Handled API calls to the Flask backend and displayed matched MEPs, complete with metadata and similarity scores.
- Ensured smooth user experience with responsive design and error handling.

### 🗃️ Final Database Model
Our app relies on clean, structured data, and I helped finalize the database logic:
- Cleaned and organized the `active_members.csv` dataset.
- Structured it into a normalized format that could efficiently support voting vectors, group metadata, and similarity calculations.
- Verified that our route logic aligned with the database schema to avoid redundant lookups and keep latency low.

### 🎨 UI/UX Enhancements
Throughout the final stretch, I contributed to improving the usability of the entire web app:
- Updated column names, button labels, and hover text to make the app more intuitive.
- Wrote short explanations for quiz results and model behavior to help non-technical users understand how it works.
- Adjusted layout spacing and styling to make the interface more polished and accessible.

## 🛠 Software Architecture & ML Summary

Our project stack was built with:
- **Frontend**: Streamlit (Python-based), communicating with the backend via HTTP.
- **Backend**: Flask with modular blueprints for different functionality (e.g., `/b` for the recommender, `/w` for watchlists).
- **ML Model**: Cosine similarity matching user preference vectors with MEPs' voting behavior, allowing us to surface political representatives with high alignment and low party dissent.
- **Database**: Structured CSVs loaded into Pandas DataFrames, mimicking relational databases for dynamic querying and clean data access.

Although the final web app doesn’t show everything behind the scenes, we took care to verify our ML model’s validity through predictive checks, input normalization, and assumption validation before integrating it.

---

## Final Thoughts

This dialogue was much more than a class—it was a launchpad. Before this trip, I had never deployed a real ML model, written Flask API routes, or connected backend models to a live frontend interface. Now, I’ve done all three, and more.

Beyond the technical growth, I’ll always remember the dinners with Dr. Gerber, late-night debugging sessions with friends, and the energy of building something meaningful together. Brussels has been the perfect backdrop for this experience, and I’m incredibly grateful for the people I’ve met and everything I’ve learned.

Thanks to everyone who made this dialogue unforgettable—this has truly been a highlight of my college journey.
