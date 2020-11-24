# NFL Regular Season Skilled Position Player Performance as a Predictor of Playoff Appearance Overtime

- [x] we suggest you use markdown tables if you can they are easy to create for example from pandas. There is a special function for that
- [x] are the p values all 0? if so you need to do 2 digits behind comma. change format in table
- [x] Attribute names in the text differe from tables and figures e.g. "Succesful Reception" I suggest you create a table with abbreviation mapping, but in reality you should changethem in your tables and figues. The way to do this is to rename the columns and describe in your Dataset what you did

[![Check Report](https://github.com/cybertraining-dsc/fa20-523-308/workflows/Check%20Report/badge.svg)](https://github.com/cybertraining-dsc/fa20-523-308/actions)
[![Status](https://github.com/cybertraining-dsc/fa20-523-308/workflows/Status/badge.svg)](https://github.com/cybertraining-dsc/fa20-523-308/actions)
Status: in progress


Travis Whitaker, [fa20-523-308](https://github.com/cybertraining-dsc/fa20-523-308), [Edit](https://github.com/cybertraining-dsc/fa20-523-308/blob/main/project/project.md)

{{% pageinfo %}}

## Abstract

Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** ANOVA, Comparative Analysis, Exploratory Analysis, Football, Sports, Metrics

## 1. Introduction

In the modern NFL the biggest negotiating tools for players in signing a new contract is their on-field performance. Many players choose to "hold-out" of pre-season practice or regular season games as a negotiating tool in their attempt to sign a more lucrative contract. In this situation players feel as though their exceptional performance on the field is not reflected in the monetary compensation structure of their contract. This is most often reflected in skill position players such as wide receivers or running backs whose play on the field is most often celebrated (e.g., touchdowns) and discussed by fans of the game. While these positions are no doubt important to a team’s success, the question remains how important is one players contribution to a team’s overall success? The current project will attempt to evaluate the importance of skill position players' (i.e., Quarterback (QB), Wide Receiver (WR), Running Back (RB), and Tight End (TE)) performance during the regular season and use in-game performance metrics as a predictive factor for their team making the playoffs. This is an attempt to answer the question can qualifying for the post-season be predicted by skill position metrics measured during the regular season? If so, then which metrics are most crucial to predicting post-season birth?

A secondary analysis in this project will look at a comparison between 2009-2011 vs. 2016-2018 regular season metrics and build separate models for each three year span to investigate whether a shift in performance metric importance has occurred over the past decade. NFL insiders and journalists have noted the shift in play-calling over the past decade in the NFL as well as the change at the quarterback position to more "dual-threat" (running and throwing) quarterbacks that have transitioned the game to a more "aggressive" play-style [^1]. Yet punditry and reporting have not always been supported by performance metrics and this specific claim of a transition over the past decade needs some exploring. Therefore, we will be investigating whether there has been a shift in the performance metrics that are important in predicting team success. Again, team success will be measured by making the post-season. 

## 2. Background Research and Previous Work

There are many playoff predictor models that focus on team performance or team wins vs losses as a predictor of making the playoffs [^2]. However, few take into consideration individual player performance as an indicator of their team making the post-season playoffs in the NFL. The most famous model that takes into consideration player performance is ELO rating [^3]. The first ELO rating was a straightforward model that took head-to-head results and player-vs-team model in order to predict win probability in an NFL game. However, in 2019 Silver and his team at FiveThirtyEight updated their ELO model to give a value rating to the quarterback position for each team. This quarterback value included metrics such as pass attempts, completions, passing yards, passing touchdowns, interceptions, sacks, rush attempts, rushing yards, and rushing touchdowns. Taking these metrics along with the defensive quality metrics, which is an adjustment of quarterback value based on the opposing defense ranking, gives you an overall value for your quarterback. Thus, this widely accepted model takes head-to-head team comparisons on a week-to-week basis and includes the quarterback value in predicting the winners of these head-to-head matchups. However, no model has taken just player performance and tried to predict team success for an entire regular season based on each of their individual players. These previous models primarily look at offensive vs. defensive units and try to predict win/loss records based off each of these units.

The goal of the present research is not to compare our model vs previous models, as these standing models are not meant for playoff prediction, rather these previous models are used for a game-by-game matchup comparison. The present research investigates whether looking at position players at each of the skilled positions, maps onto predicting the post-season qualifying teams. Further, how does this predictive model change over time? Looking at 2009-2011 NFL skill player performance vs 2016-2018 skill player performance we will investigate if there are differences in metrics that predict post-season appearance. This will show us whether there are shifts in skill position play that impact predicting post-season playoff appearance. Specifically, by comparing the two models which use two different periods of time (i.e., 2009-2011 vs 2016-2018) we will be able to better investigate specific metrics at each position that are important for predicting success. For example, if the wide receiver position is important, what is most important about that position, yards-after-catch or number of receptions? Further, how might the importance of those metrics shift over time? We hope to explore and understand better the impact of skill players and the metrics that they are measured on in terms of making the post-season.

## 3. Choice of Data-sets

The dataset we will be using is in a github folder that holds nflscrapR-data that originates from NFL.com [^4]. The folder includes play-by-play data, including performance measures, for all regular season games from 2009 to 2019. This file will be paired with week-by-week regular season roster data for each team in the NFL. This will allow us to track skilled position player performance during the regular season and then compare this regular season file with the files that contain playoff teams for each year from 2009-2019. Supplemental data may be pulled from Pro-Football-Reference.com or other sources depending on what preliminary data analysis presents [^5].

## 4. Methodology

The first step we took to understand the data was to use various slices of the data put into scatterplots and bar charts to find trends, as well as various time series charts. This was an exploratory step in understanding the data. 

Then each metric from player performance during the regular season was included in the analysis or algorithm that were built to predict post-season appearance. Post-season appearance is a designation for a team qualifying for the post-season or playoffs. We think it may be important to engineer some new features to potentially provide insights.  For instance, it is possible to determine whether a play was during the final two minutes of a half and if a play was in the red zone. During these critical points of a game a win or lose is often determined. Our thought is by weighing these moments and performance metrics with more importance the model will better predict a team’s likelihood of making the playoffs. Another secondary metric that may strengthen the predictive ability of the model would be to use Football Outsider’s Success Rate, which is a determination of a play’s success rate for the offense that is on the field [^5]. This can also provide me with the down and distance to go for the offense and players that are on the field. We will also use college position designations as way to normalize the positions performance across teams. Many NFL teams utilize different player sets. Thus, it is important to use a standard, which college football uses across all teams. Since we are only interested in skill position players this will include Wide Receiver (WR), Running Back (RB), Full Back (FB), Quarterback (QB), and Tight End (TE). These designations will allow the algorithm to compare, if needed, the skill position performance across teams and by designation of players on that team for each metric utilized. 

After breaking down the data into key categorical variables to see if there was an impact for these performance variables in making the playoffs for the NFL teams. These individual position statistics were analyzed as a group and then separated into "Post Season" meaning the player's team qualified for the playoffs, or "No Post" meaning the player's team did not qualify for the playoffs. By doing this we were able to verify that a reasonable number of players fell into the "Post Season" group, as only 12 out of 32 teams qualify for the post-season. Further we were able to use these designations in the next step of modeling, where the data was analyzed in an ANOVA to see how important each metric was in predicting post-season appearance for each player.

Metric measurement needs to be consistent across years. A comparison of year-to-year metrics was completed comparing each years measurements from 2009-2011 and 2016-2018 in order to make sure that the measurement techniques were stable and do not vary across time. If there were changes in the way metrics are measured than either that year will need to be dropped from the model or adjustments will need to be made to the metric to balance it with the other years included in the model. Luckily, there were no variation in metric measurement across years, so all measurements initially included in the model were kept. 

Finally, once all metrics had been balanced and the team performance metrics have been aggregated. The ANOVA model was built to analyze metric measurement as a predictor of a player making post-season play. This ANOVA model was created twice, once for the 2009-2011 players and then again for the 2016-2018 players. Once this analysis was run, we were able to see the strength of the model in predicting playoff appearance by player, based on metric measurement.

## 5. Results

### Inference

An individual player-performance model for NFL skill position players (i.e., quarterback, wide receiver, tight end, and running back) will perform better than chance level (50%) of identifying playoff teams from the NFL during the season's of 2009-2011 and 2016-2018. Further, an exploratory analysis of time periods (2009-2011 vs 2016-2018) will expose differences in the key metrics that are used to predict playoff appearance over time. This will give us a better understanding of the shifts in performance in the NFL at each skill position.

### Preliminary Results

The descriptive statistics for the player performance revealed no issues with normality or different metric standards across seasons for player performance measurements. Figure 1 represents a count check for players qualifying for the post-season in the seasons of 2009-2011. Based on the NFL post-season structure 12 out of 32 teams qualify for the post-season, or 37.5%. Figure 1 shows that roughly 1/3 of players qualify for the post season at each position. However, it is important to note that each team structure and roster is different. For example, one team may carry 7 receivers, 2 running backs, 2, quarter backs, 2 tight ends, and 0 full backs, where another team may carry 4 receivers, 4 running backs, 3 quarter backs, 4 tight ends, and 1 full back. This is an important distinction to make because the "Post Season" players shown in figure 1 are not at an equal percentage across position. 

#### 2009-2011 Skill Position Player Performance as Playoff Predictor


![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2009_2011.png)

**Figure 1:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2009-2011)

We also wanted to investigate whether play-count at each position was balanced across post-season players and players who did not qualify for the post-season. Figure 2 shows that players on teams who did qualify for the post-season were involved in more plays at their position than players at their position who did not qualify for the playoffs. Thinking about this finding as a result of the regular season, players in skilled positions on post-season qualifying teams play on offenses that won more games than teams who did not qualify for the playoffs. While we did not look at time of possesion for players by position, it seems fairly reasonable by logic and the results in figure 2 that play count is higher because these teams are more succesful and the players on post-season qualifying teams are on the field more than teams with more losses who did not qualify for the post-season. 

![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_count_position_2009.png)

**Figure 2:** Count of Play-type by Post-Season Qualification category (2009-2011)

Using the player performance metrics for the regular season, an ANOVA was run to see if these metrics placed together would be a succesful predictor of post-season qualification. Figure 4 shows the top 10 metrics that had the highest f-values for predicting post-season qualification, all of which were all significant (p<.05) in the model. Reviewing the model, the most significant factors for predicting post-season qualification for teams in order were; 1. Succesful Reception (wide receiver or tight end), 2. Total Receiving Yards (Wide Receiver or Tight End), 3. Yards After Catch (wide receiver or tight end), 4. Total Receiving Touchdowns (Wide Receiver or Tight End), 5. Total Touchdowns (All positions), 6. Receiver Plays (Wide Receiver), 7. Redzone Plays (All positions), 8. Succesful Plays (All positions), 9. Yards Gained (All positions), 10. Total Offensive Plays in the 3rd Quarter (All positions). The model accounted for 78.2% of variance. The model succesfully accounted for predicting post-season qualifying teams in 78.2% of instances. 

![Feature Descriptions](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/figure_description_table.png)

**Figure 3:** Description for top features included in ANOVA regression model


![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_pvalue_table_2009.png)

**Figure 4:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)


#### 2016-2018 Skill Position Player Performance as Playoff Predictor

We paralleled our analysis from the 2009-2011 analysis above in completing the 2016-2018 analysis represented in Figures 5-7. Figure 5 represents the player count that qualified for post-season play (orange) and the nonpost-season players (blue). Again, player count was compared to the roughly 37.5% rate that should be expected for 12 teams out of 32 qualifying for post-season play. However, the rates were a bit below the 37.5% rate. This can be explained by the number of injuries and roster changes that occur througout the season. Teams shuffle in-and-out players at each position  based on injury or performance. Teams will not have a static roster throughout the season, this includes post-season teams who cut players or put players on IR. These players, even tough they played for post-season qualifying teams, would be in blue because they are not on the post-season rosters for the teams who qualify for post-season play. This along with the roster structure described for figure 1 explains the lower than 1/3 rate of players qualifying for post-season play.

![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2016-2018.png)

**Figure 5:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2016-2018)



![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_Count_Position_2016.png)

**Figure 6:** Count of Play-type by Post-Season Qualification category (20016-2018)



![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_pvalue_table_2016.png)

**Figure 7:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)


### Comparative Results


![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2009.png)

**Figure 8:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)


