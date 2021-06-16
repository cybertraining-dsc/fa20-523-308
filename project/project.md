---
date: 2021-03-15
title: NFL Regular Season Skilled Position Player Performance as a Predictor of Playoff Appearance Overtime
linkTitle: NFL
tags: ["project", "ai", "sports"]
description: "The present research investigates the value of in-game performance metrics for NFL skill position players (i.e., Quarterback, Wide Receiver, Tight End, Running Back and Full Back) in predicting post-season qualification. Utilizing nflscrapR-data that collects all regular season in-game performance metrics between 2009-2018, we are able to analyze the value of each of these in-game metrics by including them in a regression model that explores each variables strength in predicting post-season qualification. We also explore a comparative analysis between two time periods in the NFL (2009-2011 vs 2016-2018) to see if there is a shift in the critical metrics that predict post-season qualification for NFL teams. Theoretically, this could help inform the debate as to whether there has been a shift in the style of play in the NFL across the previous decade and where those changes may be taking place according to the data. Implications and future research are discussed."
author: Travis Whitaker
resources:
- src: "**.{png,jpg}"
  title: "Image #:counter"
---


[![Check Report](https://github.com/cybertraining-dsc/fa20-523-308/workflows/Check%20Report/badge.svg)](https://github.com/cybertraining-dsc/fa20-523-308/actions)
[![Status](https://github.com/cybertraining-dsc/fa20-523-308/workflows/Status/badge.svg)](https://github.com/cybertraining-dsc/fa20-523-308/actions)
Status: final, Type: Project


Travis Whitaker, [fa20-523-308](https://github.com/cybertraining-dsc/fa20-523-308), [Edit](https://github.com/cybertraining-dsc/fa20-523-308/blob/main/project/project.md)

{{% pageinfo %}}

## Abstract

The present research investigates the value of in-game performance metrics for NFL skill position players (i.e., Quarterback, Wide Receiver, Tight End, Running Back and Full Back) in predicting post-season qualification. Utilizing nflscrapR-data that collects all regular season in-game performance metrics between 2009-2018, we are able to analyze the value of each of these in-game metrics by including them in a regression model that explores each variables strength in predicting post-season qualification. We also explore a comparative analysis between two time periods in the NFL (2009-2011 vs 2016-2018) to see if there is a shift in the critical metrics that predict post-season qualification for NFL teams. Theoretically, this could help inform the debate as to whether there has been a shift in the style of play in the NFL across the previous decade and where those changes may be taking place according to the data. Implications and future research are discussed. 

Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** ANOVA, Comparative Analysis, Exploratory Analysis, Football, Sports, Metrics

## 1. Introduction

In the modern NFL the biggest negotiating tools for players in signing a new contract is their on-field performance. Many players choose to "hold-out" of pre-season practice or regular season games as a negotiating tool in their attempt to sign a more lucrative contract. In this situation players feel as though their exceptional performance on the field is not reflected in the monetary compensation structure of their contract. This is most often reflected in skill position players such as wide receivers or running backs whose play on the field is most often celebrated (e.g., touchdowns) and discussed by fans of the game. While these positions are no doubt important to a team’s success, the question remains how important is one players contribution to a team’s overall success? The current project will attempt to evaluate the importance of skill position players' (i.e., Quarterback (QB), Wide Receiver (WR), Running Back (RB), and Tight End (TE)) performance during the regular season and use in-game performance metrics as a predictive factor for their team making the playoffs. This is an attempt to answer the question can qualifying for the post-season be predicted by skill position metrics measured during the regular season? If so, then which metrics are most crucial to predicting post-season qualification?

A secondary analysis in this project will look at a comparison between 2009-2011 vs. 2016-2018 regular season metrics and build separate models for each three year span to investigate whether a shift in performance metric importance has occurred over the past decade. NFL insiders and journalists have noted the shift in play-calling over the past decade in the NFL as well as the change at the quarterback position to more "dual-threat" (running and throwing) quarterbacks that have transitioned the game to a more "aggressive" play-style [^1]. Yet punditry and reporting have not always been supported by performance metrics and this specific claim of a transition over the past decade needs some exploring. Therefore, we will be investigating whether there has been a shift in the performance metrics that are important in predicting team success. Again, team success will be measured by making the post-season. 

## 2. Background Research and Previous Work

There are many playoff predictor models that focus on team performance or team wins vs losses as a predictor of making the playoffs [^2]. However, few take into consideration individual player performance as an indicator of their team making the post-season playoffs in the NFL. The most famous model that takes into consideration player performance is ELO rating [^3]. The first ELO rating was a straightforward model that took head-to-head results and player-vs-team model to predict win probability in an NFL game. However, in 2019 Silver and his team at FiveThirtyEight updated their ELO model to give a value rating to the quarterback position for each team. This quarterback value included metrics such as pass attempts, completions, passing yards, passing touchdowns, interceptions, sacks, rush attempts, rushing yards, and rushing touchdowns. Taking these metrics along with the defensive quality metrics, which is an adjustment of quarterback value based on the opposing defense ranking, gives you an overall value for your quarterback. Thus, this widely accepted model takes head-to-head team comparisons on a week-to-week basis and includes the quarterback value in predicting the winners of these head-to-head matchups. However, no model has taken just player performance and tried to predict team success for an entire regular season based on each of their individual players. These previous models primarily look at offensive vs. defensive units and try to predict win/loss records based off each of these units.

The goal of the present research is not to compare our model vs previous models, as these standing models are not meant for playoff prediction, rather these previous models are used for a game-by-game matchup comparison. The present research investigates whether looking at position players at each of the skilled positions, maps onto predicting the post-season qualifying teams. Further, how does this predictive model change over time? Looking at 2009-2011 NFL skill player performance vs 2016-2018 skill player performance we will investigate if there are differences in metrics that predict post-season appearance. This will show us whether there are shifts in skill position play that impact predicting post-season playoff appearance. Specifically, by comparing the two models which use two different periods of time (i.e., 2009-2011 vs 2016-2018) we will be able to better investigate specific metrics at each position that are important for predicting success. For example, if the wide receiver position is important, what is most important about that position, yards-after-catch or number of receptions? Further, how might the importance of those metrics shift over time? We hope to explore and understand better the impact of skill players and the metrics that they are measured on in terms of making the post-season.

## 3. Choice of Data-sets

The datasets used are in a github folder that holds nflscrapR-data that originates from NFL.com [^4]. The folder includes play-by-play data, including performance measures, for all regular season games from 2009 to 2019. This file was paired with week-by-week regular season roster data for each team in the NFL. This allowed us to track skilled position player performance during the regular season and then compare this regular season file with the files that contain playoff teams for each year from 2009-2019. Supplemental data was pulled from Pro-Football-Reference.com [^5].

## 4. Methodology

The first step we took to understand the data was to use various slices of the data put into scatterplots and bar charts to find trends, as well as various time series charts. This was an exploratory step in understanding the data. 

Then each metric from player performance during the regular season was included in the analysis or models that were built to predict post-season appearance. Post-season appearance is a designation for a team qualifying for the post-season or playoffs. We think it is important to engineer some new features to potentially provide insights.  For instance, it is possible to determine whether a play was during the final two minutes of a half and if a play was in the red zone. During these critical points of a game a win or lose is often determined. Our thought is by weighing these moments and performance metrics with more importance the model will better predict a team’s likelihood of making the playoffs. Another secondary metric that may strengthen the predictive ability of the model would be to use Football Outsider’s Success Rate, which is a determination of a play’s success rate for the offense that is on the field [^5]. This can also provide me with the down and distance to go for the offense and players that are on the field. We will also use college position designations as way to normalize the positions performance across teams. Many NFL teams utilize different player sets. Thus, it is important to use a standard, which college football uses across all teams. Since we are only interested in skill position players this will include Wide Receiver (WR), Running Back (RB), Full Back (FB), Quarterback (QB), and Tight End (TE). These designations will allow the model to compare player performance by position. 

After breaking down the data into key categorical variables to see if there was an impact for these performance variables in making the playoffs for the NFL teams. These individual position statistics were analyzed as a group and then separated into "Post Season" meaning the player's team qualified for the playoffs, or "No Post" meaning the player's team did not qualify for the playoffs. By doing this we were able to verify that a reasonable number of players fell into the "Post Season" group, as only 12 out of 32 teams qualify for the post-season. Further we were able to use these designations in the next step of modeling, where the data was analyzed in an ANOVA to see how important each metric was in predicting post-season appearance for each player.

Metric measurement needs to be consistent across years. A comparison of year-to-year metrics was completed comparing each years measurements from 2009-2011 and 2016-2018 in order to make sure that the measurement techniques were stable and do not vary across time. If there were changes in the way metrics are measured than either that year will need to be dropped from the model or adjustments will need to be made to the metric to balance it with the other years included in the model. Luckily, there were no variation in metric measurement across years, so all measurements initially included in the model were kept. 

Finally, once all metrics were balanced and the team performance metrics had been aggregated. The ANOVA model was built to analyze metric measurement as a predictor of a player making post-season play. This ANOVA model was created twice, once for the 2009-2011 players and then again for the 2016-2018 players. Once this analysis was run, we were able to see the strength of the model in predicting playoff appearance by player, based on metric measurement.

## 5. Results

### Inference

An individual player-performance model for NFL skill position players (i.e., quarterback, wide receiver, tight end, and running back) will perform better than chance level (50%) of identifying playoff teams from the NFL during the season's of 2009-2011 and 2016-2018. Further, an exploratory analysis of time periods (2009-2011 vs 2016-2018) will expose differences in the key metrics that are used to predict playoff appearance over time. This will give us a better understanding of the shifts in performance in the NFL at each skill position.

### Preliminary Results

The descriptive statistics for the player performance revealed no issues with normality or different metric standards across seasons for player performance measurements. Figure 1 represents a count check for players qualifying for the post-season in the seasons of 2009-2011. Based on the NFL post-season structure 12 out of 32 teams qualify for the post-season, or 37.5%. Figure 1 shows that roughly 1/3 of players qualify for the post season at each position. However, it is important to note that each team structure and roster is different. For example, one team may carry 7 receivers, 2 running backs, 2, quarter backs, 2 tight ends, and 0 full backs, where another team may carry 4 receivers, 4 running backs, 3 quarter backs, 4 tight ends, and 1 full back. This is an important distinction to make because the "Post Season" players shown in figure 1 are not at an equal percentage across position. 

#### 2009-2011 Skill Position Player Performance as Playoff Predictor


![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2009_2011.png)

**Figure 1:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2009-2011)

We also wanted to investigate whether play-count at each position was balanced across post-season players and players who did not qualify for the post-season. Figure 2 shows that players on teams who did qualify for the post-season were involved in more plays at their position than players at their position who did not qualify for the playoffs. Thinking about this finding as a result of the regular season, players in skilled positions on post-season qualifying teams play on offenses that won more games than teams who did not qualify for the playoffs. While we did not look at time of possession for players by position, it seems fairly reasonable through logic and the results in figure 2 that play count is higher because these teams are more successful and the players on post-season qualifying teams are on the field more than teams with more losses who did not qualify for the post-season.

![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_count_position_2009.png)

**Figure 2:** Count of Play-type by Post-Season Qualification category (2009-2011)

Figure 3 below is a reference table for the features included in the ANOVA regression model determining the key features that predict post-season qualification. These features are used for reference in figures 4 and 7. 

Using the player performance metrics for the regular season, an ANOVA was run to see if these metrics placed together would be a successful predictor of post-season qualification. Figure 4 shows the top 10 metrics that had the highest f-values for predicting post-season qualification, all of which were all significant (p<.05) in the model. Reviewing the model, the most significant factors for predicting post-season qualification for teams in order were; 1. Successful Reception (wide receiver or tight end), 2. Total Receiving Yards (Wide Receiver or Tight End), 3. Yards After Catch (wide receiver or tight end), 4. Total Receiving Touchdowns (Wide Receiver or Tight End), 5. Total Touchdowns (All positions), 6. Receiver Plays (Wide Receiver), 7. Redzone Plays (All positions), 8. Successful Plays (All positions), 9. Yards Gained (All positions), 10. Total Offensive Plays in the 3rd Quarter (All positions). The model accounted for 78.2% of variance. The model successfully accounted for predicting post-season qualifying teams in 78.2% of instances. 

![Feature Descriptions](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/figure_description_table.png)

**Figure 3:** Description for top features included in ANOVA regression model


![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_pvalue_table_2009.png)

**Figure 4:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)


#### 2016-2018 Skill Position Player Performance as Playoff Predictor

We paralleled our analysis from the 2009-2011 analysis above in completing the 2016-2018 analysis represented in Figures 5-7. Figure 5 represents the player count that qualified for post-season play (orange) and the non-post-season players (blue). Again, player count was compared to the roughly 37.5% rate that should be expected for 12 teams out of 32 qualifying for post-season play. However, the rates were a bit below the 37.5% rate. This can be explained by the number of injuries and roster changes that occur throughout the season. Teams shuffle in-and-out players at each position based on injury or performance. Teams will not have a static roster throughout the season, this includes post-season teams who cut players or put players on IR. These players, even though they played for post-season qualifying teams, would be in blue because they are not on the post-season rosters for the teams who qualify for post-season play. This along with the roster structure described for figure 1 explains the lower than 1/3 rate of players qualifying for post-season play.

![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2016-2018.png)

**Figure 5:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2016-2018)

Figure 6 investigates play-count at each position, like figure 2, but this time for the seasons of 2016-2018. Again, the analysis was balanced across post-season players and players who did not qualify for the post-season. Figure 6 shows that players on teams who did qualify for the post-season were involved in more plays at their position than players at their position who did not qualify for the playoffs. Figure 6 shows a consistent pattern with figure 2. Descriptive statistic comparison between the 2009-2011 seasons and the 2016-2018 seasons will be revisited in the discussion section.

![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_Count_Position_2016.png)

**Figure 6:** Count of Play-type by Post-Season Qualification category (20016-2018)

Using the player performance metrics for the regular season, an ANOVA was run to see if these metrics placed together would be a successful predictor of post-season qualification. Figure 7 shows the top 10 metrics that had the highest f-values for predicting post-season qualification, all of which were significant (p<.05) in the model. The model successfully accounted for predicting post-season qualifying teams in 77.8% of instances.

![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_pvalue_table_2016.png)

**Figure 7:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)


### Comparative Results

Comparing the 2016-2018 with the 2009-2011 season model, certain shifts have occurred from the 2009-2011 seasons model. Namely, yards-after-catch has become the strongest predictor of post-season qualification, flipping positions with successful reception in the 2009-2011 model. Another notable shift is the importance of number of plays run in the second quarter in the 2016-2018 model, overtaking number of plays run in the third quarter from the 2009-2011. The models themselves also shift in their strength of prediction. The 2009-2011 model shows stronger predictive capability (78.2% vs 77.8%), which is reflected in the f-values for the top 10 metrics of the model. The 2009-2011 model has four variables with f-values above 50 and one above 60. The 2016-2018 model only has one variable with an f-value above 50. These values represent the variance accounted for in the model by a variable. The higher the f-value the more variance accounted for in the model by that specific variable. Since the f-values were so high for many of the top 10 variables listed in each model, the p-values showed highly significant far exceeding the p=.05 level that was needed. The f-values were high because they accounted for so much of the variance in the model, meaning the predictive nature of the model was due in large part to many of the variables in the top 10. Another way to state this is that each of these top 10 variables were significantly better at predicting post-season qualification than would be expected due to chance. 

![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2009.png)

**Figure 8:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)


