


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
 - [x] Lecture Note 6
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

But has no refining power on weakly dominated strategies.

Why P24? belief is 0, 1.

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

## Lecture 7

The essence of the questions of whether, when and how a prisoners' dilemma can be resolved is the difficulty of achieving a cooperative (jointly preferred) outcome through noncooperative(individual) actions.

Solutions:
- Repetition
- Penalties and Rewards
- Leadership
- Asymmetric Information

Finite Repetition

As long as the relationship between the two players in a prisoners' dilemma game lasts a fixed and known length of time, the dominant-strategy *equilibrium with defecting should prevail* in the last period of play.

Infinite Repetition

`Contingent Strategies`
In repeated games of any kind, the sequential nature of the relationship means that players can adopt strategies that *depend on behavior in preceding plays* of the games.

`Trigger Strategies`
A player using a trigger strategy plays cooperatively as long as her rivals do so, but any defection on their part ''triggers'' a period of `punishment`, of specified length, in which she plays non-cooperatively in response.

`Grim Strategy` and `Tit-for-tat` TFT

`Grim Strategy` cooperate until rival defects; and punish on every play for the rest of the game.

`TFT` can solve the prisoners' dilemma without requiring permanent punishment.
choosing the action chosen by your rival in the preceding period of play. When playing TFT, you cooperate with your rival if she cooperated during the most recent play of the game and defect if your rival defected. The punishment phase lasts only as long as your rival continues to defect; you will return to cooperation one period after your rival chooses to do so.

TFT for both players constitutes a NE. Leads to a cooperative outcome

Proving Strategy:
1. Fix one player's strategy
2. Check if it is worthwhile to defect only once
3. Check if it is worthwhile to defect forever

$\frac{1}{1+r} + \frac{1}{(1+r)^2} + \cdots \rightarrow \frac{1}{r}$.

`Folk Theorem for PD`

Let G be a prisoners' Dilemma with D,D as unique NE and C,C be socially desirable outcome

For any discount factor $\delta = \frac{1}{1+r}$, the discounted average payoff of each player i in any NE of the infinitely repeated game of G is at least $u_i(D,D)$.

Let x_1,x_2 be a feasible pair of payoffs in G for which $x_i > u_i(D,D)$ for each player i. There exists $\bar\delta < 1$ such that if the discount factor exceeds $\bar\delta$, then the infinitely repeated game of G has a NE in which the discounted average payoff of each player i is $x_i$. 

For any value of discount factor, the infinitely repeated game of G has a NE in which the discounted average payoff of each player is $u_i(D,D)$.

1. Use SPE instead of NE for PD
2. Replace PD with any two-player game with finitely many actions
3. Replace PD with any multi-player game with finitely many actions and no players' payoff function is same as any other's.

## Lecture 8

**Second-price sealed-bid auction with perfect information**

NEs
- $(v_1, 0, 0, 0, \cdots, 0)$ 
- $(v_2, v_1, 0, 0 \cdots, 0)$
- there is one NE in which player n obtains the object
- $(v_1, v_2, v_3, v_4, \cdots, 0)$ Weakly Dominant Nash Equilibrium

Consider all Nash equilibrium of a second-price sealed-bid auction with two bidders.

**First-price sealed-bid auction with perfect information**

NEs
- $(v_2, v_2, v_3, \cdots, v_n)$
- In all equilibria, the winner is player 1

`Revenue Equivalence`
single Nash Equilibrium in which no player's bid is weakly dominated in a second-price auction yields the same outcome as the distinguished equilibria of a first-price auction.

**Independent private values (IPV)**
Values $v_i \in [v', v'']$ is i.i.d. according to F(v_i) 
Strategies: bidding function $\beta$ maps interval of value to bid
$P(b)$ the price paid by the winner of auction when the profile of bids is b.
Payoffs: Player i's Bernoulli payoff is 0 if her bid b_i is not the highest bid, and $(v_i - P(b))/m$ if no bid is higher than $b_i$ and $m$ bids are equal to $b_i$.

Finding: In second-price auction with perfect information and IPV, a player's bid equal to her valuation weakly dominates all her other bids. Then, there is a NE where each type of every player bids her valuation $\beta_i(v) = v$.

Exercise: Find a NE of a second-price sealed-bid auction in which player i wins regardless of her value. (bid max)

**First-price Auction with IPV**
Observation: the bid of $v_i$ by type $v_i$ of player $i$ weakly dominates any bid greater, but is weakly dominated by any such lower bid.
- If type $v_i$ bids $v_i$, her payoff is certainly 0
- If she bids less than $v_i$, she may win and obtain a positive payoff.

**FPV with IPV, 2 bidders, uniform value distribution over [0,1]**

Most plausible strategy:
- symmetric bidding
- monotonically increasing in $v_i$

Guess $\beta(v) = kv$ where $k \in [0,1]$

[Know the objective function, winning prob. multiply by payoff]



## Some Stuff from Jiang Wenda

possible midterm problems

Sequential, Bayesian 

payoff integral

Information set, principal agent problem


<!--stackedit_data:
eyJoaXN0b3J5IjpbNTU2MTY2MTA3LC01NDE3MTk5NzMsOTEyMz
gzMjY1LC0yMTA0NDA4MDQ4LDI4ODQyMDMxNCwtNDIxMzE4Mjcw
LDc3NzQxMjQwNywtMTgwNzQ0ODQyOSwxMjIzNDc5ODA3LC0xOD
A3NDQ4NDI5LDE3ODY0MDg1MywxNTg0MTc5NTIzLC0xNDgxNzA1
MDIyLC00ODYzNDkwMjksMTQ3MzQyNDgzNSwtMTA2Mzk1NzI3My
wxMjYyNjg0MDQ3LC05NzAwMDAyODEsMTIxNzIyMzg1OSwtMTg4
OTYxNjE3NV19
-->