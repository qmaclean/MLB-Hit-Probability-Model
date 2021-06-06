# MLB-Hit-Probability-Model
Modeling hits for balls in play in MLB

## Data
Baseball_scraped_data -> uses pybaseball package in Python. We used 2021 baseball season from March to May for exploratory data analysis. 

MLB Ids.csv comes from: http://www.smartfantasybaseball.com/tools/
-This site has a lot of referential IDs across multiple sites. 

Data regarding upcoming free agents comes from: https://legacy.baseballprospectus.com/compensation/cots/league-info/potential-2020-free-agents/

## Exploratory Data Analysis
Used GeomMLBStadiums & baseballr for exploratory analysis and data visualizations. 

## Model Fitting
Using caret package to build models. Ultimate model: 
Hits ~ hc_x + hc_y + launch_angle + launch_speed + launch_speed_angle

Fit using a 5 CV method with the random Forests being the final model of choice. 

## Model Application
-Hits against shifts
-Optimized Launch Angle & Speed
-Hits Added (Who's hitting more than expected?)
-Who would be some targeted hitters based on their hard hit percentage? 

