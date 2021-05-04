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
To build a preliminary model for basketball player salaries, we performed a principal component analysis (PCA) using salary as the target variable and minutes played per game, points scored per minute, assists per minute, and rebounds per minute as input variables. This PCA was performed separately on a WNBA data set and a NBA data set. The weights were mildly different but comparable and were as follows:

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

We see that minutes played per game is slightly more influential in our projection for salary in the WNBA than it is for the NBA whereas assists per minute and rebounds per minute are slighly more influential in our projection for salary in the NBA than for the WNBA. However, it is noteworthy that the weights are quite similar for both leagues, suggesting that players with similar performance metrics in each league should have comparable salaries using this model.
