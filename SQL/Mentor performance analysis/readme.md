Overview

This project analyzes user submission data from a mentor-based learning platform to evaluate performance, engagement, and improvement trends.
It demonstrates SQL skills in data aggregation, conditional logic, ranking, and time-based analytics using PostgreSQL.

The main business goal is to help identify:

Which mentors or learners are most consistent performers
Which users need intervention or training
When engagement and accuracy peak throughout the week
🗂️ Project File
📄 Mentor Performance Analysis.sql
🧱 Database Schema
Table: user_submissions

Includes:

Table creation and data loading
Daily and weekly performance tracking
Correct vs. incorrect submission analysis
Leaderboard generation and ranking logic
🧱 Database Schema
Table: user_submissions

Column	Type	Description
id	SERIAL (PK)	Unique submission ID
user_id	BIGINT	Unique user/mentor identifier
question_id	INT	Question or task identifier
points	INT	Points awarded (+ve for correct, -ve for incorrect)
submitted_at	TIMESTAMP WITH TIME ZONE	Submission timestamp
username	VARCHAR(50)	User name for reporting
🔍 Business Context & Value
This analysis simulates a mentorship or learning platform where users submit answers or exercises.
Each submission is scored to track accuracy, activity, and overall contribution quality.

The results can be used by the business to:

Recognize top performers and consistent mentors for rewards or promotions
Identify users struggling with accuracy to provide coaching
Track weekly and daily engagement trends to optimize session timing
Support data-driven mentor evaluation and performance-based incentives
📊 Analytical Questions Answered
1️⃣ User Summary Stats
List distinct users with their total submissions and total points earned.

2️⃣ Daily Performance
Calculate each user's daily average points to track short-term performance consistency.

3️⃣ Top Performers per Day
Identify the top 3 users each day with the highest number of correct submissions using window functions.

4️⃣ Incorrect Submission Analysis
Find the top 5 users with the most incorrect submissions and compare them against their correct attempts.

5️⃣ Weekly Leaderboard
Rank users weekly by total points earned and select the top 10 performers per week using DENSE_RANK().

🧩 Example Query Snippets
-- Q1. Distinct users and their stats
SELECT 
    username,
    COUNT(id) AS total_submissions,
    SUM(points) AS points_earned
FROM user_submissions
GROUP BY username
ORDER BY total_submissions DESC;
