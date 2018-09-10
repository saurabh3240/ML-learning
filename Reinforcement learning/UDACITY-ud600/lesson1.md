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
    - if $$U(S_0, S_1,S_2, ...) > U(S_0, S_1',S_2', ...)​$$
    - then $$U(S_1,S_2, ...) > U(S_1',S_2', ...)$$