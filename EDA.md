# Exploratory Data Analysis (EDA)
**2024 Valentine's Amazon Bestsellers** </br>
**Author**: Mal Sikora <br />

## Question
What are the top 5 products with the highest average rating?
### Query
````sql
SELECT title, AVG((3 * starsBreakdown_3star + 4 * starsBreakdown_4star + 5 * starsBreakdown_5star) / 100) AS avg_rating
FROM best_sellers
GROUP BY title
ORDER BY avg_rating DESC
LIMIT 5;
````
### Results

| First Header  | Second Header |
| ------------- | ------------- |
| Content Cell  | Content Cell  |
| Content Cell  | Content Cell  |

### Findings
The small amount of reviews might lead to higher "worst_reviews" value hence, better approach would be 
to have reviewsCount > certain amount, let's explore what is the average number of "reviewsCount"