![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2016.png)

**Figure 9:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)

Cloudmesh Comon [^cloudmesh-benchmark] is used to create the benchmark.

## 6. Discussion

The first inference of this project was investigating the possibility of using in-game performance metrics as a competent and better-than-chance predictor of selecting skill position players making the NFL post-season. Both the 2009-2011 and the 2016-2018 season models were able to predict player post-season qualification at 78.2% and 77.8% levels of success, both above chance level. This success highlights the critical nature of skill performance players and provides confidence to the modern metric model of NFL players as a useful and qualified tool to evaluate player performance as a measure of success. This also gives clout to the skill position players who believe their contributions on the field are deserving of top dollar compensation in the NFL. According to our models, wide receivers are deserving of high compensation as their game play impacts the likelihood of their team making the playoff more than running backs. However, it is hard to discriminate whether quarterback play is also key to the success of wide receivers. It could well be that these two positions work hand-in-hand. 

Investigating the second inference regarding changes in the predictive model across time. In comparing the descriptive statistic models (figs. 1, 2 vs. 5, 6). There are some noticeable, but not significant differences in the two-time ranges. First, there are more receivers in the 2016-2018 time range, which reflects the NFL’s shift towards a more pass prone league. Since there was not an increase in roster size between the two-time ranges, the increase in receivers lead to a decrease in the number of quarterbacks and fullbacks on a roster, but these additional receivers carried probably took the roster spots of non-skill positions players that are not accounted for here. Both models show the importance of pass plays, successful pass plays, receiving touchdowns and yards, yards after catch, and other passing variables that highlight the importance of wide receivers and tight ends. The NFL has shifted towards a more pass-friendly league [^1], and the models built here highlight the reasons why that occurred. Receiver plays are significantly more important in predicting post-season qualification than any other skill position metrics. It is likely that the shift towards receivers and away from running backs has taken place over time. It is possible that we have pulled two time periods that are too close together to reflect the shift in NFL play, and if we had pulled data from the 1990’s or 1980’s (unfortunately this data is not available in the needed metrics) we would see more running back heavy metrics at the tops of our models and significant changes in the two time periods.

