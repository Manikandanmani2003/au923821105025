import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier
from sklearn.metrics import accuracy_score

# Load the hotel booking dataset
hotel_data = pd.read_csv('hotel_booking_data.csv')

# Data preprocessing
# Handle missing values, encode categorical variables, etc.

# Exploratory Data Analysis (EDA)
# Explore booking patterns, trends, and correlations

# Feature Engineering
# Select relevant features for predictive modeling
X = hotel_data[['lead_time', 'arrival_date_month', 'stays_in_weekend_nights', 'stays_in_week_nights']]
y = hotel_data['is_special_request']

# Split the data into training and testing sets
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Model Training
model = RandomForestClassifier()
model.fit(X_train, y_train)

# Model Evaluation
y_pred = model.predict(X_test)
accuracy = accuracy_score(y_test, y_pred)
print("Accuracy:", accuracy)

# Feature Importance
feature_importance = pd.DataFrame({'feature': X.columns, 'importance': model.feature_importances_})
print("Feature Importance:", feature_importance)

# Predictions
# Make predictions on new data or deploy the model for future bookings



OUTPUT:
1.	Accuracy: The accuracy of the trained model on the test data. It indicates how well the model is performing in predicting whether a booking will receive special requests.
2.	Feature Importance: A table showing the importance of each feature in the prediction task. This will help you understand which factors (such as lead time, month of arrival, etc.) are most influential in determining whether a booking will have special requests.
3.	Predictions: If you have new data, you can use the trained model to make predictions on it. The output would be the predicted probability or class label indicating whether each booking is likely to receive special requests.
To generate the output:
•	Replace 'hotel_booking_data.csv' with the path to your dataset containing hotel booking information.
•	Ensure that your dataset contains the necessary features (lead_time, arrival_date_month, stays_in_weekend_nights, stays_in_week_nights, and is_special_request).
•	Run the code in a Python environment with the required libraries installed (pandas, scikit-learn).
Once executed, you should see the accuracy score printed to the console, the feature importance table displayed, and you can use the trained model to make predictions on new data.

