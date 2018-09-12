#Lesson2: Smoov & Curly's Bogus Journey

## Decision  Making and Reinforcement Learning

- Supervised Learning
  - function approximation  of **f** given **x'**s that new **x** maps to **y**
  - $y = f(x)$ 
- Unsupervised Learning

  - $f(x)$
  - f that gives compact description of **x** 
- Reinforcement Learning

  - $y = f(x) $ given **z**

  - we are given **x**'s and **z**'s we have to learn some **f** that generate **y**'s.

## Markov Decision Processes (MDP)

- **STATES : S**  
  - are set of token every state the agent could be in.
  - position in the grids **(x, y)** coordinates.
- **MODEL : T(s , a , s') ~ Pr(s'|s, a)**
  - transition model/ function, physics of the world, rules that don't change.
  - **T** is function of **s**(current state) **a** action you take and **s'** (next state)
  - function produces probability when you are in state **s** and takes action **a** to go to state **s'**
  - these rules doesn't change over time.
- **ACTIONS: A(s), A**
  - actions/things agent is allowed to do.
  - up, down , left, right
  - note: outcomes here may be different up, down, left, right, stay where you are.
- **REWARD: R(s), R(s, a), R(s, a, s')**
  - a scaler for being in state. /usefulness of being in state.
  - or being in state taking an action
  - or being in state taking an action to get to another state.
- **Notes:**
  - Markovian property: you don't have to condition on anything past the most recent state.
  - only the present matters.
- These four above defines  a MDP

## POLICY : SOLUTION TO MARKOV DECISION PROCESS

- Policy  tell for every state you are in it tells which action to take.
- POLCIY: $$\pi(s) \rightarrow a $$
- $$\pi^{*} $$ policy that optimizes long term expected reward. or at any given point of time.
  - in RL learns by **<s, a, r > <s, a, r>** 
- **plan*** : sequence of actions to take from a particular state. whereas policy is what action should we take to maximize the chance of reward/wining.

## Rewards

- delayed reward
- minor changes matter reward function matters.
- some action can turn out to be good or bad later as the game progresses.
- **Temporal Credit assignment problem**
- maximize expected long term reward
- rewards are like teaching signal and rewards are domain knowledge 
  - often this is like hyperparameter of the model.

## Sequence of Rewards

- **ASSUMPTION**: (Stationarity)
  - **Infinite Horizons**
    - infinite amount of time is considers.
    - if you are in finite horizon case your policies might be change because now it is running out of time.
    - policy might be function of state and function.( not in this case.)
  - **Utility Of Sequence** (stationarity of preference)
    - if $$U(S_0, S_1,S_2, ...) > U(S_0, S_1',S_2', ...)$$
    - then **$$U(S_1,S_2, ...) > U(S_1',S_2', ...)$$**
    - **Mathematically :** $$U(S_0, S_1,S_2, ...) =  \sum_{t=0}^{\infty} R(S_t)$$ ( that does not work in real world)

![](1.png)

- Existential dilemma of being immortal

- **Mathematically :** $$U(S_0, S_1,S_2, ...) =  \sum_{t=0}^{\infty} \gamma^t R(S_t)\   where \  0\leq \gamma < 1 $$

  - discounted series/rewards/sum

  - bounded by   $$\sum_{t=0}^{\infty} \gamma^t R_{MAX} = \frac{R_{max}}{1-\gamma}$$

  - allow us to get infinite distance in finite sum

  - discounted -> geometric

  - infinite -> finite ( after a time $\gamma^t$ becomes v. small thus we can think as finite horizon)

       

## POLICIES

- Optimal policy: is that maximizes long term expected rewards
  - $\pi^* = argmax_{\pi} E[ \sum_{t=0}^{\infty} \gamma^t R(S_t) | \pi]$
- **Utility** of particular state depend on policy we are following
  -  it is expected reward we will get from that state if follow a certain policy
  - $$U^{\pi}(s) = E[ \sum_{t=0}^{\infty} \gamma^t R(S_t) | \pi ,  s_0 =s]$$
  - note $R(s) \neq U^{\pi}(s)$
    - rewards are immediate
    - utility is long term feedback. 
- Optimal policy at a state can be found out by recursive equation as:
  - $\pi^*(s) = argmax_{s}  \sum_{s'} T(s,a,s') U(s')$
  - here author means $$U(s)  =  U^{\pi^*}(s)$$  :always following optimal policy.
- True utility can be defined as:
  - $$U(s) = R(s) + \gamma\  max _{a} \sum_{s'} T(s,a,s') U(s') $$
  - This is known as Bellman equation.
  - fundamental equation in MDP.

## Finding Policies

- suppose we have n states thus we will have n equation  and we don't now U's thus we have h unknown.
- These equations are not linear because of **max** operator.
- Algorithm ( Value iteration):
  - start with random utilities
  - repeat until convergence
    - update utilities based on neighbors ( all of the state it can reach)
    - $$\hat{U}_{t+1}(s) = R(s) + \gamma\  max _{a} \sum_{s'} T(s,a,s') \hat{U_t}(s') $$
- why does it work?
  - because of the term R(s)
  - propagating out true Reward for entering a state  to all sate we can see
  - and propagating it back and forth.
  - at every step we are adding the reality also discounting the wrong moves.  thus it must converge( proof ? )
  - because of $\gamma$ later truth became more prominent than the past arbitrary truth
- Algorithm(policy iteration):
  - start with $\pi_0 \leftarrow guess$
  - **evaluate:** given $\pi_t$ calculate $U_t = U^{\pi_t}$
  - **improve :** 
    - $\pi_{t+1} = argmax_{a} \sum T(s,a,s') U_t(s')$
    - $U_t(s) = R(s) + \gamma \sum T(s, \pi_t(s),s') U(s')$
    - this equation is linear thus it is easy to solve than value iteration.
  - **end**
  - because there are finitely many policy this is guaranteed to converge.
  - it makes jumps in policy space. 
  - roughly O($n^3$)

## Bellman Equation

some Notation difference

Value function / utility function

$$V(s) =max _{a} ( R(s,a) + \gamma\  \sum_{s'} T(s,a,s')V(s') )$$

![](Bellman.png)

lets rewrite the equations as 

![](Bellman2.png)

V(s) - Value equation

Q(s,a)- Quality equation

why new forms of bellman equations

- this will help in the context of Reinforcement learning where we don't know transition and rewards

Third equation of Bellman equations

C(s,a) - continuation equation

![](bellman3.png)

## Bellman Equations Relations

![](Relation.png)



- It turns out **Q function is very powerful** we do not need to know the reward function except for continuation we need transition function not the the reward function.
- If the reward function is hard to represent than q function is really powerful.