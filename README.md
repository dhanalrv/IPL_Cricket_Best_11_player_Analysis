# IPL_Cricket_Best_11_player_Analysis
Data Analysis Project for IPL Cricket to select Best 11 player.

**Problem Statement** :

Project Sportan : We Don't know the strenghts and weaknesses of our oppenents but give me the best 11 from this planet based on last T20 world cup data.
1. The team should be able to score at least 180 runs on an average.
2. They should be to defend 150 runs on an average

**Data Source** : 
considered the data from ESPN website through web scrapping. Below are the data set considered for Analysis-
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



