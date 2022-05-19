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

#### Backtracking
