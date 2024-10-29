# Project Description: Building a Streamer Recommendation System for Users

### Objective
The goal of this project was to develop a model to predict the probability that a user will send a gift to a streamer on a streaming platform. The task involved analyzing data on users, streamers, and their interactions during events (streams, gift sending, etc.). The primary aim was to enhance the effectiveness of recommendations for users and gain better insights into their behavior.

### Steps Taken

1. **Data Cleaning and Preparation**
   - Loaded and initially reviewed three datasets: *Users*, *Streamers*, and *Users’ Activity*.
   - Removed duplicates and missing values to ensure data quality.
   - Dropped columns that were not helpful for prediction, such as `event_date`, `event_timestamp`, IDs, and other temporary variables.
   - Filled missing values for numerical features, such as the number of subscriptions and followers, with 0.

2. **Feature Engineering**
   - Created new variables for the model, such as:
     - `days_since_user_install` — the number of days from the user's app installation to the event.
     - `days_since_streamer_install` — the number of days from the streamer’s app installation to the event.
     - `coins_per_day_streamer` — the average number of coins earned by the streamer per day.

3. **Encoding Categorical Variables**
   - Applied *One-Hot Encoding* for categorical features, such as user and streamer gender, and app installation source (*media_source*).
   - Converted boolean variables into 0 and 1 formats to facilitate model usage.

4. **Balancing the Target Variable**
   - The target variable (gift sending) was highly imbalanced: most users did not send gifts. To address this, we applied class resampling to balance the number of examples for both classes.

5. **Modeling**
   - Used three algorithms for building the model:
     - Logistic Regression.
     - *Random Forest*.
     - *XGBoost*.
   - The *XGBoost* model showed the best results with an accuracy and *F1-score* of 82%.

6. **Feature Importance Analysis**
   - Used *SHAP* analysis to evaluate the importance of each feature. The most important factors identified were:
     - The number of days since the app installation by the user.
     - The number of subscriptions to streamers.
     - User gender (men sent gifts more often).
     - Average duration of streamer’s streams.

7. **Visualization and Analytics**
   - Generated *Partial Dependence Plots* (PDP) for the most significant features. PDP enabled us to observe how changes in feature values affect the probability of a user sending a gift.

### Results
- **Prediction Accuracy**: The *XGBoost* model achieved an accuracy of 82% on the balanced dataset, outperforming other models.
- **Key Factors**:
  - Days since app installation: users who recently installed the app were more likely to send gifts.
  - Gender: male users were more inclined to send gifts compared to other categories.
  - Number of subscriptions: users with fewer subscriptions to streamers were more likely to send gifts.
  - Average stream duration: shorter streams received more gifts.

### Conclusion
The *XGBoost* model provided the best performance compared to other algorithms. Analysis based on *SHAP* and *Partial Dependence Plots* helped to understand the key factors influencing user behavior. The findings can be used to fine-tune the recommendation system and develop personalized offers for platform users.
