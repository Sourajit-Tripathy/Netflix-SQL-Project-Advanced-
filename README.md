# Netflix-SQL-Project-Advanced
![ logo](https://github.com/Sourajit-Tripathy/Netflix-SQL-Project-Advanced-/blob/main/logo.png)

## Objectives

## 📌 **Project Overview**

This project performs an end-to-end advanced SQL analysis on the Netflix dataset using **MS SQL Server**.  
It demonstrates advanced querying techniques such as CTEs, window functions, multi-value field normalization, date parsing, and text classification to extract meaningful insights from semi-structured data.

## ✅ **Key SQL Tasks Performed (with Explanation)**

### **1️⃣ Content Analysis — Movies vs TV Shows**
Used `GROUP BY` to compare the distribution of Movies and TV Shows.  
**Insight:** Helps understand platform-level content strategy.


### **2️⃣ Rating Dominance by Category (Window Functions)**
Used **CTEs** + `RANK() OVER(PARTITION BY type ORDER BY count DESC)` to identify the most common rating for each content type.  
**Skill:** Window functions for ranking and analytical insights.


### **3️⃣ Normalizing Multi-Value Fields (STRING_SPLIT + CROSS APPLY)**
Split comma-separated fields for **country, genre, cast**, then normalized them using `CROSS APPLY`.  
**Skill:** Handling non-normalized, multi-valued columns.


### **4️⃣ Identifying the Longest Movie (String Parsing)**
Extracted numeric duration from strings like “120 min” using `LEFT`, `CHARINDEX`, and `CAST`.  
**Skill:** String parsing + numeric extraction.


### **5️⃣ Time-Based Analysis (Date Parsing & Filtering)**
Used `PARSE()` and `DATEADD()` to find content added in the last 5 years.  
**Skill:** Date cleaning, conversion, and temporal analysis.


### **6️⃣ TV Shows Season Count Extraction**
Filtered TV Shows having more than 5 seasons by parsing numeric values embedded in text.  
**Skill:** Extracting numbers from irregular text fields.


### **7️⃣ Actor & Director Frequency Insights**
Used `STRING_SPLIT` on the cast field to identify top recurring actors, especially for India-produced content.  
**Skill:** Contributor-level analytics from multi-value text.

### **8️⃣ Genre Popularity Analysis**
Normalized genres using `STRING_SPLIT` and calculated their frequency.  
**Skill:** Understanding content category trends.


### **9️⃣ Keyword-Based Text Classification**
Built a rule-based classifier using `CASE` to label content as **Good** or **Bad** based on keywords like *kill* or *violence*.  
**Skill:** Basic text classification using SQL logic.



## 🎓 **Skills & Learning Outcomes**

This project strengthened knowledge in:

- Advanced SQL **string functions**  
- **Window functions** (`RANK`, `OVER`)  
- **CTEs** for structured query logic  
- Multi-value handling with **STRING_SPLIT + CROSS APPLY**  
- **Date parsing**, conversion & filtering  
- Data cleaning & transformation  
- Rule-based **text classification**  
- Working with real-world messy datasets  




