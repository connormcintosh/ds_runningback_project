# NFL Salary Predictions
## Salary Cap Percentage of Running Backs

by Aaron Freid, Brian Li, Connor McIntosh, Alex Rudolph, Nate Soeth

# Abstract
Using supervised learning methods, our goal is to create a model that will be able to accurately predict what percentage of the NFL salary cap a single running back will take up for a season. In this project, we will analyze regular season game statistics, offensive line metrics, and career data to create useful features as well as calculate actual salary cap percentages to train our model.

# Motivation
The running back position has seen a paradigm shift in the last decade and a half. Running back used to be the premier position in football, but as the passing game has opened up and more teams start to adopt a 'running back by committee' model, there has been more fluctuation in the running back market,. as so it is our goal to try to predict a slary cap percentage based on real world in-game data.

# Data Cleaning
The process of cleaning our dataset involved merging data from different sources (season statistics data from profootballreference.com financial and salary cap data from spotrac.com) We then had to remove ambiguous data such as player who were not listed at the running back position or those who were listed at multiple positions during their career.

Listed below a few rows of the cleaned dataset:

|    |   year | playername         | team   |   age |   draft_yr |   draft_pos |   attempts |   yards_run |   tds_run |   longgain_run |   yardsperatt |   yardspergame_run |   Percenthit (%) |   g |   gs |   tgt |   rec | catchpercent   |   yards_rec |   yardsperrec |   tds_rec |   firstdowns |   longgain_rec |   yardspertarget |   recpergame |   yardspergame_rec |   fumbles |   team_adjusted_line_yards |   team_running_back_yards |   team_stuffed_rate |
|---:|-------:|:-------------------|:-------|------:|-----------:|------------:|-----------:|------------:|----------:|---------------:|--------------:|-------------------:|-----------------:|----:|-----:|------:|------:|:---------------|------------:|--------------:|----------:|-------------:|---------------:|-----------------:|-------------:|-------------------:|----------:|---------------------------:|--------------------------:|--------------------:|
|  0 |   2020 | Aaron Jones        | GNB    |    26 |       2017 |         182 |         75 |         389 |         5 |             75 |           5.2 |               77.8 |         1.10091  |   9 |    9 |    45 |    33 | 73.30%         |         261 |           7.9 |         2 |           12 |             30 |              5.8 |          3.7 |               29   |         2 |                          5 |                         3 |                   1 |
|  4 |   2020 | Adrian Peterson    | DET    |    35 |       2007 |           7 |         80 |         314 |         2 |             27 |           3.9 |               52.3 |         0.529768 |  11 |    8 |    16 |    11 | 68.80%         |          78 |           7.1 |         0 |            3 |             18 |              4.9 |          1   |                7.1 |         0 |                         19 |                        22 |                  18 |
| 27 |   2020 | Alexander Mattison | MIN    |    22 |       2019 |         102 |         54 |         245 |         1 |             25 |           4.5 |               40.8 |         0.444271 |  11 |    1 |    11 |     9 | 81.80%         |          61 |           6.8 |         0 |            3 |             14 |              5.5 |          0.8 |                5.5 |         0 |                          1 |                         5 |                   6 |
| 34 |   2020 | Alvin Kamara       | NOR    |    25 |       2017 |          67 |         75 |         364 |         4 |             49 |           4.9 |               60.7 |         2.05661  |  11 |    6 |    83 |    68 | 81.90%         |         646 |           9.5 |         4 |           29 |             52 |              7.8 |          6.2 |               58.7 |         1 |                          4 |                         8 |                   2 |
| 38 |   2020 | Ameer Abdullah     | MIN    |    27 |       2015 |          54 |          2 |           7 |         0 |              4 |           3.5 |                1.2 |         0.44778  |  11 |    0 |     2 |     2 | 100.00%        |          23 |          11.5 |         1 |            1 |             22 |             11.5 |          0.2 |                2.1 |         0 |                          1 |                         5 |                   6 |

# Modelling
