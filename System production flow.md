# Recommendation System Production Pipeline

This document outlines the key stages involved in the production pipeline for a recommendation system.

## 1. Data Ingestion and Processing
- Continuously collect swipe data from the application and stream it into a data source (e.g., Kafka → data warehouse).
- Periodically (e.g., hourly or daily), map swipe data to internal indices.

## 2. Model Training Pipeline
- Periodically train the model (daily or weekly) using a suitable serverless function (e.g., AWS Lambda).
- Regularly optimize model hyperparameters using techniques such as grid search.
- Retrain the model by running a predefined set of steps (e.g., feature engineering, hyperparameter tuning).
- Utilize version control (Git) to store code, ensuring reproducibility and traceability.

## 3. Real-time API for Serving Recommendations
- Deploy the trained model to an API endpoint.
- The API endpoint accepts a `userid` as input.
- Run the model to generate and return recommendations based on the provided `userid`.

## 4. A/B Testing
- Roll out the new model to a subset of users to evaluate its performance.

## 5. Monitoring
- Continuously monitor the model's performance using cloud monitoring tools (e.g., AWS CloudWatch).
- Set up alarms to trigger notifications if model performance degrades, `5xx` errors occur during the API call, and swipe data collection performance is degraded.

## 6. Caching
- Maintain a cache of recommendations to enable pre-suggestion to users within the mobile app, improving user experience and reducing latency.
- Set up a cache server (like Redis), to fetch the recommendations instantly, without making a synchronous call to the Model API.
- Set up timely jobs to prefill/invalidate the existing entries in the server cache and also in the mobile app cache.

# Flow chart
<img width="1536" height="1024" alt="Recommendation_system" src="https://github.com/user-attachments/assets/5bd38db5-d126-491d-aa40-f672fc3f2d1d" />
