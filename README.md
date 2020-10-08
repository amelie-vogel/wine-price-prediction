#  Prediction of French Wine Prices

## Dataset 

### Description 
The dataset comes from the scraping of websites dedicated to wine.

It consists of 48 features and 3,600 rows - each example is one vintage of a wine.

The features are composed of numerical and categorical attributes such as: vintage, id, name, type of the wine (red or white), id, name of the winery, country, region, appelation of the wine, biodynamic wine or not, natural wine or not, level of acidity, type of body, alcohol content (%), number and type of awards won, ratings of the wine (grade from 1 to 5), year of production, grapes that compose the wine etc.

As the database is extremely imbalanced in favor of French (conventional) wine, I decided to focus on French wine only.

I used the feature *median_price* as a label for my predictive model, since I wanted to predict the price of a specific wine. The median has been computed by taking into account the volume of the priced bottles.

The whole dataset is the private property of Eldiias, but you can find a pickel file named *wine_dataset_sql*.


## Cleaning The data

Cleaning the data was an important part of the project, as the database came from webscraping. 

I cleaned the data in SQL and python, getting rid of duplicates, missing values, and formatting the values.


# Exploratory Data Analysis

## Visualization

The exploratory part of the analysis let me suspect a strong relationship - either linear or quadratic - between the ratings and the prices, but also between the years of production and the prices, as shown below:

![image](https://user-images.githubusercontent.com/63364114/95489259-eebc6300-0996-11eb-97da-f21f51bc764b.png)

![image](https://user-images.githubusercontent.com/63364114/95489339-0d225e80-0997-11eb-8281-ca2fa475b221.png)

![image](https://user-images.githubusercontent.com/63364114/95489347-114e7c00-0997-11eb-9b65-ba2620be5985.png)


We also see an important disparity between grapes and regions : 

![image](https://user-images.githubusercontent.com/63364114/95489681-7b672100-0997-11eb-97f0-af2cf277a6b9.png)

![image](https://user-images.githubusercontent.com/63364114/95489718-84f08900-0997-11eb-9760-18d3613a26b2.png)

But, paradoxically, there seems to be a reversed relationship between the number of awards won and the prices : 

![image](https://user-images.githubusercontent.com/63364114/95489902-be28f900-0997-11eb-8f9a-25a80cabc463.png)
 
This can be explained by at least two reasons:
- most of wines in the dataset have no award, so the rewarded wines might be not significant
- famous and expensive wines do not compete for awards as they are already considered top of the range - in France, awards go to cheaper wines that need to build a reputation.


# Inferential Statistics

## Confidence Interval For The Price Mean

![image](https://user-images.githubusercontent.com/63364114/95493255-82dcf900-099c-11eb-9333-ff345c0f951b.png)

After visualizing the distribution of the prices, it seemed relevant to compute a confidence interval for the mean of the prices, using scipy. 

##### Results: 
The average price of French wine falls between 69.3€ and 73.7€, with certainty 95%.

## Hypothesis Testing

##### Research Question:
Is French natural/biodynamic wine significantly more acidic than French conventionnal wine, on average ?

##### T-Test for difference in population proportions
###### Populations: 
All conventional French wines + all biodynamic and natural French wines - both following a binomial distribution.

###### Parameter of Interest: 
p1 proportion of wines with acidity "élevée" among conventional wines ; p2 proportion of wines with acidity "élevée" among biodynamic and natural wines.

###### Null Hypothesis: p1 = p2

###### Alternative Hypthosis: p1 > p2

###### Data/sample: 
14 biodynamic and natural French wines, a proportion p1 = 0.93 for biodynamic and natural wines with acidity "élevée" ; 215 conventional French wines, a proportion p2 = 0.81 for conventional wines with acidity "élevée"


# Supervised Learning: Regression Models

After working separately with different variables on 3 different models of regression - linear regression and random forest - (1: variables ratings and year, 2: variables ratings and region, 3: variables ratings and grapes), I wrapped up all the variables in one model of regression that reached satisfying R-squared.

##### Results with Linear Regression:
 
Train score: 0.88
Test score: 0.88

(taking the log of the datapoints since it appeared more like a quadratic relationship in the visualization)

##### Results with Random Forest: 
Train score: 0.75
Test score: 0.76

(taking the log of the datapoints)



## Contact me
[LinkedIn](https://linkedin.com/in/amelie-vogel-/)

[GitHub](https://https://github.com/amelie-vogel/)
