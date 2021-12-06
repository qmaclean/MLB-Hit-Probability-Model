# MLB-Hit-Probability-Model
The purpose of this analysis is to model the probability of a hit given a ball in play. We will use this model to evaluate and find the batter that had the most hits added vs. expected. We will also see what variables contribute to a higher probability of hits as a way to compare players. We will have data from the current 2021 season through the end of May. The two months of data will be used to build our preliminary model.

## Data
Baseball_scraped_data -> uses pybaseball package in Python. We used 2021 baseball season from March to May for exploratory data analysis. 

MLB Ids.csv comes from: http://www.smartfantasybaseball.com/tools/
-This site has a lot of referential IDs across multiple sites. 

Data regarding upcoming free agents comes from: https://legacy.baseballprospectus.com/compensation/cots/league-info/potential-2020-free-agents/




## Exploratory Data Analysis
We see that most balls into place are shallow outfield and that those balls hit into the infield are likely outs. We can derive that line-drive hits are more likely to become hits.

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/babip_outs.png" width="75%" />

Line drives can be determined from a batter’s launch angle and speed. Fangraphs derived that ground balls are less than 10 degrees, line drives are between 10-26 degrees, fly balls are 26-39 degrees and pop-ups are greater than 39 degrees. You can see the light orange below are those with the launch angle of 10 -26 degrees.

Link: https://fantasy.fangraphs.com/anglebbtypes/

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/babip_la.png" width="75%" />

Launch angle isn’t the only variable as the exit velocity or launch speed can determine how hard the ball comes of the bat. MLB Statcast defines a hard hit is those with a launch speed of greater than 95. We can see there’s a high concentration of batter’s with hard hits overall.

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/ls_la_density.png" width="75%" />

Nick Castellanos & JD Martinez have a conistent launch angle for hard hit balls in play, which results in a higher percentage of hits as a result. Eric Hosmer has the lowest average launch angle resulting in a lower conversion of his hard hit balls resulting in hits. His average launch angle of 4 degrees is likely a hard hit ground ball, which has been fielded appropriately.

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/hard_hit.png" width="75%" />

If we view Nick Castellanos hard hits solely in both home and NL Central ballparks during the 2021 season (thru end of May). We can see how much he stretches the hit at home. Even at Wrigley, he’s hit hard line drives between Left & Center. His aim & velocity has contributed to his early season success.

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/castellanos.png" width="75%" />

On the contrary, we can see Eric Hosmer’s hard hit ground balls at Petco. If he were to increase his launch angle by nearly ~4 to 6 degrees at least, he’d have a lot more hits.

<img src="https://github.com/qmaclean/MLB-Hit-Probability-Model/blob/main/images/hosmer.png" width="75%" />

## Model Fitting
Using caret package to build models. Ultimate model: 
Hits ~ hc_x + hc_y + launch_angle + launch_speed + launch_speed_angle

Fit using a 5 CV method with the random Forests being the final model of choice. 

## Model Application
-Hits against shifts
-Optimized Launch Angle & Speed
-Hits Added (Who's hitting more than expected?)
-Who would be some targeted hitters based on their hard hit percentage? 

