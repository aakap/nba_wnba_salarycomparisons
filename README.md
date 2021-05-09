# Examining Gender-Driven Salary Gaps in Professional Basketball

 

# Code
[Google Colaboratory Notebook](https://colab.research.google.com/drive/1nvf1zCmnPAUnjT9JlXlr4WBT2VerZmW8?usp=sharing)

# Abstract
There is a striking difference in pay between men’s and women’s basketball. To reconcile the many arguments about whether this pay gap is justified by the lower number of games played by players in the women’s basketball league, we conducted several analyses using available salary and player performance data provided by the NBA and WNBA. We found a 200-fold difference in salary between the highest paid players in the NBA and WNBA. Moreover, we found that there was no significant difference in the skill level and player utility across the two leagues. Star players in the WNBA performed just as well for their teams as comparable players in the NBA, despite their strikingly different salaries. We also found that the pay gap between the NBA and WNBA increases as starpower, or player performance, increases. The top players in the NBA are getting paid in spades above the top players in the WNBA. Pay inequity in sports effects more than just the players. The league as a whole suffers due to the lack of player and viewer satisfaction. In addition, youth athletes are discouraged from starting a career in professional basketball because it is hard to make a stable living. Our findings indicate that the degree of pay inequity is unjustified. We propose to increase the salary cap of the WNBA and potentially reallocate funds from the NBA to support WNBA infrastructure. We also propose to increase the salaries and exposure of the star players in the WNBA to draw more attention to their performance given the value they add to their teams. Finally, we all must come together to support the WNBA by increasing our viewership, attending games, and purchasing merchandise. Overall, this report walks through the data justifying the significance of the pay inequity and outlines recommendations on how to mitigate this issue to encourage gender equality in professional basketball, which can set the precedent for other sports and professions. 

# Data Sources
## Raw Data Sources:
[WNBA Player Performance Stats (Website)](https://www.rotowire.com/wnba/stats.php) | [WNBA Player Performance Stats (CSV)] (https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/wnba-player-performance-stats.csv)
[WNBA Player Salary Stats (Website)](https://www.spotrac.com/wnba/rankings/2020/cap-hit/) | [WNBA Player Salary Stats (CSV)](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/wnba-salary-stats.csv)
[NBA Player Performance Stats (Website)](https://www.nba.com/stats/leaders/?Season=2020-21&SeasonType=Regular%20Season&PerMode=Totals) | [NBA Player Performance Stats (CSV)](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/nba-player-performance-stats.csv)
[NBA Player Salary Stats (Website)](https://www.basketball-reference.com/contracts/players.html) | [NBA Player Salary Stats](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/nba-salary-stats.csv)

## Manipulated Data Files:
[WNBA Player Performance Stats with Salaries](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/wnba-player-and-salary-stats-2020.csv)
[NBA Player Performance Stats with Salaries](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/mnba-player-and-salary-stats-2020.csv)
[Excel file used to produce these two data sets](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/wnba-nba-player-performance-and-salary-stats.xlsx)

# Background 
The gender pay gap manifests across all industry, but is especially pronounced in basketball. Recently in the [news](https://www.espn.com/mens-college-basketball/story/_/id/31141363/ncaa-budget-men-basketball-tournament-almost-twice-much-women-budget), the NCAA's March Madness tournament budgeted almost double for the men's tournament than it did for the women's tournament, leaving the womens' teams without access to gym equipment, sponsorship items, and adequate facilities. This stark contrast materializes across the sports industry, especially in the salaries of WNBA players compared to that of the NBA. It is common knowledge that male athletes make more than female athletes make, but the magnitutde of that difference is often the matter of millions. A hard to justify statistic, many sportscasters and fans claim that men's sports is simply "more interesting to watch" or that the men are "better players." To determine the degree of injustice in the salaries, we examined the difference between salaries for WNBA and NBA players based on key metrics that determine player performance such as games played and points scored. This analysis helps us understand the question of ***can we predict salaries based on player performance?"** 


# Data Question
The specific data question we looked at had two parts:
1. How are player perforamnce metrics related to salary?
2. For players in the WNBA and NBA with comparable performance, what is the discrepancy in salary?

# Results 

# Exploratory Regressions
Figure 1a. Salary vs Games Played for NBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/mens_salaryvgames.png)

Figure 1b. Salary vs Games Played for NBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/boxplotmens.png)

Figure 2a. Salary vs Games Played for WNBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/womens_salaryvgames.png)

Figure 2b. Salary vs Games Played for WNBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/boxplotwomens.png)

Multivariate Regression Results:
NBA salary = -56900*games played + 9609*rebounds + 10220*points + 30600*assists
R^2 = 0.686

WNBA salary = 3533*games played + 37 *rebounds + 14.7*points + 545.8 *assists
R^2 = 0.774

From these results, it is immediately clear that the men's salaries are significantly higher than the women's salaries just by looking at the units of the axes, regardless of games played. The regression visualized in Figures 1 has an R^2 of 0.46 whereas the R^2 of the regression in Figures 2 is 0.75. Thus, the WNBA has a stronger linear relationship between salary and games played. We can see that there are fewer outliers of women having high salaries with few games played comparatively as there are several men's players who played few games but have similar salaries to those who played 60 games. This may be due to injuries that prevented players from getting court-time after their salaries and contracts were negotiated. It is also important to note that there are far fewer games played in the WNBA than in the NBA, which may account for some difference in salary. Based on the multivariate regression results, all performance metrics positively influence salary as expected, except for the number of games played for men's teams. This is likely a discrepancy and could be caused by the unexpected injuries as aforementioned. Games played has the largest impact on salary for women's teams. Overall, the data shows a stronger linear fit for predicting slaary based on performance metrics for WNBA compared to the NBA, which may suggest that external factors such as sponsorships and player "hype" are contributors to salary for men's basketball.

# Principle Component Analysis
To build a preliminary model for basketball player salaries, we performed a principal component analysis (PCA) using salary as the target variable and minutes played per game, points scored per minute, assists per minute, and rebounds per minute as input variables (all standardized as z-scores). This PCA was performed separately on a WNBA data set and a NBA data set. The weights were mildly different but comparable and were as follows:

WNBA weights...
Minutes played per game*: 0.52000132
Points per minute: 0.27180841
Assists per minute: 0.12897109
Rebounds per minute: 0.0711918

NBA weights...
Minutes played per game: 0.4856832
Points per minute: 027166118
Assists per minute: 0.1420279
Rebounds per minute: 0.10062772

`*WNBA games are 40 minutes in length and NBA games are 48 minutes in length. To prevent this difference from skewing the PCA model, WNBA minutes figures were multiplied by 48/40 = 1.2

We see that minutes played per game is slightly more influential in our projection for value in the WNBA than it is for the NBA whereas assists per minute and rebounds per minute are slighly more influential in our projection for value in the NBA than for the WNBA. However, it is noteworthy that the weights are quite similar for both leagues, suggesting that players with similar performance metrics in each league offer comparable value and should have comparable salaries using this model.

Models are invaluable in that they aren't as susceptible to human biases and perceptions, but it is useful to check the model results to see if they seem even remotely reasonable. As a quick eye check, it is good to see who the PCA model ranks as the top-10 players in each league. The purpose of the PCA is not to make a judgement on who the best players in the league are, but it is important to verify that players widely regarded as elite and at the top of each league are in the top-tier of the model. The top fifteen players in each league are as follows:

Figure 3a: Top 15 WNBA Players by PCA Model
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/PCA%20Top%20WNBA%20Players.png)

Figure 3b: Top 15 NBA Players by PCA Model
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/PCA%20Top%20NBA%20Players.png)

These lists both pass the eye test and would be considered to be quite reasonable in the judgement of most fans. As a more tangible source of validation, Google's top professional athlete listings upon googling "best wnba players" and "best nba players" results in 10 of our top 15 WNBA players and 12 of our 15 top NBA players appearing on the list.

Now that we have proof-of-concept for the PCA model, it's time to use the model to explore the discrepancy of salaries of players of comparable value in the PCA model based on league. It was important to build the PCA model separately for each league because actual salary figures vary severely by league and the model would fail to accurately model salary in either league if both were done together (instead getting stuck in the middle). However, as a means of evaluating both WNBA and NBA players all together, we averaged each weight from the two individual PCA models together to form an overall, non-league-specific set of weights. These weights are as follows: 

Minutes per Game: 0.5028422613056367
Points per Game: 0.271784794225057
Assists per Game: 0.1354994985248121
Rebounds per Game: 0.0898344594449426

We then used these weights to determine an overall projected player value score for every WNBA and NBA player by averaging the WNBA and NBA weights for each variable, resulting in the following overall weights giving us a projected player value score:

Minutes per Game: 0.50
Points per Game: 0.27
Assists per Game: 0.14
Rebounds per Game: 0.09

This projected player value score was then compared to players' actual salaries. WNBA players are plotted in blue and NBA players are plotted in red.

![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/Actual%20Player%20Salary%20vs.%20Projected%20Player%20Value%20Differentiated%20by%20League.PNG)
*Note*: For the HTML version of this visual, which labels each dot with coordinate info and the player that it corresponds to, download and view this [file](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/actual-player-salary-versus-projected-player-value-differentiated-by-league).

This graph makes it very clear that NBA players and WNBA players who have extremely comparable player performance and projected player value scores make vastly different salaries due to the pay gap. For any given x-axis value (projected player value score), the red dots are significantly below the blue dots when it comes to the y-axis (actual salary). There is no merit to any conception that there is a player-performance driven reason for WNBA players to be underpaid relative to NBA players.

However, stopping at the point of identifying that WNBA players are underpaid relative to comparable NBA players would not do the problem justice. In particular, the pay gap between comparable WNBA and NBA athletes from a percentage perspective increases with the star status of the player.

Figure 4: Pay Gap by Projected Value Tier
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/PCA%20Pay%20Gap%20by%20Projected%20Value%20Tier.png)

NBA players whose projected value is in the 50th percentile or lower make an average of between 2,000% and 5,500% of the salaries of WNBA players in the same boat. Even more pronoucned, NBA stars make nearly 18,000% of the salary of similarly performing WNBA stars. To put this in a more anecdotal perspective, WNBA star Brittney Griner and NBA star John Wall have nearly identical projected value scores (1.15 and 1.18) yet John Wall makes $41,300,000 million per year while Griner makes $215,000 per year.
The last player on the bench on an NBA team makes nearly four times that of the highest paid players in the WNBA. The WNBA and NBA exhibit an undeniable pay gap across the board; this pay gap is especially pronounced when it comes to the stars of each league.



