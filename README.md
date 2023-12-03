# IPL_Cricket_Best_11_player_Analysis
Data Analysis Project for IPL Cricket to select Best 11 player.

**Problem Statement** :

Project Sportan : We Don't know the strenghts and weaknesses of our oppenents but give me the best 11 from this planet based on last T20 world cup data.
1. The team should be able to score at least 180 runs on an average.
2. They should be to defend 150 runs on an average

**Data Source** : 
considered the data from ESPN website through web scrapping. Below are the data sets used for Analysis-
1. t20_wc_batting_summary.json
2. t20_wc_bowling_summary.json
3. t20_wc_match_results.json
4. t20_wc_player_info.json


**Requirements Gathering** :
Considered below metrics to perform Analysis-

**Openers** -
| Parameters      | Description                        | Criteria|
| :--------------:|:--------------------------------:  | :------:|
| Batting average | Average runs scored in an innings  |   >30   |
| Strike Rate     | No of runs scored per 100 balls    |   >140  |
| Innings Batted  | Total Innings batted               |   >3    |
| Boundary %      | % of runs scored in boundaries     |   >50   |
| Batting Position| Order in which the batter played   |   <4    |

**Anchors/ Middle Order** -
| Parameters      | Description                                     | Criteria|
| :--------------:|:-----------------------------------------------:| :------:|
| Batting average | Average runs scored in an innings               |   >40   |
| Strike Rate     | No of runs scored per 100 balls                 |   >125  |
| Innings Batted  | Total Innings batted                            |   >3    |
| Avg. Balls Faced| Average balls faced by the batter in an innings |   >20   |
| Batting Position| Order in which the batter played                |   >2    |

**Finisher/ Loer Order Anchor** -
| Parameters      | Description                                     | Criteria|
| :--------------:|:-----------------------------------------------:| :------:|
| Batting average | Average runs scored in an innings               |   >25   |
| Strike Rate     | No of runs scored per 100 balls                 |   >130  |
| Innings Batted  | Total Innings batted                            |   >3    |
| Avg. Balls Faced| Average balls faced by the batter in an innings |   >12   |
| Batting Position| Order in which the batter played                |   >4    |
| Innings Bowled  | Total innings Bowled by the bowler              |   >1    |

**ALL-Rounders/ Lower Order** -
| Parameters         | Description                                     | Criteria|
| :----------------: |:-----------------------------------------------:| :------:|
| Batting average    | Average runs scored in an innings               |   >15   |
| Strike Rate        | No of runs scored per 100 balls                 |   >140  |
| Innings Batted     | Total Innings batted                            |   >2    |
| Batting Position   | Order in which the batter played                |   >4    |
| Innings Bowled     | Total innings Bowled by the bowler              |   >2    |
| Bowling Economy    | Average runs allowed per over                   |   <7    |
| Bowling Strike Rate| Average no. of balls required to take a wicket  |   <20   |

**Specialist Fast Bowler** -
| Parameters         | Description                                     | Criteria|
| :----------------: |:-----------------------------------------------:| :------:|
| Innings Bowled     | Total innings Bowled by the bowler              |   >2    |
| Bowling Economy    | Average runs allowed per over                   |   <7    |
| Bowling Strike Rate| Average no. of balls required to take a wicket  |   <20   |
| Bowling Style      | Bowling style of the player                     |   <20   |
| Bowling average    | No. of runs allowed per wicket                  |   >15   |
| Dot Ball %         | % of dot balls bowled                           |   >140  |

**Data Analysis Steps** :
1. Used Python for data cleaning and Transformation of the json data files to csv files which makes futher Analysis easier.
2. Used MS Excel for further glance on data cleaning and Transforming.
3. Used PowerBI for further transformation and Visualization of insights driven through the Analysis.

**DataCleaning and basic Transformations Using Python (Jupyter Notebook)** : 
1. Read the Json files into pandas dataframe and performed Data Cleaning and checked the data types.
2. Handled the Null and duplicate data.
3. Renaming of column names and cleaned up the weired charaters.
4. Added new columns which helps in joining the tables and maintain the relationship between tables.
5. Data Transformations are performed to make data more efficient to draw insights.
6. Finally write the cleaned and transformed data to csv files.
    dim_match_summary.csv
    dim_players_no_images.csv
    fact_bating_summary.csv
    fact_bowling_summary.csv

**DataCleaning and Transformations Using MS Excel** :
1. Open the files in excel and re-verified the data, make sured the data was cleaned and in required format.
2. Added the new column image manually which can help in visualization.
   	--> dim_players.csv

**Data Visualization using PowerBI** :
1. Loaded the data into powerBI and Transformed the data through power Query.
2. Verified the data was cleaned and was in required format.
3. Verified the data model and relationship between the tables.
4. Created the Statistical measures which help in dashboard calculations. Below are the measured & calculated columns used-

**Measures**:		


