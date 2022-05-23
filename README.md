# Predicting the NBA's Most Valuable Player
## Introduction
The purpose of this project is to create a machine learning model that web scrapes NBA data and predicts the top five players with the most votes for the NBA's Most Valuable Player (MVP) award. There are essentially 3 steps for this project:
1. Scrape NBA data using BeautifulSoup and Selenium
2. Clean the data
3. Create, train, and test the machine learning model

Note: The data is scraped from [basketball-reference.com](https://www.basketball-reference.com "Title")

## Procedure
#### Error Metric
To track the effectiveness and correctness of the algorithms, I used a custom metric that returns an average precision as follows. The metric assigned one point if the algorithm was able to correctly predict a player in the top 5 of MVP votes. The pseudocode is as follows:
```
PROGRAM ErrorMetric:
  found = 0
  seen = 1
  FOR each player
    IF player is in top five MVP votes
      precision score = found / seen
  return AVG(all precision scores)
```

#### Backtesting
Since there are only 31 years of modern MVPs, backtesting has helped doubly check whether the model is accurate or not. Instead of running this error metric solely on validation and test data, backtesting for the previous 26 years gives a better estimate of what the error is truly like.

#### Random Forest Regression
Although a linear regression was initally used, a random forest regression showed a much more improved error metric. Additionally, it also allowed for categorizing the Team and Position labels, since in a linear regression, they would be taken into account. 

## Results
**Update: 5/22/22**
The newewst model now shows an **92.5% success** rate of identifying the top 5 players with the most MVP votes. In this new model, advanced statistics were added as features for the model, and the number of estimators for the random forest regression was increased. The 2021-22 season was taken as testing data, and the orders can be seen in the table below.
|     Predicted Rank    |      Actual Rank      |
|:---------------------:|:---------------------:|
| Nikola Jokic          | Nikola Jokic          |
| Giannis Antetokounmpo | Joel Embiid           |
| Joel Embiid           | Giannis Antetokounmpo |
| Luka Doncic           | Devin Booker          |
| LeBron James          | Luka Doncic           |

Although the model identified 4 of the top 5, the order is still not perfect. 


The current model, which is still improving, shows an **85.4%** success rate of identifying the top 5 players with the most MVP votes. The 2021-22 season was taken as testing data, and the orders can be seen in the table below.
|     Predicted Rank    |      Actual Rank      |
|:---------------------:|:---------------------:|
| Devin Booker          | Nikola Jokic          |
| Joel Embiid           | Joel Embiid           |
| Ja Morant             | Giannis Antetokounmpo |
| Nikola Jokic          | Devin Booker          |
| Giannis Antetokounmpo | Luka Doncic           |

Although the model identified 4 of the top 5, the order is still not perfect. This will constitute as the next steps as the chosen algorithms will aim to become better and better.
