# Personalized Student Recommendations System🧑‍🎓

#Overview📌

This project implements a personalized student recommendation system based on quiz performance data. By analyzing students' quiz submissions, the system generates recommendations that help students focus on weak areas, improve their understanding, and enhance their overall preparation.

App Link
App: NEET Testline (Available on Google Play)


# Problem Statement📌

The task is to analyze the student's quiz performance by looking into various aspects such as:

Weak Topics: Identify the topics where the student is performing poorly.
Difficulty Levels: Suggest appropriate difficulty levels based on the student’s performance.
Improvement Trends: Highlight how the student’s performance has evolved over time.
Personalized Recommendations: Provide actionable steps to help students improve their preparation.


# Datasets📌

There are two primary datasets that the system works with:

Current Quiz Data: Contains details of the user’s latest quiz submission including questions, topics, responses, etc.
https://jsonkeeper.com/b/LLQT

Data Source: API Endpoint
Historical Quiz Data: Performance data from the last 5 quizzes for each user, including scores and response maps.
https://api.jsonserve.com/rJvd7g

Data Source: API Endpoint


# Features & Approach📌
The system is designed to analyze quiz performance and provide personalized recommendations for improvement. The following steps were followed to implement the system:

# Steps for Solution Implementation

#Step 1: Data Loading and Preprocessing
We begin by loading the datasets and preprocessing the data. This involves cleaning the data by removing missing values, formatting the data, and ensuring consistency across different fields.

# Loading current and historical quiz data
current_quiz_data = pd.read_json("current_quiz_data.json")
historical_quiz_data = pd.read_json("historical_quiz_data.json")

# Preprocessing: Cleaning missing values and formatting
current_quiz_cleaned = current_quiz_data.dropna()
historical_quiz_cleaned = historical_quiz_data.dropna()


# Step 2: Feature Engineering📌

# Extracting important features
current_quiz_cleaned['score'] = current_quiz_cleaned['score'].astype(float)
historical_quiz_cleaned['accuracy'] = historical_quiz_cleaned['accuracy'].astype(float)

# Step 3: Exploratory Data Analysis (EDA)📌

Perform an exploratory analysis to understand patterns in the data. This includes looking at the distribution of scores, accuracy, and identifying weak topics.

import seaborn as sns
import matplotlib.pyplot as plt

# Visualizing Score Distribution📌
sns.histplot(current_quiz_cleaned['score'], kde=True)
plt.title('Current Quiz Score Distribution')
plt.xlabel('Score')
plt.ylabel('Frequency')
plt.show()

![Image](https://github.com/user-attachments/assets/38ea9d89-c904-4f86-9a3c-2d0da5701bd8)


# Step 4: Personalized Recommendations📌
Based on the performance, we generate recommendations for students. These could be to focus on specific topics or difficulty levels.

python

# Example recommendation generation
if current_quiz_cleaned['score'].mean() < 50:
    recommendation = "Focus on easier topics to improve your score."
else:
    recommendation = "Challenge yourself with harder questions to further improve."
print(recommendation)


# Step 5: Visualization of Weak Topics📌
We visualize weak topics for a student by analyzing the topics in the dataset and identifying the ones with the lowest scores.

# Plotting weak topics based on average scores
weak_topics = current_quiz_cleaned.groupby('quiz_topic')['score'].mean().reset_index()
sns.barplot(x='score', y='quiz_topic', data=weak_topics, palette="coolwarm")
plt.title('Weak Topics Based on Average Score')
plt.xlabel('Average Score')
plt.ylabel('Topic')
plt.show()


# Step 6: Evaluation and Testing📌
After implementing the recommendations, we evaluate the output to ensure the accuracy of the insights.

# Check recommendation accuracy
assert recommendation in ["Focus on easier topics to improve your score.", "Challenge yourself with harder questions."]


# Step 7: Modular and Clean Code📌
The code has been broken down into functions for better readability and maintainability.

# Step 8: Final Report📌
The final report includes visualizations, insights, and a summary of the results.

Visualization of the student’s performance trends.
Summary of weak topics and performance improvement.
Recommendations for the student to focus on.


# Visualizations📌
Here are some key visualizations that summarize the student's performance:

1. Score Distribution (Current Quiz)

2. Weak Topics


# Usage Instructions📌
Installation
Clone the repository to your local machine
git clone https://github.com/your-username/student-recommendations.git

Install the required dependencies
pip install -r requirements.txt

# Running the Script📌
To run the script, simply execute the Python file:
python recommendation_system.py


# Conclusion📌
The personalized recommendation system developed in this project helps students improve their preparation for quizzes by providing insights into weak topics, recommended difficulty levels, and actionable steps for improvement.

