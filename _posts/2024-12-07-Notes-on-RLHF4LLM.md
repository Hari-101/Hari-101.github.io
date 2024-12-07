---
title: 'MDP Setting in RLHF for LLM'
date: 2024-12-07
permalink: /posts/2024/12/notes-rlhf4llm/
tags:
  - RLHF
  - LLM
  - Notes
---
How could the MDP in the RLHF setting for LLMs look like? Let us look at one of the possibilities here ...

Let the vocabulary be set **V**.  
Let an input query be:

$$
\bar{z}_0 = (z_{-n}, z_{-n+1}, \ldots, z_0)
$$

## Definitions
- **Starting state:**  
  $$ S_0 = \bar{z}_0 $$

- **State at time $t$:**  
  $$ S_t = S_{t-1} \cdot A_t $$  
  where $$\cdot$$ denotes concatenation.

- **Action:**  
  $$ A_t \in V $$

- **Policy/Agent:**  
  The LLM $$\pi$$, where:  
  $$ A_t = \pi(S_t) $$

- **Environment/Transition Function:** 
The environment or transition function is defined as:

$$
P(S_{t+1}, R_{t+1} \mid S_t, A_t) = \begin{cases} 
    S_{t+1} = S_t \cdot A_t, & \text{if } A_t \neq \text{EOS token} \\
    R_{t+1} = 0, & \\
    \\
    S_{t+1} = \phi \text{ (end of rollout)}, & \text{if } A_t = \text{EOS token} \\
    R_{t+1} = \gamma(S_t), &
\end{cases}
$$

where $$\gamma$$ is the learned reward model.

## Structures Observed
Some structural observations that could be possibly exploited for better algorithms:

1. As opposed to a conventional DRL setup (let's say a computer screen as the state, some Atari game) where the dimensionality of the state remains fixed throughout,\
   in the LLM setup, the dimensionality increases by a unit after every action (i.e., if the state is represented by 1 token at t=0, at t=1, it becomes 1 + the selected action in the previous time = 2), and so on, at t=3, 3 etc.

2. The specific nature of the transition function, i.e., the concatenation of $$S_t$$ and $$A_t$$ to produce $$S_{t+1}$$

3. As opposed to some games like chess, the environment has two key characteristics:
   a) deterministic nature
   b) non-adversarial nature

Some observations on this basic setup are:

1. As opposed to a conventional DRL setup (let's say a computer screen as the state, some Atari game) where the dimensionality of the state remains fixed throughout,\
   in the LLM setup, the dimensionality increases by a unit after every action (i.e., if the state is represented by 1 token at t=0, at t=1, it becomes 1 + the selected action in the previous time = 2), and so on, at t=3, 3 etc.

2. The specific nature of the transition function, i.e., the concatenation of $$S_t$$ and $$A_t$$ to produce $$S_{t+1}$$

3. As opposed to some games like chess, the environment has two key characteristics:
   a) deterministic nature
   b) non-adversarial nature



