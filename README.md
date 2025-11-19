# Netflix-SQL-Project-Advanced
![ logo](https://github.com/Sourajit-Tripathy/Netflix-SQL-Project-Advanced-/blob/main/logo.png)

## Objectives
📌 Project Overview

This project focuses on performing advanced SQL analysis on a Netflix dataset.
It covers window functions, STRING_SPLIT, CTE pipelines, date parsing, ranking, text categorization, and data cleaning techniques, demonstrating strong analytical and SQL engineering skills.

##create database netflix
use netflix
select * from netflix_data


-- 1. Count the Number of Movies vs TV Shows
select type,count(show_id) as total_shows from netflix_data
group by type
order by total_shows desc 

-- 2. Find the Most Common Rating for Movies and TV Shows

with cte as (select type, rating, count(*) as total_count from netflix_data
group by type,rating
), 
cte2 as(
select type,rating,total_count, rank()over(partition by type order by total_count desc) as rank
from cte)

select type,rating from cte2
where rank = 1;

-- 3. List All Movies Released in a Specific Year (e.g., 2020)

select * 
from netflix_data
where release_year = 2020 and type ='movie'

-- 4. Find the Top 5 Countries with the Most Content on Netflix


SELECT TOP 5 country, COUNT(*) AS total_content
FROM (
    SELECT 
        LTRIM(RTRIM(value)) AS country
    FROM netflix_data
    CROSS APPLY STRING_SPLIT(country, ',')
) AS t1
WHERE country IS NOT NULL
GROUP BY country
ORDER BY total_content DESC;


-- 5. Identify the Longest Movie

select * from netflix_data

SELECT *
FROM netflix_data
WHERE type = 'Movie'
ORDER BY 
    CAST(
        LEFT(duration, CHARINDEX(' ', duration + ' ') - 1)
    AS INT) DESC;

-- 6. Find Content Added in the Last 5 Years

    SELECT *
FROM netflix_data
WHERE PARSE(date_added AS DATE USING 'en-US') 
      >= DATEADD(YEAR, -5, GETDATE());
   
   -- 7.  Find All Movies/TV Shows by Director 'Rajiv Chilaka'

select * from 
( select *,LTRIM(RTRIM(value)) as director_name from netflix_data CROSS APPLY string_split(country,','))
as t where director = 'Rajiv Chilaka'

select * from netflix_data where director like '%Rajiv Chilaka%'

-- 8. List All TV Shows with More Than 5 Seasons

select type, title from netflix_data
where type = 'TV Show' and cast(left(duration,charindex(' ' ,duration + ' ')-1) as int) >5

-- 9. Count the Number of Content Items in Each Genre
select* from netflix_data

select LTRIM(rtrim(value)) as genre, 
count(*) as total_count from netflix_data 
cross apply string_split(listed_in, ',')
group by value 

select(value) as genre from netflix_data cross apply string_split(listed_in, ',')
group by value


-- 10.Find each year and the average numbers of content release in India on netflix.

select TOP 5  country,
    release_year,
    COUNT(show_id) AS total_release,
    ROUND(count(show_id)/(select count(show_id) from netflix_data where country = 'India')*100,2)
    AS avg_release
FROM netflix_data
WHERE country = 'India'
GROUP BY country, release_year
ORDER BY avg_release DESC

-- 11. Find the Top 10 Actors Who Have Appeared in the Highest Number of Movies Produced in India

select top 5 (value) as casts,count(*) as total from netflix_data cross apply string_split( cast, ',') 
where country = 'India'
group by value
order by total desc

-- 12. Categorize Content Based on the Presence of 'Kill' and 'Violence' Keywords
WITH cte  AS (
    SELECT 
        CASE 
            WHEN description LIKE '%kill%' THEN 'Bad'
            WHEN description LIKE '%violence%' THEN 'Bad'
            ELSE 'Good'
        END AS category
    FROM netflix_data
)

SELECT 
    category,
    COUNT(*) AS total
FROM cte
GROUP BY category;
