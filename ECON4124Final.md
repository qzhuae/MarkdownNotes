


> Written with [StackEdit](https://stackedit.io/).
# ECON4124 Final Review
## To-Dos

 - [ ] HW1
 - [ ] HW2
 - [ ] HW3
 - [ ] Final Guide
 - [ ] Lecture Note 1
 - [ ] Lecture Note 2
 - [ ] Lecture Note 3
 - [ ] Lecture Note 4
 - [ ] Lecture Note 5
 - [ ] Lecture Note 6
 - [ ] Lecture Note 7
 - [ ] Lecture Note 8
 - [ ] Lecture Note 9

## Lecture 6
- Symmetric Nash Equilibrium (Game of Chicken)
- Pareto Optimal NE (Assurance Game)
	- Pre-play communication

`Strict NE`
A strategy profile is **strict** NE if every player's strategy is a unique best response to the other players' strategies. 
Mixed-strategy NE is not strict; pure-strategy NE may or may not be strict
[Example?] 

Informal Arguments for Unique Strict NE [Eliminate the column player's strategy R based on weak dominance]

`Trembling Hand Perfection`
THP, each player i's strategy is not only a best response to other players' strategy $s_{-i}$, but also best response even when other players deviate from $s_{-i}$ with infinitely small probability. 

Strategy profile $\sigma$ is a THP equilibrium if $\exists$ a sequence of totally mixed strategy profile $\sigma^n \rightarrow \sigma$ such that for all $i$, $u_i(\sigma, \sigma_{-i}^n) \geq  u_i(s_i, \sigma^n_{-i})$ for all $s_i$.

[Ask for course example solution]

[Ask about correction on THP on the course note]

1. If every player has two pure strategies in a game, then THP = Proper.

2. THP gets rid of an NE (Nash equilibrium) with a weakly dominated strategy.

3. But THP does more than getting rid of a weakly dominated strategy.

4. Any NE in which both players are using totally mixed strategies is THP.

`Proper Equilibrium`
- refinement based on THP
- a player is more likely to tremble in directions that are least harmful to him.


Strategy profile $\sigma$ is an $\epsilon-$proper equilibrium iff 
- it is a totally mixed strategy profile
- for any $i$ and pure strategies $s_i$ and $\hat s_i$, 
$u_i(s_i,\sigma_{-i}) > u_i(\hat s_i, \sigma_{-i}) \Rightarrow \sigma_i(s_i) > \sigma_i(\hat s_i)/\epsilon$

$\sigma$ is `proper` equilibrium iff there is a sequence $\sigma_\epsilon$ each $\sigma_\epsilon$ is an $\epsilon-$proper eqm

[Informal Argument for proper equilibrium]

`Subgame` consists of the game tree

[Tutorial Note 5 and 9]

## Some Stuff from Jiang Wenda

possible midterm problems

Sequential, Bayesian 

payoff integral

Information set, principal agent problem


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2MjAxOTY4MywtMTIyNjUzNzYxNywxMj
AzMDAwMjAwLDI4MDcwNzI0NCwxOTMwMzA0NzcsMTE0MzA3NzQz
MiwyNzY1MjUxMTAsMjM5MzkxMzE4LDE4ODMwNjQ5OTMsMjA1ND
Y5MDU3OCwtNjY5ODA3Nzc4XX0=
-->