# NFL Regular Season Skilled Position Player Performance as a Predictor of Playoff Appearance Overtime

[![Check Report](https://github.com/cybertraining-dsc/fa20-523-308/workflows/Check%20Report/badge.svg)](https://github.com/cybertraining-dsc/fa20-523-308/actions)

Travis Whitaker, [fa20-523-308](https://github.com/cybertraining-dsc/fa20-523-308), [Edit](https://github.com/cybertraining-dsc/fa20-523-308/blob/main/project/project.md)


{{% pageinfo %}}

## Abstract

Contents

{{< table_of_contents >}}

{{% /pageinfo %}}

**Keywords:** ANOVA, Comparative Analysis, Exploratory Analysis, Football, Sports, Metrics

## 1. Introduction

In the modern NFL the biggest negotiating tools for players in signing a new contract is their on-field performance. Many players choose to "hold-out" of pre-season practice or regular season games as a negotiating tool in their attempt to sign a more lucrative contract. Players often feel as though their exceptional performance on the field is not reflected in the monetary compensation structure of their contract. This is most often reflected in skill position players such as wide receivers or running backs whose play on the field is most often celebrated (e.g., touchdowns) and discussed by fans of the game. While these positions are no doubt important to a team’s success, the question remains how important is one players contribution to a team’s overall success? Our project will attempt to evaluate the importance of skill position players' (i.e., Quarterback (QB), Wide Receiver (WR), Running Back (RB), and Tight End (TE)) performance during the regular season and use in-game performance metrics as a predictive factor for their team making the playoffs. This is an attempt to answer the question can qualifying for the post-season be predicted by skill position metrics measured during the regular season? If so, then which metrics are most crucial to predicting post-season birth?

A secondary analysis in this project will look at a comparison between 2009-2011 vs. 2016-2018 regular season metrics and build seperate models for each three year span to investigate whether a shift in performance metric importance has occured over the past decade. NFL insiders and journalists have noted the shift in play-calling over the past decade in the NFL as well as the change at the quarterback position to more "dual-threat" (running and throwing) quarterbacks that have transitioned the game to a more "aggresive" play-style [^1]. Yet punditry and reporting have not always been supported by performance metrics and this specific claim of a tranisition over the past decade needs some exploring. Therefore, we will be investigating whether there has been a shift in the performance metrics that are important in predicting team success. Again, team success will be measured by making the post-season. 

## 2. Background Research and Previous Work

There are many playoff predictor models that focus on team performance or team wins vs losses as a predictor of making the playoffs [^2]. However, few take into consideration individual player performance as an indicator of their team making the post-season playoffs in the NFL. The most famous model that takes into consideration player performance is ELO rating [^3]. The first ELO rating was a straightforward model that took head-to-head results and player-vs-team model in order to predict win probability in an NFL game. However, in 2019 Silver and his team at FiveThirtyEight updated their ELO model to give a value rating to the quarterback position for each team. This quarterback value included metrics such as pass attempts, completions, passing yards, passing touchdowns, interceptions, sacks, rush attempts, rushing yards, and rushing touchdowns. Taking these metrics along with the defensive quality metrics, which is an adjustment of quarterback value based on the opposing defense ranking, gives you an overall value for your quarterback. Thus, this widely accepted model takes head-to-head team comparisons on a week-to-week basis and includes the quarterback value in predicting these head-to-head matchup. However, no model has taken just player performance and tried to predict team success based on each of their individual players. These previous models primarily look at offensive vs. defensive units and try to predict win/loss records based off each of these units.

The goal of the present research is not to compare our model vs previous models, as these standing models are not meant for playoff prediction, rather a game-by-game matchup comparison. The present research investigates whether looking at position players at each of the skilled positions maps onto predicting the playoff teams. Further, how does this prediction change over time? Looking at 2009-2011 NFL skill player peroformance vs 2016-2018 skill player performance we will investigate if there are differences in metrics that predict playoff appearance. This will show us whether there are shifts in the positions that are most important for predicting playoff appearance (i.e., QB, WR, TE, RB) then this model will show us if there are specific metrics at each position that are important for predicting success. For example, if the wide receiver position is important, what is most important about that position, yards-after-catch or number of receptions. Further, how might the importance of those metrics shift over time. We hope to explore and understand better the impact of skill players and the metrics that they are measured on in terms of making the playoffs.

## 3. Choice of Data-sets

The dataset we will be using is in a github folder that holds nflscrapR-data that originates from NFL.com [^4]. The folder includes play-by-play data, including performance measures, for all regular season games from 2009 to 2019. This file will be paired with week-by-week regular season roster data for each team in the NFL. This will allow me to track skilled position player performance during the regular season and then compare this regular season file with the files that contain playoff teams for each year from 2009-2019. Supplemental data may be pulled from Pro-Football-Reference.com or other sources depending on what preliminary data analysis presents [^5].

## 4. Methodology

The first step we am planning to take in understanding the data will be to use various slices of the data put into scatterplots and bar charts to find correlations and trends, as well as various time series charts. This will be an exploratory step in understanding the data. we may also deploy area charts to observe any interesting trends or segments of our data that may warrant additional analysis.

Then each metric from player performance during the regular season will be included in the analysis or algorithm that will be built to predict playoff appearance. Playoff appearance is a designation for a team qualifying for the post-season or playoffs. We am thinking it may be important to engineer some new features to potentially provide insights.  For instance, it is possible to determine whether a play was during the final two minutes of a half and if a play was in the red zone. During these critical points of a game a win or lose is often determined. So my thought is by weighing these moments and performance metrics with more importance in an algorithm the machine will better predict a team’s likelihood of making the playoffs. Another secondary metric that may strengthen the predictive ability of the algorithm would be to use Football Outsider’s Success Rate, which is a determination of a play’s success rate for the offense that is on the field [^5]. This can also provide me with the down and distance to go for the offense and players that are on the field. We will also use college position designations as way to normalize the positions performance across teams. Many NFL teams utilize different player sets. Thus, it is important to use a standard, which college football uses across all teams. Since we am only interested in skill position players this will include Wide Receiver (WR), Running Back (RB), Full Back (FB), Quarterback (QB), and Tight End (TE). These designations will allow the algorithm to compare, if needed, the skill position performance across teams and by designation of players on that team for each metric utilized. 

After breaking down the data into key categorical variables to see if there was an impact for these performance variables in making the playoffs for the NFL teams. These individual position statistics will need to be paired with their teammate’s performance metrics so that each team is represented by all of their skill position players. It is often debated as to which position is most important in football and whether a QB is critical to a successful post-season appearance. My hope is that by combining each skill position player onto their respective team we will be able to better determine the importance of success at each position by whether or not that team made the playoffs. Further, it will be important to see whether roster makeup across teams varies by position. If roster makeup is stable than we will not need to combining positions. However, if roster makeup varies, we will need to combine positions into a larger group instead of two subgroups. The concern here is the deployment of WR over TE. Some teams may carry more TE than others and fewer WR. Therefor we would need to combine WR and TE into a group called Designated Receiver (DR). 

Metric measurement needs to be consistent across years. A comparison of year-to-year metrics will need to be done comparing each years measurements from 2009-2019 in order to make sure that the measurement techniques are stable and do not vary across time. If there are changes in the way metrics are measured than either that year will need to be dropped from the model or adjustments will need to be made to the metric to balance it with the other years included in the model. 

Finally, once all metrics have been balanced and the team performance metrics have been aggregated. The algorithm will need to be implemented to identify the eight best teams from each NFL division and the two best other teams in the conference that would constitute the wild card playoff teams from each conference. Once this analysis is run, we will be able to look at retroactive NFL post-season designated teams from 2009-2019 to see how accurate the playoff prediction machine was at identifying NFL post-season teams for each year. 

## 5. Inference

An individual player-performance model for NFL skill position players (i.e., quarterback, wide receiver, tight end, and running back) will perform better than chance level (50%) of identifying playoff teams from the NFL during the season's of 2009-2019. Further, an exploratory analysis of time periods (2009-2011 vs 2016-2018) will expose differences in the key metrics that are used to predict playoff appearance over time. This will give us a better understanding of the shifts in perfromance in the NFL at each skill position.

### Preliminary Results

#### 2009-2011 Skill Position Player Performance as Playoff Predictor

**Figure 1:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2009-2011)
![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2009_2011.png)

**Figure 2:** Count of Play-type by Post-Season Qualification category (2009-2011)
![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_count_position_2009.png)

**Figure 3:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)
![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_metric_importance_2009.png)

#### 2016-2018 Skill Position Player Performance as Playoff Predictor

**Figure 4:** Breakdown of Players by Skill Position That Qualified for Post-Season Play (2016-2018)
![Player Qualifying for Post-Season](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Player_summary_2016-2018.png)

**Figure 5:** Count of Play-type by Post-Season Qualification category (20016-2018)
![Count of Play-type by Post-Season Qualification category](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Play_Count_Position_2016.png)

**Figure 6:** ANOVA Table for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)
![ANOVA for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_Metric_importance_2016.png)

