# user_recommendation_system

## Overview
This project implements a **feature-based recommendation system** for a swipe-based application. 
It uses user-item interaction data (likes) along with engineered features to generate personalized recommendations.
The pipeline supports **warm-start** (known users) and **cold-start** (new users) scenarios, with a fallback to popularity-based recommendations.

## Result
Achieved 80% hit ratio on warm start users and 75% hit ratio for cold start users

## Key Features
- **Feature Engineering**: 
  - Demographics (age difference, age group match)
  - Temporal behavior (night swipes, recency)
  - Popularity scores
  - Mutual likes
  - Hour bucket matching
- **Modeling**:
  - LightGBM-based ranking model
  - Negative sampling with hard negative strategy
  - Optimized feature computation
- **Evaluation**:
  - Hit Rate@K metric for retrieval performance
  - Support for both warm-start and cold-start evaluation
- **Demonstration**:
  - Shows recommendations for both warm-start and cold-start test users with original IDs
## Production Architecture
<img width="1536" height="1024" alt="Recommendation_system" src="https://github.com/user-attachments/assets/0e631def-40f0-49f6-878c-aab13305291e" />
Read more about production flow [here](/system_production_flow.md)
 
## Requirements
- Python 3.8+
- pandas, numpy, scikit-learn
- lightgbm
