


> Written with [StackEdit](https://stackedit.io/).
# ECON4124 Final Review
## To-Dos

 - [ ] HW1
 - [ ] HW2
 - [ ] HW3
 - [x] ~~Final Guide~~
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
[Example?] Because of indifference condition, you could have multiple response.

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


> Can you ﬁnd out any belief system (p, 1 − p) that can rationalize L?

(Relationship between strict and proper eqm?)

Strategy profile $\sigma$ is an $\epsilon-$proper equilibrium iff 
- it is a totally mixed strategy profile
- for any $i$ and pure strategies $s_i$ and $\hat s_i$, 
$u_i(s_i,\sigma_{-i}) > u_i(\hat s_i, \sigma_{-i}) \Rightarrow \sigma_i(s_i) > \sigma_i(\hat s_i)/\epsilon$

$\sigma$ is `proper` equilibrium iff there is a sequence $\sigma_\epsilon$ each $\sigma_\epsilon$ is an $\epsilon-$proper eqm

[Informal Argument for proper equilibrium]

`Subgame` consists of the game tree following a singleton information set, provided *the resulting subtree does not cut any information sets*.

Definition: A Nash Equilibrium in the original game is `subgame perfect` if it specifies Nash Equilibrium strategies in every sub-game. 

Theorem: **Given a finite extensive-form game, there exists a sub-game-perfect NE**. 

SPE cannot prevent a strictly dominated strategy from being used. 

~~[Obtain Tutorial Note 5 and 9]~~

Anything condition about when a sub-game can be written into matrix form?

Why is (Stay Out, L) an SPE? Because it is not a sub-game.

`Perfect Bayesian Equilibrium`
a strategy-belief pair $(\sigma, \mu)$ is a PBE iff
- $\sigma$ is sequentially rational, optimal in every information set given \mu
- $\mu$ is derived by Bayes' rule at every information set that is reached with positive probability under $\mu$

`Sequential Equilibrium`

`Consistency` A strategy-belief pair is `consistent` if there exists a sequence of totally mixed strategies $\sigma_n$ and corresponding beliefs $\mu_n$ such that
- $\mu_n$ is derived from Bayes' rule and
- $\lim_{n\rightarrow \infty} (\sigma_n, \mu_n) \rightarrow (\sigma, \mu)$


**Theorem**. For every finite extensive-form game there exists at least one sequential eqm. Also, if sequential eqm then $\sigma$ is subgame-perfect NE.

[There exists one sequential equilibrium, \sigma is subgame-perfect NE]

Sequential equilibrium prevents strictly dominated strategies from being used as threats off the equilibrium path: not sequentially rational for any beliefs.


**Similarity and Differences between SE and THP**
both SE and THP consider a convergent sequence of totally mixed-strategy profiles.

1. In SE, the strategy profile interacts with the belief system via Bayes' rule (by the consistency requirment)
2. In SE, the totally mixed-strategy profiles in the convergent sequence do not need to satisfy the mutual best response condition.
3. In THP, the totally mixed-strategy profiles in the convergent sequence must be an equilibrium in the perturbed game.

What if SE does not work?
- Structural Consistency Requirment
- Extensive-form THP
- Forward Induction, Intuitive Criteria
- Strategic Stability


## Some Stuff from Jiang Wenda

possible midterm problems

Sequential, Bayesian 

payoff integral

Information set, principal agent problem


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MDc0NDg0MjksMTIyMzQ3OTgwNywtMT
gwNzQ0ODQyOSwxNzg2NDA4NTMsMTU4NDE3OTUyMywtMTQ4MTcw
NTAyMiwtNDg2MzQ5MDI5LDE0NzM0MjQ4MzUsLTEwNjM5NTcyNz
MsMTI2MjY4NDA0NywtOTcwMDAwMjgxLDEyMTcyMjM4NTksLTE4
ODk2MTYxNzUsNDgzMDg5MjQ0LC0zNjIwMTk2ODMsLTEyMjY1Mz
c2MTcsMTIwMzAwMDIwMCwyODA3MDcyNDQsMTkzMDMwNDc3LDEx
NDMwNzc0MzJdfQ==
-->