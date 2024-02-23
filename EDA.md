# Exploratory Data Analysis (EDA)
**2024 Valentine's Amazon Bestsellers** </br>
**Author**: Mal Sikora <br />

## Question 1
What is the distribution of star ratings (3-star, 4-star, 5-star)?
### Query
````sql
SELECT TOP 10 LEFT(title, 
                  CASE 
            WHEN CHARINDEX(',', title + ',') > 0 THEN CHARINDEX(',', title + ',') - 1
            WHEN CHARINDEX('-', title + '-') > 0 THEN CHARINDEX('-', title + '-') - 1
			WHEN CHARINDEX('.' , title + '.')>0 THEN CHARINDEX('.', title + '.') - 1
			            ELSE LEN(title) END) AS title,
	brand,
	ROUND(starsBreakdown_3star * reviewsCount, 1) AS nr_3stars,
	ROUND(starsBreakdown_4star * reviewsCount, 1) AS nr_4stars,
	ROUND(starsBreakdown_5star * reviewsCount, 1) AS nr_5stars
FROM best_sellers
````
### Results
 Outer pipes  Cell padding 
No sorting
| title                                                                                | brand          | nr_3stars | nr_4stars | nr_5stars |
| ------------------------------------------------------------------------------------ | -------------- | --------- | --------- | --------- |
| Ferrero Rocher                                                                       | Ferrero Rocher | 400.4     | 1401.5    | 17818.7   |
| HERSHEY'S NUGGETS Assorted Chocolate                                                 | HERSHEY'S      | 566.7     | 1889.1    | 15868.4   |
| LEGO Icons Flower Bouquet Building Decoration Set                                    | LEGO           | 193.9     | 969.8     | 17843.4   |
| BodyRefresh Shower Steamers Aromatherapy                                             | BodyRefresh    | 41.5      | 89        | 397.3     |
| JoJowell Shower Steamers Aromatherapy                                                | JoJowell       | 81.6      | 122.4     | 514.1     |
| ChunRun Valentines Day Gifts                                                         | ChunRun        | 0         | 1         | 1         |
| LEGO Cherry Blossoms Gift for Valentine's Day                                        | LEGO           | 2.8       | 3.9       | 45.6      |
| Body Restore Shower Steamers Aromatherapy 6 Packs              | Body Restore   | 1012.4    | 1898.3    | 8858.5    |
| 40 Date Ideas Card Games for Couples Date Night  | Tryuunion      | 51.9      | 84.4      | 486.8     |
| JOYIN 24 PCS Valentine's Day Heart Stress Balls 1.6"x1.6" for Kids                   | JOYIN          | 43.3      | 93.7      | 555.2     |


### Findings
The reviews don't have even distriubiution across products, hence further investigation will be necessary. 
</br>


## Question 2
Which product has the highest number of reviews? Show top 5
### Query
````sql
SELECT TOP 5 
			LEFT(title, CASE 
            WHEN CHARINDEX(',', title + ',') > 0 THEN CHARINDEX(',', title + ',') - 1
            WHEN CHARINDEX(':', title + ':') > 0 THEN CHARINDEX(':', title + ':') - 1
			ELSE LEN(title) END) AS title, brand, reviewsCount
FROM best_sellers
ORDER BY reviewsCount DESC;
````
### Results
| title                                                                                         | brand                | reviewsCount |
| --------------------------------------------------------------------------------------------- | -------------------- | ------------ |
| BAIMEI Jade Roller & Gua Sha                                                                  | BAIMEI               | 54895        |
| Burt's Bees Essential Everyday Beauty Valentines Day Gifts Set                                | Burt's Bees          | 40125        |
| Ferrero Collection                                                                            | Ferrero Rocher       | 29239        |
| Ferrero Rocher Collection                                                                     | Ferrero Rocher       | 28226        |
| Valentine’s Candy Variety Pack 18 Count | Bazooka Candy Brands | 27866        |

### Findings
The top product, with the most reviews is Jade Roller & Gua Sha from BAIMEI. It shows, that the beauty product keep
top 2 positions, as opposed to sweets. 
</br>


## Question 3
What is the average price of the best-selling products?
### Query
````sql
SELECT ROUND(AVG(price_value),2) AS average_price
FROM best_sellers;
````
### Results
| average_price |
| ------------- |
| 18.05         |

### Findings
On average, the price for a gift in 2024 was $18.05.
</br>


## Question 4
What is the overall distribution of reviews across different brands?
### Query
````sql
SELECT TOP 10 brand, SUM(reviewsCount) AS total_reviews
FROM best_sellers
WHERE brand IS NOT NULL
		AND reviewsCount IS NOT NULL 
GROUP BY brand
ORDER BY total_reviews DESC;
````
### Results
| brand                | total_reviews |
| -------------------- | ------------- |
| Ferrero Rocher       | 91961         |
| Burt's Bees          | 65890         |
| BAIMEI               | 54895         |
| Body Restore         | 32562         |
| Bazooka Candy Brands | 27866         |
| LEGO                 | 25298         |
| HOME SMILE           | 24615         |
| HERSHEY'S            | 22124         |
| grace & stella       | 21545         |
| Skittles             | 19772         |

### Findings
The brand with the most reviews is Ferrero Rocher. Evidently, there is a trend of the type of product
purchased by consumers. We can distinct three main cathegories: beauty products, sweets and other. 
</br>


## Question 5
Are there any products with a disproportionately high percentage of 5-star ratings?
### Query
````sql

````
### Results


### Findings
__________________________________________________________


Thank you very much!


