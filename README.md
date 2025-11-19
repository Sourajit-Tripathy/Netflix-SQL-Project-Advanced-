# Netflix-SQL-Project-Advanced
![ logo](https://github.com/Sourajit-Tripathy/Netflix-SQL-Project-Advanced-/blob/main/logo.png)

## Objectives
📌 Project Overview

This project focuses on performing advanced SQL analysis on a Netflix dataset.
It covers window functions, STRING_SPLIT, CTE pipelines, date parsing, ranking, text categorization, and data cleaning techniques, demonstrating strong analytical and SQL engineering skills.




## ✅ Key SQL Tasks Performed (with Explanation)

1️⃣ Content Analysis: Movies vs TV Shows

Used GROUP BY to count distribution across content types.

Helps understand platform content strategy.

2️⃣ Rating Dominance by Category (Window Function)

Used CTE + RANK() OVER(PARTITION BY) to identify the most frequent rating for movies and TV shows.

Demonstrates expertise in window functions.

3️⃣ Extracting Multi-value Fields (STRING_SPLIT + CROSS APPLY)

Split comma-separated values for country, genre, and cast.

Used CROSS APPLY to normalize data for frequency analysis.

Learned handling non-normalized datasets in SQL.

4️⃣ Identifying Longest Movie (Data Extraction from String)

Parsed duration using LEFT, CHARINDEX, and CAST.

Shows string manipulation + numeric extraction ability.

5️⃣ Time-Based Analysis (Date Functions)

Parsed date using PARSE() and extracted content added in the last 5 years.

Demonstrated date conversion, validation, and filtering skills.

6️⃣ Season Count for TV Shows

Extracted season count using string parsing and applied numeric filtering.

Shows understanding of irregular numeric values inside text fields.

7️⃣ Actor and Director Frequency Analysis

Performed cast splitting and aggregated counts to find top actors in India-produced content.

Shows ability to build insights from semi-structured text columns.

8️⃣ Genre Popularity Breakdown

Used STRING_SPLIT to extract all genres and calculate frequency.

Supports content recommendation and trend analysis use cases.

9️⃣ Text Classification (Keyword Flagging)

Categorized descriptions as Good/Bad based on keywords like “kill” and “violence”.

Demonstrates ability to build rule-based text classifiers using SQL.

## 🎓 Skills & Learning Outcomes

By completing this project you learned:

How to perform advanced SQL string manipulation

Use of window functions for ranking

Applying CTEs for clean step-wise analysis

Using STRING_SPLIT + CROSS APPLY for multi-value fields

Date parsing and temporal analysis

Dataset cleaning + transformation

Rule-based text classification using SQL conditions
