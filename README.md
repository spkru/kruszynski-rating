# Kruszyński Rating

**Szymon P. Kruszyński**  
_May 30, 2021_

Kruszyński rating is method of calculating player's score based on the outcome of the match and  
relative score of players.

## Introduction

The main purpose of rating system is to check and compare skill levels of different players.  
Additional function is to support matchmaking process, thus creating interesting and balanced  
games. The most widely used is Elo ranking system, it's used mainly to compare chess players.  
More recent derivative called Glicko improves Elo rating by incorporating the variability  
in parameter estimates. Although these systems are successfully used in chess they work only  
for two-player game. In video games often there are more than two players or teams competing  
against each other. This creates demand for new more universal rating system.

### Skill Rating

The skill rating of a player is an estimate of their ability to win the next match, based on  
the results of their previous matches. A skill rating system is only as good as its underlying  
assumptions. This paper focuses on making skill ratings more accurate by making better assumptions.

## Design Criteria

Good rating system should have certain properties such as:
- **credibility** or fairness gives ability to accurately estimate player skills based on score
- **simplicity**, being able to calculate and understand algorithm make it feels "fair"
- **constant value**, lack of rating inflation let players track their progress through time
- **quick convergence** to the player true skill
- **flexibility** helps implement system to different types of competitive games
- **predictability**, predicts match outcome correctly

Additonal factors that could be put under consideration are:
- quality matchmaking
- accurate predictions
- fun (approachable, fell of mystery, status)

Every rating system should follow these three principles:
- rating goes up on wins
- rating goes down on losses
- amount depends on opponent strenght

### Online Games

Rating algorithms for online games require to solve additional challenges.  
As authors of this paper[<sup>10</sup>][10] about TrueSkill 2™ rating system pointed out:  
> After consulting with the makers of Gears of War and Halo, we have found  
> that their top priorities are:  
> 1. **Support for team games**. The system should support matches with any number of  
>    teams and any number of players on each team.  
> 2. **Changeable skill ratings**. It must be possible for a player’s skill rating to change,  
>    no matter how many matches they have played in the past. This ensures that players  
>    receive meaningful feedback on their performance.  
> 3. **Compatibility** with an existing matchmaker. Existing matchmakers assume skill is  
>    described by a single number. Players can easily understand a single ordered skill ranking.  
> 4. **Aligned incentives**. The skill rating system should create incentives that align with the  
>    spirit of the game. For example, consider a team game where players cooperate to  
>    achieve a goal. An improperly-designed skill rating system could encourage players  
>    to impede their teammates. As another example, consider a system that increased  
>    skill rating according to the number of times a player healed themselves. This  
>    creates an incentive for a player to repeatedly injure themselves so that they  
>    could be healed. In general, the more control that a player has over a quantity,  
>    the less useful it is for skill rating.  
> 5. **Low computational cost**. Skill updates are done on servers hosted by the game  
>    studio, and skill ratings are stored in a database hosted by the game studio.  
>    This means that skill representations should be small and updates should be cheap.  

## Issues

These are the problems commonly found among rating systems:
- complexity
- cold start
- time decay
- fun factor
- margin of victory
- 50% win ratio
- beyond games
- skill depth
- interaction

### Complexity

- more precise and flexible is more complex
- hard to understant can feel "unfair"
- simplicity goes a long way, Elo is still most widely used system

### Time Decay

- returning players may be out of practice
- TrueSkill and Glick can model time decay by increasing uncertainty (σ)

### Fun Factor

- ranking system can be brutally honest, and most players just want to feel progress
- use ranking system for matchmaking, and accumulative system for progression

### Margin of Victory: Wins vs Points

- most systems count only victories, no individual players contribution and points
- counting game points can improve accuracy, as random factor (bad team) is skipped

### 50% Win Ratio

- good matchmaking system gives player a 50% chance of winning

### Beyond Games

- ranking and rating systems are everywhere: Amazon, Yelp, Google search, etc.
- any item that can be compared can be ranked (i.e. player vs map)

### Skill Depth

- good skill-based matchmaking allows skill depth
- less depth makes recognizing skills harder

### Interaction

Players should not be both ranked and matchmaked based on the same statistics.  
For example if matchmaking system would be fed with K/D ratio, players can't  
be ranked based on that statistics, because everyone would end up with the same  
K/D ratio.

## Other Rating Systems

### Elo

Elo rating system was created by Arpad Elo for rating chess players. Given Player A has  
rating of ![Ra][a] and Player B has rating of ![Rb][b] the formula<sup>20</sup> for expected score of Player A is  
![Ea][c]  
Similarly the expected score for Player B is  
![Eb][d]
- inefficient by today's standards
- don't address all today's needs
- very slow

## Dictionary

Skill System - figure out how good players are  
Matchmaking System - puts players together into matches  
Ranking/Rating System - tells players how good they are

## References

[10] _T. Minka, R. Cleven, Y. Zaykov_  
TrueSkill 2: An improved Bayesian skill rating system  

[20] _Arpad Elo_  
The rating of Chessplayers


[10]: https://www.microsoft.com/en-us/research/uploads/prod/2018/03/trueskill2.pdf
[20]: https://en.wikipedia.org/wiki/Elo_rating_system

[a]: https://render.githubusercontent.com/render/math?math=R_%7BA%7D
[b]: https://render.githubusercontent.com/render/math?math=R_%7BB%7D
[c]: https://render.githubusercontent.com/render/math?math=%5Clarge%20E_%7BA%7D%3D%5Cfrac%7B1%7D%7B1%2B10%5E%7B(R_%7BB%7D-R_%7BA%7D)%3A400%7D%7D%0D
[d]: https://render.githubusercontent.com/render/math?math=%5Clarge%20E_%7BB%7D%3D%5Cfrac%7B1%7D%7B1%2B10%5E%7B(R_%7BA%7D-R_%7BB%7D)%3A400%7D%7D%0D