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

---

## Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

| Quarter     |   Count |
|:------------|--------:|
| Fall 2020   |       3 |
| Winter 2021 |       2 |
| Spring 2021 |       6 |
| Summer 2021 |       4 |
| Fall 2021   |      55 |

---

## Hypothesis Testing


---