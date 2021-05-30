# Kruszyński Rating

Kruszyński rating is method of calculating player's score based on the outcome of the match and  
relative score of players.

## Introduction

## Qualities

Good rating system should have certain qualities such as:
- **credibility** or fairness gives ability to accurately estimate player skills based on score
- **simplicity**, being able to calculate and understand algorithm make it feels "fair"
- **constant value**, lack of rating inflation let players track their progress throught time
- **quick convergence** to the player true skill
- **flexibility** helps implement system to different types of competetive games
- **predictability**, predicts match outcome correctly

Aditonal factors that could be put under consideration are:
- quality matchmaking
- accurate predictions
- fun (approachable, fell of mystery, status)

Every rating system should follow these three principles:
- rating goes up on wins
- rating goes down on losses
- amount depends on opponent strenght

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
- less depth makes recognizng skills harder

### Interaction

Players should not be both ranked and matchmaked based on the same statistics.
For example if matchmaking system would be fed with K/D ratio, players can't
be ranked based on that statistics, because everyone would end up with the same
K/D ratio.

## Other Rating Systems

### Elo

Elo rating system was created by Arpad Elo for rating chess players.  
If Player A has rating of ![Ra](https://render.githubusercontent.com/render/math?math=%5Clarge%20R_%7BA%7D)
and Player B has rating of ![Rb](https://render.githubusercontent.com/render/math?math=%5Clarge%20R_%7BB%7D)
the formula for expected score of Player A is  
![Ea](https://render.githubusercontent.com/render/math?math=%5Clarge%20E_%7BA%7D%3D%5Cfrac%7B1%7D%7B1%2B10%5E%7B(R_%7BB%7D-R_%7BA%7D)%3A400%7D%7D%0D)  
Similarly the expected score for Player B is  
![Eb](https://render.githubusercontent.com/render/math?math=%5Clarge%20E_%7BB%7D%3D%5Cfrac%7B1%7D%7B1%2B10%5E%7B(R_%7BA%7D-R_%7BB%7D)%3A400%7D%7D%0D)

- inefficient by today's standards
- don't adress all today's needs
- very slow

## Dictionary

Skill System - figure out how good players are
Matchmaking System - puts players togheter into matches
Ranking/Rating System - tells players how good they are