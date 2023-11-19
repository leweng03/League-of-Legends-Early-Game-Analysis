# League of Legends Early Game Analysis

by Lewis Weng

***Note***: This is for a DSC80 project.

---

## Introduction

This analysis is based on the League of Legends Competitive Matches dataset, which can be found on the website "Oracle's Elixir". In this dataset, there are 149400 rows and 123 columns. The data includes the champions picked and banned, the teams that played, their regions, objectives taken, game time, and differences in gold and experience at the 15 minute mark. Every row of the column equates to one player. Every 10 columns there are 2 columns that contains information about the 2 teams. Every match is 12 rows.

This project will be focusing on these columns: league, firstdragon, firstherald, firsttower, golddiffat15, and result. New columns that are based on the existing columns will be created for the purposes of this project. The 'league' refers to the league in which the game was played in. 'firstdragon' refers to whether a team has claimed first dragon (0 for No, 1 for Yes). 'firstherald' refers to whether a team has taken the first herald (0 for No, 1 for Yes). 'firsttower' refers to whether a team has taken the first tower (0 for No, 1 for Yes). 'golddiffat15' refers to the gold difference betweeen the player and opposing player, or the team and the opposing team. 'result' contains data on whether a team or player won the game (0 for Loss, 1 for Win). 

The goal of this project is to determine whether having a gold lead in the early game leads to winning games. This dataset contains game information from professional League of Legends esports games from 2022. Other League of Legends players may be interested in this information because it can help them identify what can help them win more games. People that bet on League of Legends esports games can also use this information to evaluate the strength of teams or determine to likelihood of their bets succeeding while the game is in progress. 

---

## Cleaning and EDA

For my analysis, I convert the columns that consist of 0's and 1's to boolean values of True and False. I also removed the rows in the dataset that were empty. These rows were missing information that were needed for the analysis.

| league   | firstdragon   | firstherald   | firsttower   |   golddiffat15 | result   | goldlead@15   |
|:---------|:--------------|:--------------|:-------------|---------------:|:---------|:--------------|
| LCK      | False         | True          | True         |           4757 | False    | True          |
| LCK      | True          | False         | False        |          -4757 | True     | False         |
| LCK      | False         | True          | True         |          -1045 | False    | False         |
| LCK      | True          | False         | False        |           1045 | True     | True          |
| LCK      | True          | True          | False        |           1309 | True     | True          |

<iframe src="assets/goldfig15.html" width=800 height=600 frameBorder=0></iframe>

From this visualization we can see that the chances of winning are highly elevated when the team has a gold lead at 15 minutes. Teams that have a gold lead at 15 minutes have won 72% of the time while teams that didn't have a gold lead at 15 minutes won 28% of the time.


<iframe src="assets/gold15_tower_fig.html" width=800 height=600 frameBorder=0></iframe>

This visualization shows the overlapping distribution for the gold difference at 15 minutse when first tower was taken vs first tower was not taken. The orange distribution is when first tower was not taken. The blue distribution is when first tower was taken. The red in the center is the overlapping part of the distributions. This means that teams that have taken first tower tend to have a bigger gold lead, with some overlap.


|   result |   firstherald |   firstdragon |   firsttower |
|---------:|--------------:|--------------:|-------------:|
| 0.271654 |      0.359252 |      0.462598 |     0.195866 |
| 0.728346 |      0.640748 |      0.537402 |     0.804134 |

---

## Assessment of Missingness

|      False |     True |
|-----------:|---------:|
|   0.459646 | 0.238363 |
|   0.301181 | 0.156186 |
|   0.239173 | 0.12403  |
| nan        | 0.481421 |

|      0.0 |      1.0 |
|---------:|---------:|
| 0.228014 | 0.250624 |
| 0.297721 | 0.234082 |
| 0.243122 | 0.235258 |
| 0.231143 | 0.280035 |


<iframe src="assets/side_vs_towermissing.html" width=800 height=600 frameBorder=0></iframe>

In the dataset, 50% of the towermissing was on red side and the other 50% of the tower missing was on blue side (there are two sides, 1 for each team). When I shuffle the 'towermissing' column and run permutation tests, I get this visualization and can clearly see that 0.5 is part of the empirical distribution.

---

## Hypothesis Testing

<iframe src="assets/hypothesis_fig.html" width=800 height=600 frameBorder=0></iframe>

This visualization is created by shuffling the 'result' column and getting the distribution of wins with a gold lead at 15 minutes. The red line is the observed statistic, which is not part of the empirical distribution. The p-value is 0, so we can reject the null hypothesis.

---