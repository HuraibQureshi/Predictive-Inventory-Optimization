# Predictive Inventory & Supply Chain Optimization

## Overview
This project addresses inventory stockouts in e-commerce by predicting demand using machine learning.

## Key Features
- **Data Pipeline:** ETL process using SQLite for high-speed analysis.
- **Forecasting:** Developed an optimized Random Forest model to predict demand.
- **Business Impact:** Automated reorder triggers reducing stockout risk.

## How to run
1. Clone this repository.
2. Ensure you have the Olist E-commerce dataset.
3. Run the notebook in Google Colab.






Technical Case Study: Predictive Inventory Optimization
Author: Mohammed Huraib Qureshi
Target Impact: 15–20% Reduction in Stockout Occurrences
Technologies: Python (Scikit-Learn, Pandas), SQL (Relational Design), XGBoost, Tableau
________________________________________
1. Abstract: The Vision
In the world of e-commerce, data is the heartbeat of the warehouse. This project was born from a simple observation: manual inventory counts are reactive and prone to human error. I set out to build an end-to-end pipeline using the O-list Brazilian E-Commerce dataset to prove that we can move from "guessing" what we need to "knowing" what we need. By combining SQL-based data warehousing with an optimized Random Forest model, I achieved a Mean Absolute Error (MAE) of 10.6, creating a system that tells a warehouse manager exactly when to reorder before the shelf goes empty.
________________________________________
2. The Problem: Moving Beyond "Reactive" Logistics
Working in environments like Baby’s Best Food GmbH, I’ve seen firsthand how a single stockout does not just lose a sale—it loses a customer’s trust. Traditional inventory management is often "backward-looking."
The goal of this project was to build a proactive "early warning system" to solve three specific pain points:
•	The Stockout Trap: Losing revenue because high-velocity items are not replenished in time.
•	The Dead Stock Problem: Wasting warehouse space and capital on items that aren't moving.
•	The Operational Fog: Giving operations teams clear, actionable triggers rather than complex spreadsheets.
________________________________________




3. Data Engineering: Building the Foundation
3.1 The "Warehouse First" Approach
I did not just load a CSV file; I built a Relational Data Warehouse. Using SQLite, I modelled the relationship between customers, orders, and products. This reflects a real-world production environment where data is messy and spread across multiple tables.
 
Figure 1: Relational Data Schema connecting Orders, Products, and Items.

3.2 Feature Engineering: Teaching the AI "Time"
A model is only as smart as the data it's fed. I focused on Temporal Intelligence:
•	Human Cycles: I taught the model to recognize weekends and month-end shopping spikes.
•	Short-term Memory (Lags): I created a 7-day "lag" feature so the model knows what happened exactly one week ago.
•	Momentum (Rolling Windows): By calculating a 30-day moving average, the model can tell if a product is "trending" or "fading."

 
Figure 2: Time-series analysis of Health & Beauty demand, highlighting weekly spikes and monthly seasonality.
________________________________________
4. Modelling: The Search for Stability
I didn't settle for the first algorithm I tried. I benchmarked three industry heavyweights specifically for the Health & Beauty sector:
Algorithm	Performance (MAE)	Why it worked/failed
XGBoost	12.52	Powerful, but slightly overfit the noise in this specific volume.
LightGBM	10.75	Very fast, but struggled with some of the extreme outliers.
Random Forest	10.62	Winner. The ensemble approach provided the most stable predictions.

 
Figure 3: Comparative Performance Analysis—Random Forest achieved the lowest Mean Absolute Error (MAE).
I then performed a Grid Search to fine-tune the "forest," ensuring that the model was not just memorizing the past, but learning the patterns.
________________________________________



5. Turning Math into Money: The Action Plan
A prediction is useless if it doesn't lead to an action. I integrated the model into a Reorder Point (ROP) framework.
I factored in Lead Time (how long the supplier takes) and Safety Stock (the "cushion" needed for unexpected surges). The final output isn't a graph; it's a Daily Reorder List. If the current stock is lower than the calculated "safe" level, the system flags it: "REORDER NOW."
 
Figure 6: Automated Inventory Action Plan—Translating ML predictions into operational reorder triggers.
________________________________________
6. Reflections & Conclusion
This project represents my philosophy as a Data Scientist: Data is a tool for decision-making. By bridging the gap between a MySQL data warehouse and a Machine Learning pipeline, I have created a blueprint for modern logistics. For a business, this means higher fulfilment rates, lower storage costs, and a more resilient supply chain.
