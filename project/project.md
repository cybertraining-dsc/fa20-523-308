# NFL Regular Season Skilled Position Player Performance as a Predictor of Playoff Appearance

- [ ] please follow our template
- [ ] remove other assignments out of this directory
- [ ] improve markdown skills
- [ ] use footnotes as refernces, learn how to do this, read our piaza posts

Travis Whitaker [fa20-523-308](https://github.com/cybertraining-dsc/fa20-523-308)


## Dataset

The dataset we will be using is in a github folder that holds nflscrapR-data that originates from NFL.com [1]. The folder includes play-by-play data, including performance measures, for all regular season games from 2009 to 2019. This file will be paired with week-by-week regular season roster data for each team in the NFL. This will allow me to track skilled position player performance during the regular season and then compare this regular season file with the files that contain playoff teams for each year from 2009-2019. Supplemental data may be pulled from Pro-Football-Reference.com or other sources depending on what preliminary data analysis presents [2].

## What needs to be done to get a great grade

The first step we am planning to take in understanding the data will be to use various slices of the data put into scatterplots and bar charts to find correlations and trends, as well as various time series charts. This will be an exploratory step in understanding the data. we may also deploy area charts to observe any interesting trends or segments of our data that may warrant additional analysis.

Then each metric from player performance during the regular season will be included in the analysis or algorithm that will be built to predict playoff appearance. Playoff appearance is a designation for a team qualifying for the post-season or playoffs. We am thinking it may be important to engineer some new features to potentially provide insights.  For instance, it is possible to determine whether a play was during the final two minutes of a half and if a play was in the red zone. During these critical points of a game a win or lose is often determined. So my thought is by weighing these moments and performance metrics with more importance in an algorithm the machine will better predict a team’s likelihood of making the playoffs. Another secondary metric that may strengthen the predictive ability of the algorithm would be to use Football Outsider’s Success Rate, which is a determination of a play’s success rate for the offense that is on the field [2]. This can also provide me with the down and distance to go for the offense and players that are on the field. We will also use college position designations as way to normalize the positions performance across teams. Many NFL teams utilize different player sets. Thus, it is important to use a standard, which college football uses across all teams. Since we am only interested in skill position players this will include Wide Receiver (WR), Running Back (RB), Full Back (FB), Quarterback (QB), and Tight End (TE). These designations will allow the algorithm to compare, if needed, the skill position performance across teams and by designation of players on that team for each metric utilized. 

After breaking down the data into key categorical variables to see if there was an impact for these performance variables in making the playoffs for the NFL teams. These individual position statistics will need to be paired with their teammate’s performance metrics so that each team is represented by all of their skill position players. It is often debated as to which position is most important in football and whether a QB is critical to a successful post-season appearance. My hope is that by combining each skill position player onto their respective team we will be able to better determine the importance of success at each position by whether or not that team made the playoffs. Further, it will be important to see whether roster makeup across teams varies by position. If roster makeup is stable than we will not need to combining positions. However, if roster makeup varies, we will need to combine positions into a larger group instead of two subgroups. The concern here is the deployment of WR over TE. Some teams may carry more TE than others and fewer WR. Therefor we would need to combine WR and TE into a group called Designated Receiver (DR). 

Metric measurement needs to be consistent across years. A comparison of year-to-year metrics will need to be done comparing each years measurements from 2009-2019 in order to make sure that the measurement techniques are stable and do not vary across time. If there are changes in the way metrics are measured than either that year will need to be dropped from the model or adjustments will need to be made to the metric to balance it with the other years included in the model. 

Finally, once all metrics have been balanced and the team performance metrics have been aggregated. The algorithm will need to be implemented to identify the eight best teams from each NFL division and the two best other teams in the conference that would constitute the wild card playoff teams from each conference. Once this analysis is run, we will be able to look at retroactive NFL post-season designated teams from 2009-2019 to see how accurate the playoff prediction machine was at identifying NFL post-season teams for each year. 

## References

[1] Ryurko. Ryurko/NflscrapR-Data. 2 Mar. 2020, github.com/ryurko/nflscrapR-data.
[2] Sports Reference, LLC. “Pro Football Statistics and History.”  Retrieved October 09, 2020. https://www.pro-football-reference.com/
