# Fantasy Football Manager Rating

## Inspiration:
I’ve noticed, in my years of competing in fantasy football, that the same handful of managers tend to be at the top of the league every year. Although luck certainly plays its part in the outcomes of matchups, in my observation, success in fantasy football is highly correlated with the skill on the manager. And the US agrees with this observation; fantasy football has been legal in the country due to skill component even when sports betting was overwhelmingly illegal. The equation I came up with attempts to mitigate one specific factor of luck in fantasy football by weighing both performance vs opponent and performance vs median score of the league participants in that week. Opponent performance is something a manager has no control over, so taking performance vs median into account is a crucial part of my equation. It would be difficult to argue that a manager who consistently scores below the median and takes advantage of an easy schedule is somehow better than a manager that consistently scores above the median and is burdened with tough matchups. As for the importance of performance vs opponent, I have another example. Take, for instance, a manager who knows they are projected to lose their matchup. This manager will likely start a more volatile option who has the potential to “boom” than a consistent option who doesn’t have a “boom” in their range of outcomes. Additionally, the ultimate goal for a manager is to win their matchup, so this must be a point of emphasis in the model.

## Challenges:
I collected and inputted all the data for this project manually into excel, which proved to be time-consuming. Additionally, I had to manually change each formula to calculate the correct Elo based on each matchup, which required a large amount of patience and attention to detail. I believe I could make the collection and calculation process much easier with more experience with python and  working with API’s. I hope to rebuild this project in a more efficient way in the future.

## Equations:
Elo vs opponent:
![](readme_images/vprime.PNG)

Elo vs median:
![](readme_images/mprime.PNG)

Manager Rating:
![](readme_images/mrr.png.png)

The original equation that I started with equally weighs Elo for the performance vs opponent and performance vs median (above), so the formula was just the basic average of the two ratings(α=0.5). I decided to write the equation in a more general form with α being the determining factor for the weight. I believe the optimal α will be between 0.15 and 0.35, which would mean performance vs median is much more indicative of success than performance vs opponent.  

Mean Regression Rate:
![](readme_images/mrr.PNG)

In this equation, β is a value between 0 and 1 that regresses each rating to the mean at the beginning of each season. I got this idea from FiveThirtyEight’s NFL game predictions.

https://fivethirtyeight.com/methodology/how-our-nfl-predictions-work/

The NFL model has a mean regression rate of 1/3, fantasy football is much more volatile because each team is completely wiped out each after each season. Thus, I believe the optimal β value will be somewhere between 0.5 and .75.

## Results:

 
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
