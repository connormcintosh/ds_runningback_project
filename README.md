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
|  1 |   2019 | Aaron Jones        | GNB    |    25 |       2017 |         182 |        236 |        1084 |        16 |             56 |           4.6 |               67.8 |         0.369547 |  16 |   16 |    68 |    49 | 72.10%         |         474 |           9.7 |         3 |           18 |             67 |              7   |          3.1 |               29.6 |         3 |                          5 |                        13 |                   6 |
|  5 |   2019 | Adrian Peterson    | WAS    |    34 |       2007 |           7 |        211 |         898 |         5 |             32 |           4.3 |               59.9 |         0.945802 |  15 |   15 |    23 |    17 | 73.90%         |         142 |           8.4 |         0 |            7 |             22 |              6.2 |          1.1 |                9.5 |         3 |                         18 |                        15 |                  17 |
| 28 |   2019 | Alexander Mattison | MIN    |    21 |       2019 |         102 |        100 |         462 |         1 |             35 |           4.6 |               35.5 |         0.372234 |  13 |    0 |    12 |    10 | 83.30%         |          82 |           8.2 |         0 |            3 |             17 |              6.8 |          0.8 |                6.3 |         1 |                          7 |                         7 |                   5 |
| 35 |   2019 | Alvin Kamara       | NOR    |    24 |       2017 |          67 |        171 |         797 |         5 |             40 |           4.7 |               56.9 |         0.558285 |  14 |    9 |    97 |    81 | 83.50%         |         533 |           6.6 |         1 |           28 |             41 |              5.5 |          5.8 |               38.1 |         4 |                          1 |                        11 |                   4 |
| 39 |   2019 | Ameer Abdullah     | MIN    |    26 |       2015 |          54 |         23 |         115 |         0 |             15 |           5   |                7.2 |         0.390542 |  16 |    0 |    21 |    15 | 71.40%         |          88 |           5.9 |         1 |            5 |             16 |              4.2 |          0.9 |                5.5 |         1 |                          7 |                         7 |                   5 |


# Modeling
Our model was a Feedforward Neural Network built using the keras library that took 18 features gathered from the cleaned dataset and contained three dense hidden layers of 40 neurons each of which using the ReLU activation function. The model was trained using the mean squared error validation function and the SGD optimizer. Below is the model summary:
![image](https://user-images.githubusercontent.com/46730903/119598993-ee8f9d00-bd98-11eb-8653-e4042bc45be8.png)

Using the tools provided by
[NN-SVG](http://alexlenail.me/NN-SVG/index.html)
we were able to create a visualizartion of our neural network complete wilth all three hidden layers and the dimensions of each input, hidden and output layer:
<img width="960" alt="DNNViz" src="https://user-images.githubusercontent.com/46730903/119599826-9bb6e500-bd9a-11eb-8c38-52ca103e80cd.PNG">

The initiial dataset was split 25-75 in terms of testing and training. After the model was trained, it achieved an explained variance score of 0.51 on the testing set as well as other metrics shown below. We have also graphed the predicted values compared to the actual values for the entire dataset used:

![image](https://user-images.githubusercontent.com/46730903/119598927-c738d000-bd98-11eb-90a0-9735b706afc1.png)


# 2021 Free Agent Predictions
We decided to use our model to predict the salaey cap percentage values for some of the members of the most recent class of free agent running back signings. The results are listed below as well as the difference between our prediction and the actual salary cap percentage for the 2021 season that each player signed for:

|    | name            |   2021 Actual |   Predicted Value |   difference |
|---:|:----------------|--------------:|------------------:|-------------:|
|  0 | Aaron Jones     |      2.369    |           1.84578 |    -0.523225 |
|  1 | Kenyan Drake    |      1.592    |           4.84822 |    +3.25622  |
|  2 | Gus Edwards     |      1.796    |           1.17057 |    -0.625428 |
|  3 | James Conner    |      0.9288   |           3.0995  |    +2.1707   |
|  4 | Chris Carson    |      1.327    |           1.54475 |    +0.217746 |
|  5 | Jamaal Williams |      0.862527 |           1.24564 |    +0.383116 |
|  6 | Phillip Lindsay |      1.63     |           1.02531 |    -0.604692 |

While we are very pleased to see that more than a few of these predictions were withing half of a percentage, it is interesting to see the reasons for some of our over-predictions and under-predictions. For example, team_adjusted_line_yards and team_stuffed_rate are two offensive line metrics that seek to isolate the value of the offensive line independent of the running back's performance. Aaron Jones' offensive line was one of the best in 2020, while the offensive lines that blocked for James Conner and Kenyan Drake were two of the worst in the league. However, these three players had similar production in a similar amount of games. It is likely that our model takes this into account, surmising that backs like Conner and Drake have increased value through their overcoming of poor offensive line play.

|    | playername      |   team_adjusted_line_yards |   team_stuffed_rate |   yards_run |   tds_run |   g |
|---:|:----------------|---------------------------:|--------------------:|------------:|----------:|----:|
|  0 | Aaron Jones     |                          5 |                   1 |        1104 |         9 |  14 |
|  1 | Kenyan Drake    |                         30 |                  25 |         955 |        10 |  15 |
|  3 | James Conner    |                         32 |                  28 |         721 |         6 |  13 |

# Summary
Through our analysis of the trends found in the data itself and the predictions of our model, we were able to gain valuable insight into the process that goes into the valuation of professional athletes and the nuances of constructing a competitive roster under as hard salary cap. Through this, our team gained new experience in and demonstrated proficiency in crucial data science concepts like data cleaning and exploratory data analysis as well as machine learning tools such as the scikit-learn and Keras libraries. In making predictions on real-world data, we generated novel information and accurate predictions in our results leading to new ideas  and challenges as to how to improve our methodologies and application of the skills we have used thus far.
