![Baseball-Teams-Lakeland-Florida](https://user-images.githubusercontent.com/100230332/171307514-6cdd4106-e46a-4c58-a5cd-d26280038814.jpeg)

# Predicting MLB Free Agent Salaries
## Capstone Project


### Author
---
- Jordan Kominsky: 
[LinkedIn](https://www.linkedin.com/in/jordan-kominsky/) | 
[GitHub](https://github.com/jskominsky) | 
[Email](mailto:jskominsky@gmail.com)

### Business Understanding
---

Agents not having realistic expectations and not understanding what their clients will be offered by general managers, puts them at a competitive disadvantage.  It can make their clients upset, and can lead to being fired, when the players don't receive the contract offers they were told by their agent to expect.  It also puts agents at a competitive disadvantage in negotiations with general managers.

### Overview
---

I was hired by the Boras Corporation to create a predictive model to better predict MLB free agent hitters salaries.  After these major blunders with Michael Conforto and Mike Moustakas's contracts, the Boras Corparation has realized that they need to be able to better predict free agent salaries so they can tell their clients what to expect, and to give them a leg up in negotiations with MLB general managers.

In order to address the problem that the Boras Corporation is facing, I will use the following regression models to improve the companies ability to predict free agent salaries:

1. Random Forest Regression
2. XGBoost Regressor
3. XGBoost Random Forest (XGBRF) Regressor

I chose to use these models because they all can handle multicollinearity and have the ability to tell me feature importance.  Feature importance is important because the agents can tell their clients what part of their game to improve during the offseason to give them the best chance at a bigger contract. 

### Data Understanding
---

My original dataset was found at [Kaggle.com](https://www.kaggle.com/datasets/open-source-sports/baseball-databank).  The dataset contained 20 CSV files that included MLB data from 1871-2021. Of those 20 CSV's I used the following: 
- AllstarFull.csv
- AwardsPlayes.csv
- AwardsSharePlayers.csv
- Batting.csv
- People.csv
- Salaries.csv
- Teams.csv

While the batting.csv statistics went through 2021, the salaries only went through 2016, so I wanted to find data for the salaries from 2017-2021.  I found this data at [Cot's Baseball Contracts](https://legacy.baseballprospectus.com/compensation/cots/). This data included salary data from 2000-2021, and helped me fill in 1600 values in the original salary data that were null. While searching for more salary data to fill in the null values, I found data at [The Baseball Cube](https://www.thebaseballcube.com/content/store/). This data included salary data from 1985-2022. I purchased this data set for $20. It helped me fill in 6,449 null values in the original salary data.

I subsetted my data to only use data from 1984-2021.  I also subsetted my data to only include players who played at least 6 seasons (so the only players included were ones who played long enough to make it to free agency).  I then made a new dataframe where the columns of the dataframe were the players' hitting statistics for each of his first 6 seasons, and included the players' average salary of his 7th, 8th, 9th, and 10th seasons (or less if he didn't play 10 seasons). This created a dataframe that was 1063 rows (one for each player in my dataset that played 6 or more seasons) by 131 columns.  The columns included the players' hitting statistics for his first 6 seasons, along with whether he made the All Star Game, whether he started the All Star Game, whether he won an award, or got votes for MVP or Rookie of the Year,  whether his team made the playoffs, and if his team won the World Series.

### Methods
---


### Conclusion
---

My final model was a Random Forest gridsearch.  This model is able to account for nearly 70% of the variance within my data.  My final model has an RMSE of 3,063,911, which means the error of our predictions is just over $3 million.  This seems like a fair amount of error to expect when agents and general managers are negotiating a contract. However, I believe that once I am able to detrend the salary data, my model will have an even lower mean squared error.  This is important because the average salary in MLB has gone from \\$371,571 in 1985 to \\$4,414,184 in 2022, according to [Baseball Reference](https://www.baseball-reference.com/bullpen/Minimum_salary). By using regression models to help predict MLB free agent salaries, I have given The Boras Corporation a competitive advantage when dealing with clients and when negotiating new contracts with General Managers.  

### Limitations
---

1. The fielding data that was included was very incomplete and did not include any of the truly relevant fielding statistics.
2. The original salary data was pretty incomplete, and without the data set purchased from [The Baseball Cube](https://www.thebaseballcube.com/content/store/) it would have been very difficult to succesfully complete this model, because I would not have had enough data.


### Next Steps
---

1. Find a way to account for the 2020 Pandemic Shortened 60 Game Season.
2. Detrend the salary data so the yearID isn't the most important feature and the players' statistics were more important.
3. Include data on players' service time so I can more accurately predict when a player is going to free agency.
4. Find reliable fielding data so I can include a players' fielding statistics.