![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2016.png)

**Figure 9:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)

Cloudmesh Comon [^cloudmesh-benchmark] is used to create the benchmark.

## 6. Discussion


## 7. Conclusion

This section will be addressed upon project completion.

## 8. Acknowledgements 

## Project Plan

- [ ] will be deleted in final submission
- [ ] can not be after Refernce section

Nov. 02, 2020
-Complete a draft of the introduction section and the inferences section

Nov. 09, 2020
- build a functioning read in for all csv files needed using curl or another python function. Complete descriptive statistic analysis on regular season variables. (Model should look at player performance and whether that player made the nfl postseason the year of their recorded performance metrics). 

Nov. 16, 2020
-complete background and previous work section. Work on building prediction model for players making the postseason, train the machine to predict based on variables. 

Nov. 23, 2020
- Finish model to see how accurate the machine or model is at predicting players making the post-season. Write a conclusion section to based on model.

Dec. 1, 2020
- Polish paper, write abstract and table of contents sections.

Dec. 8, 2020
- Make any changes requested by TA's 


## 9. References

[^1]: Seifert, K. (2020, June 18). How pro football has changed in the past 10 years: 12 ways the NFL evolved this decade. Retrieved November 17, 2020, from <https://www.espn.com/nfl/story/_/id/28373283/how-pro-football-changed-10-years-12-ways-nfl-evolved-decade>

[^2]: Zita, C. (2020, September 16). Improving a Famous NFL Prediction Model. Retrieved November 02, 2020, from <https://towardsdatascience.com/improving-a-famous-nfl-prediction-model-1295a7022859>

[^3]: Silver, N. (2018, September 05). How Our NFL Predictions Work. Retrieved November 02, 2020, from <https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/>

[^4]: Ryurko. Ryurko/NflscrapR-Data. 2 Mar. 2020, <https://github.com/ryurko/nflscrapR-data>.

[^5]: Sports Reference, LLC. Pro Football Statistics and History.  Retrieved October 09, 2020. <https://www.pro-football-reference.com/>

[^cloudmesh-benchmark]: Gregor von Laszewski, Cloudmesh StopWatch and Benchmark from the Cloudmesh Common Library, <https://github.com/cloudmesh/cloudmesh-common>



