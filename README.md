# Fantasy Football Manager Rating

## Inspiration:
I’ve noticed, in my years of competing in fantasy football, that the same handful of managers tend to be at the top of the league every year. Although luck certainly plays its part in the outcomes of matchups, in my observation, success in fantasy football is highly correlated with the skill on the manager. And the US agrees with this observation; fantasy football has been legal in the country due to skill component even when sports betting was overwhelmingly illegal. The equation I came up with attempts to mitigate one specific factor of luck in fantasy football by weighing both performance vs opponent and performance vs median score of the league participants in that week. Opponent performance is something a manager has no control over, so taking performance vs median into account is a crucial part of my equation. It would be difficult to argue that a manager who consistently scores below the median and takes advantage of an easy schedule is somehow better than a manager that consistently scores above the median and is burdened with tough matchups. As for the importance of performance vs opponent, I have another example. Take, for instance, a manager who knows they are projected to lose their matchup. This manager will likely start a more volatile option who has the potential to “boom” than a consistent option who doesn’t have a “boom” in their range of outcomes. Additionally, the ultimate goal for a manager is to win their matchup, so this must be a point of emphasis in the rating.

## Data Collection:
I used the [sleeper wrapper package](https://github.com/dtsong/sleeper-api-wrapper) to pull data from sleeper's API. 

## Equations:
Elo vs opponent:
![](readme_images/vprime.PNG)

Elo vs median:
![](readme_images/mprime.PNG)

Manager Rating:
![](readme_images/mrating.PNG)

The original equation that I started with equally weighs Elo for the performance vs opponent and performance vs median (above), so the formula was just the basic average of the two ratings(α=0.5). I decided to write the equation in a more general form with α being the determining factor for the weight. I believe the optimal α will be between 0.15 and 0.35, which would mean performance vs median is much more indicative of success than performance vs opponent.  

Mean Regression Rate:
![](readme_images/mrr.PNG)

In this equation, β is a value between 0 and 1 that regresses each rating to the mean at the beginning of each season. I got this idea from FiveThirtyEight’s NFL game predictions.

https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/

The NFL model has a mean regression rate of 1/3, but fantasy football is much more volatile because each team is completely wiped out each after each season. Thus, I believe the optimal β value will be somewhere between 0.5 and .75.

## Optimization:

I used a for loop to interate through 441 different combinations of alphas and betas and decided I wanted to optimize for a combination of full league accuracy and 2022 accuracy. Note that accuracy is just the ratio of correctly predicted outcomes to total number of outcomes.

![](readme_images/alphabeta_table.PNG)

The score column is simply Accuracy + 2022 Accuracy.

Here is a scatterplot showing the combinations of alpha and beta using color to show score:

![](readme_images/alphabeta_scatter1.png)

This plot provided a clear range for the optimal parameters. Alpha should be somewhere in the range (0.4,0.6) and Beta should be mewhere in the range (0.1,0.2). Also this shows that changes in Beta impact score more than changes in Alpha.

I then used scipy's curve fit function to find more precise values for the opimal Alpha and Beta.

This worked really well for Alpha:

![](readme_images/alpha_plot.png)

Alpha = .5538

Not so much for Beta:

![](readme_images/beta_plot.png)

I couldn't find a curve that was a good fit for the data, but I knew I wanted to investigate the peak between Beta = .5 and Beta .15. So, I decided to run a loop with Alpha = .5538 and Beta in (.05,.15) incrementing by .01:

![](readme_images/beta_opt.PNG)
![](readme_images/beta_opt2.PNG)

Hence, I chose Beta = .12

## Results:
The percentage of correctly predicted games by the rating system:
![](readme_images/opt_pred_perc.PNG)

By Year:

![](readme_images/perc_by_year.PNG)

By Week:

![](readme_images/perc_by_week.PNG)

 
## Conclusion:



## Future:


## Thanks to:
I was heavily inspired by FiveThirtyEight:
https://fivethirtyeight.com/ 

I used this website to quickly visualize binomial distributions:

https://homepage.divms.uiowa.edu/~mbognar/applets/bin.html 

I was inspired by the visualization of this article and plan to build a similar dash app sometime in the future:

https://towardsdatascience.com/developing-a-generalized-elo-rating-system-for-multiplayer-games-b9b495e87802 

https://poker-elo-dashboard.herokuapp.com/ 