### Comparative Results

**Figure 7:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2009-2011)
![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2009.png)

**Figure 8:** ANOVA Chart for Metrics Measured as Predictors for Teams Qualifying for Post-Season Play (2016-2018)
![ANOVA Chart for Metric Importance in Model](https://github.com/cybertraining-dsc/fa20-523-308/raw/main/project/images/Anova_sig_features_2016.png)

## 6. Conclusion

This section will be addressed upon project completion.

## 7. Acknowledgements 

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


## 8. References

[^1] Seifert, K. (2020, June 18). How pro football has changed in the past 10 years: 12 ways the NFL evolved this decade. Retrieved November 17, 2020, from <https://www.espn.com/nfl/story/_/id/28373283/how-pro-football-changed-10-years-12-ways-nfl-evolved-decade>

[^2]: Zita, C. (2020, September 16). Improving a Famous NFL Prediction Model. Retrieved November 02, 2020, from <https://towardsdatascience.com/improving-a-famous-nfl-prediction-model-1295a7022859>

[^3]: Silver, N. (2018, September 05). How Our NFL Predictions Work. Retrieved November 02, 2020, from <https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/>

[^4]: Ryurko. Ryurko/NflscrapR-Data. 2 Mar. 2020, <https://github.com/ryurko/nflscrapR-data>.

[^5]: Sports Reference, LLC. Pro Football Statistics and History.  Retrieved October 09, 2020. <https://www.pro-football-reference.com/>




