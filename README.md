# Bullet Train Passenger Experience Prediction

## 🏆 Hackathon Winner Project
This project was part of a **hackathon** conducted by **Massachusetts Institute of Technology (MIT)** as part of the *Data Science and Machine Learning: Making Data-Driven Decisions Program*. The hackathon ran from **Feb 1, 8:00 PM - Feb 16, 7:59 PM 2025**, with **over 40 teams participating**. 

**🏅 I won this competition by achieving the highest accuracy score of 0.9586821 after 38 submissions.**

---

## 📌 Problem Statement
The challenge was based on the **Shinkansen Bullet Train in Japan**, focusing on understanding passengers' experiences. The goal was to determine the **relative importance of various factors** influencing passenger satisfaction and predict whether a passenger was satisfied (1) or not (0) with their travel experience.

---

## 📂 Dataset Overview
The dataset consists of two files for both **train and test data**:
- **Surveydata_train.csv & Surveydata_test.csv**: Contains passengers' feedback on different aspects of their experience, including **seat comfort, cleanliness, catering, Wi-Fi availability**, etc.
- **Traveldata_train.csv & Traveldata_test.csv**: Includes travel-related information such as **departure delays, arrival delays, travel class, seat class, customer type**, etc.

The **target variable** was `Overall_Experience`:
- `1` → Satisfied
- `0` → Not Satisfied

---

## 🔍 Data Preprocessing
Since this was a hackathon, I tested **various data cleaning and preprocessing methods** to achieve the best performance. 
Ultimately, the following steps led to the best results:

✔ **Merging Data**: Combined `Surveydata_train.csv` and `Traveldata_train.csv` using `ID` as the key.
✔ **Handling Missing Values**:
   - Categorical columns → **One-Hot Encoding** (Replacing NAs with `0`).
   - Numerical columns → **Mean Imputation** (Age was set to `40` by default).
✔ **Feature Engineering**:
   - Created new interaction-based features.
   - Mapped categorical values into numeric form.
✔ **Ensuring Test Set Consistency**:
   - Aligned test dataset columns with the train set.
   - Saved mean values and one-hot-encoded column names to apply the same transformations to the test set.

> **Note:** This file only includes the best-performing **data preprocessing methods and machine learning model (XGBoost)**. While I experimented with **Random Forest, LightGBM, Logistic Regression, SVM, and HistGradientBoosting**, only XGBoost and the most effective filling NA method are included here for clarity.

---

## 🤖 Machine Learning Model & Optimization
For this classification problem, I tested multiple machine learning models, and **XGBoost (Extreme Gradient Boosting)** provided the best accuracy. XGBoost is a powerful ensemble learning method that improves predictions by sequentially correcting errors from previous iterations. 

### 🔧 Hyperparameter Tuning & Cross-Validation
To enhance the model’s performance, I applied **GridSearchCV with 5-Fold Cross-Validation** to systematically tune hyperparameters. This approach helps prevent overfitting and ensures the model generalizes well to unseen data. The final hyperparameters were selected after multiple iterations of testing different configurations.

The best hyperparameters determined through grid search allowed the model to achieve high accuracy by optimizing factors such as the number of trees, learning rate, tree depth, and feature sampling. 

Once the best hyperparameters were identified, the **final model was trained on the entire training dataset** and used to generate predictions for the test dataset.

---

## 🎯 Model Performance
The **final model achieved an accuracy of 0.9586821**, which was the **highest score among all participants** in the hackathon. 

### 📈 Evaluation Metric: Accuracy Score
The evaluation was based on **accuracy**, calculated as:

$$Accuracy = \frac{True Positives + True Negatives}{Total Observations}$$

---

## 📤 Submission Format
The final predictions were saved in a submission CSV file with the format:
```csv
ID,Overall_Experience
10001,1
10002,0
10003,1
...
```
---