### Limitations and Future Research

Metrics are not provided for non-skill position players who could be critical in predicting playoff qualification. For instance, if we could include offensive linemen metrics, we would have a stronger model that would be better able to predict post-season qualification. Further, the NFL data we had access to does not measure defensive player metrics that we believe are critical in being able to predict post-season qualification for NFL teams. Future work should look to include defensive player metrics into their model, as well as non-skill position players to improve on this model. 

Though we were able to build a model to predict player qualification for the post-season, future research can build on this model by making a composite of players on a team to then predict a team making the playoffs. The present study is a nice first step in understanding the capabilities of game performance for predicting player success, but NFL teams are equally interested in a team's success, not just individual skill players. Therefore, future research can build on this project by incorporating defensive player metrics, non-skill position offensive metrics, and composites of players on one team to predict a team's projected chances of making the playoffs.

## 7. Conclusion

Utilizing skill position performance metrics shows to be a successful predictor of player post-season qualification above chance level (50%). Further, there are slight shifts in which metrics are best at predicting post-season qualification between the 2009-2011 and 2016-2018 time periods. However, the key metrics that were significant in both models from the two time periods (2009-2011 and 2016-2018) did not change. Therefore, we cannot say definitively that there has been a shift in style of play from 2009 to 2018. 

## 8. Acknowledgements 

Thank you to my friends and family who supported me through working on this project.

## 9. References

[^1]: Seifert, K. (2020, June 18). How pro football has changed in the past 10 years: 12 ways the NFL evolved this decade. Retrieved November 17, 2020, from <https://www.espn.com/nfl/story/_/id/28373283/how-pro-football-changed-10-years-12-ways-nfl-evolved-decade>

[^2]: Zita, C. (2020, September 16). Improving a Famous NFL Prediction Model. Retrieved November 02, 2020, from <https://towardsdatascience.com/improving-a-famous-nfl-prediction-model-1295a7022859>

[^3]: Silver, N. (2018, September 05). How Our NFL Predictions Work. Retrieved November 02, 2020, from <https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/>

[^4]: Ryurko. Ryurko/NflscrapR-Data. 2 Mar. 2020, <https://github.com/ryurko/nflscrapR-data>.

[^5]: Sports Reference, LLC. Pro Football Statistics and History.  Retrieved October 09, 2020. <https://www.pro-football-reference.com/>

[^cloudmesh-benchmark]: Gregor von Laszewski, Cloudmesh StopWatch and Benchmark from the Cloudmesh Common Library, <https://github.com/cloudmesh/cloudmesh-common>



