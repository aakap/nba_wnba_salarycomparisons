# Examining Gender-Driven Salary Gaps in Professional Basketball

 
# Data Source
[Zip File of Initial Data Files]() | [Website]()

# Background 
The gender pay gap manifests across all industry, but is especially pronounced in basketball. Recently in the [news](https://www.espn.com/mens-college-basketball/story/_/id/31141363/ncaa-budget-men-basketball-tournament-almost-twice-much-women-budget), the NCAA's March Madness tournament budgeted almost double for the men's tournament than it did for the women's tournament, leaving the womens' teams without access to gym equipment, sponsorship items, and adequate facilities. This stark contrast materializes across the sports industry, especially in the salaries of WNBA players compared to that of the NBA. It is common knowledge that male athletes make more than female athletes make, but the magnitutde of that difference is often the matter of millions. A hard to justify statistic, many sportscasters and fans claim that men's sports is simply "more interesting to watch" or that the men are "better players." To determine the degree of injustice in the salaries, we examined the difference between salaries for WNBA and NBA players based on key metrics that determine player performance such as games played and points scored. This analysis helps us understand the question of ***can we predict salaries based on player performance?"** 


# Data Question
The specific data question we looked at had two parts:
1. How are player perforamnce metrics related to salary?
2. For players in the WNBA and NBA with comparable performance, what is the discrepancy in salary?

# Results 

# Exploratory Regressions
Figure 1. Salary vs Games Played for NBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/mens_salaryvgames.png)

Figure 2. Salary vs Games Played for WNBA
![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/womens_salaryvgames.png)

Multivariate Regression Results:
NBA salary = -56900*games played + 9609*rebounds + 10220*points + 30600*assists
R^2 = 0.686

WNBA salary = 3533*games played + 37 *rebounds + 14.7*points + 545.8 *assists
R^2 = 0.774

From these results, it is immediately clear that the men's salaries are significantly higher than the women's salaries just by looking at the units of the axes, regardless of games played. The regression visualized in Figure 1 has an R^2 of 0.46 whereas the R^2 of the regression in Figure 2 is 0.75. Thus, the WNBA has a stronger linear relationship between salary and games played. We can see that there are fewer outliers of women having high salaries with few games played comparatively as there are several men's players who played few games but have similar salaries to those who played 60 games. This may be due to injuries that prevented players from getting court-time after their salaries and contracts were negotiated. It is also important to note that there are far fewer games played in the WNBA than in the NBA, which may account for some difference in salary. Based on the multivariate regression results, all performance metrics positively influence salary as expected, except for the number of games played for men's teams. This is likely a discrepancy and could be caused by the unexpected injuries as aforementioned. Games played has the largest impact on salary for women's teams. Overall, the data shows a stronger linear fit for predicting slaary based on performance metrics for WNBA compared to the NBA, which may suggest that external factors such as sponsorships and player "hype" are contributors to salary for men's basketball.

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

WNBA...
1. Arike Ogunbowale
1. Courtney Vandersloot
1. Breanna Stewart
1. DeWanna Bonner
1. A'ja Wilson
1. Diana Taurasi
1. Alyssa Thomas
1. Sabrina Ionescu
1. Napheesa Collier
1. Candace Parker
1. Brittney Griner
1. Betnijah Laney
1. Skylar Diggins-Smith
1. Myisha Hines-Allen
1. Kelsey Mitchell

NBA...
1. Luka Doncic
1. James Harden
1. Nikola Jokic
1. Giannis Antetokounmpo
1. Russell Westbrook
1. Stephen Curry
1. Damian Lillard
1. Trae Young
1. LeBron James
1. Joel Embiid
1. Bradley Beal
1. Kevin Durant
1. Julius Randle
1. Kyrie Irving
1. Zach LaVine

These lists both pass the eye test and would be considered to be quite reasonable in the judgement of most fans.

Now that we have proof-of-concept for the PCA model, it's time to use the model to explore the discrepancy of salaries of players of comparable value in the PCA model based on league. It was important to build the PCA model separately for each league because actual salary figures vary severely by league and the model would fail to accurately model salary in either league if both were done together (instead getting stuck in the middle). However, as a means of evaluating both WNBA and NBA players all together, we averaged each weight from the two individual PCA models together to form an overall, non-league-specific set of weights. These weights are as follows: 

Minutes per Game: 0.5028422613056367
Points per Game: 0.271784794225057
Assists per Game: 0.1354994985248121
Rebounds per Game: 0.0898344594449426

We then used these weights to determine an overall projected player value score for every WNBA and NBA player. This projected player value score was then compared to players' actual salaries. WNBA players are plotted in blue and NBA players are plotted in red.

![alt text](https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/Actual%20Player%20Salary%20vs.%20Projected%20Player%20Value%20Differentiated%20by%20League.PNG)
*Note*: For the HTML version of this visual, which labels each dot with coordinate info and the player that it corresponds to, download and view this (file)[https://github.com/aakap/nba_wnba_salarycomparisons/blob/main/actual-player-salary-versus-projected-player-value-differentiated-by-league].
This graph makes it very clear that NBA players and WNBA players who have extremely comparable player performance and projected player value scores make vastly different salaries due to the pay gap. For any given x-axis value (projected player value score), the red dots are significantly below the blue dots when it comes to the y-axis (actual salary). There is no merit to any conception that there is a player-performance driven reason for WNBA players to be underpaid relatively to NBA players.