| Measures               | Description /Purpose                                  | DAX FORMULA                                                                   | Table                |
| :--------------------: |:-----------------------------------------------------:| :----------------------------------------------------------------------------:|:--------------------:|
| Total Runs             | Total number of runs scored by the batsman            | Total Runs = SUM(fact_batting_summary[runs])                                  | fact_batting_summary |
| Total Innings Batted   | Total number of innings a batsman got a chance to bat | Total Innings Batted = COUNT(fact_batting_summary[match_id])                  | fact_batting_summary |
| Total Innings Dismissed| To find the number of innings batsman got out         | Total Innings Dismissed= SUM(fact_batting_summary[out])                       | fact_batting_summary |
| Batting Average        | Average runs scored in an innings                     | Batting Avg = DIVIDE([Total Runs],[Total Innings Dismissed],0)                | fact_batting_summary |
| Total balls Faced      | Total number of balls faced by the batsman            | total balls faced = SUM(fact_batting_summary[balls])                          | fact_batting_summary |
| Strike Rate            | No of runs scored per 100 balls                       | Strike rate = DIVIDE([Total Runs],[total balls faced],0)*100                  | fact_batting_summary |
| Batting Position       | Batting position of a player                          | Batting Position = ROUNDUP(AVERAGE(fact_batting_summary[battingPos]),0)       | fact_batting_summary |
| Boundary %             | Percentage of boundaries scored by the Batsman        | Boundary % =  DIVIDE(SUM(fact_batting_summary[Boundary runs]),[Total Runs],0) | fact_batting_summary |
| Avg. balls Faced       | Average balls faced by the batter in an innings       | Avg. balls Faced=AVERAGE(fact_batting_summary[balls])                         | fact_batting_summary |
| Wickets                | Total number of wickets taken by a bowler             | wickets = SUM(fact_bowling_summary[wickets])                                  | fact_bowling_summary |
| balls Bowled           | Total number of balls bowled by the bowler            | balls Bowled = SUM(fact_bowling_summary[balls])                               | fact_bowling_summary |
| Runs Conceded          | Total runs conceded by the bowler                     | Runs Conceded = SUM(fact_bowling_summary[runs])                               | fact_bowling_summary |
| Bowling Economy        | Average number of runs conceded in an over            | Economy = DIVIDE( [Runs Conceded], ([balls Bowled]/6),0)                      | fact_bowling_summary |
| Bowling Strike Rate    | Number of balls bowled per wicket                     | Bowling Strike Rate = DIVIDE([balls Bowled], [wickets],0)                     | fact_bowling_summary |
| Bowling Average        | No. of runs allowed per wicket                        | Bowling Average = DIVIDE([Runs Conceded],[wickets],0)                         | fact_bowling_summary |
| Total Innings Bowled   | Total number of innings bowled by a bowler            | Total Innings Bowled = DISTINCTCOUNT(fact_bowling_summary[match_id])          | fact_bowling_summary |
| Dot Ball %             | Percentage of dot balls bowled by a bowler            | Dot ball % = DIVIDE(SUM(fact_bowling_summary[zeros]), SUM(fact_bowling_summary[balls]),0) | fact_bowling_summary |
| Player Selection       | To understand if a player is selected or not          | Player Selection = if(ISFILTERED(dim_players[name]),"1","0")                  | dim_players |
| Display Text           | To display a text of no player is selected            | Display Text = if([Player Selection] = "1", " " ,"Select Player(s) by clicking the player’s name to see their individual or combined strength.") |  |
| Color Callout Value    | To display a value only when a player is selected     | Color Callout Value = if([Player Selection]="0", "#D0CF1D","#1D1D2E")         |  |


**Calculated Columns** :

| Calculated Column Name | Description /Purpose                                              | DAX FORMULA                                                             | Table                |
| :--------------------: |:---------------------------------------------------------------:  | :----------------------------------------------------------------------:|:--------------------:|
| Boundary runs          | To find the total number of runs scored by hitting fours and sixes| boundary runs = fact_batting_summary[fours]*4 + fact_batting_summary[sixes]*6 | fact_batting_summary |
| Boundary runs bowling  | To find the total number of runs conceded by bowlers in boundaries| Boundary runs bowling = fact_bowling_summary[fours]*4 +fact_bowling_summary[Sixes]*6 | fact_bowling_summary |
| Custom Batting Order   | To assign the batting order to potential final 11                 | Custom Batting Order = SWITCH( TRUE(), dim_players[name] = "Jos Buttler",1, dim_players[name] = "Rilee Rossouw",2, dim_players[name] = "Alex Hales",2, dim_players[name]  = "Virat Kohli",3, dim_players[name] = "Suryakumar Yadav" ,4, dim_players[name] = "Glenn Phillips" ,5, dim_players[name] = "Marcus Stoinis" ,6, dim_players[name] = "Glenn Maxwell" ,6, dim_players[name] = "Hardik Pandya" ,6, dim_players[name] = "Sikandar Raza" ,7, dim_players[name] = "Rashid Khan" ,8, dim_players[name] = "Shadab Khan" ,8, dim_players[name] = "Sam Curran" ,9, dim_players[name] = "Shaheen Shah Afridi" ,10, dim_players[name] = "Anrich Nortje" ,11) | dim_players |




				



