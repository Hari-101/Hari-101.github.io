---
title: 'Notes on RLHF for LLM'
date: 2024-07-12
permalink: /posts/2013/08/blog-post-2/
tags:
  - RLHF
  - category1
---

# RLHF Setting for LLM

Let the vocabulary be set **V**.  
Let an input query be:

\[
\bar{z}_0 = (z_{-n}, z_{-n+1}, \ldots, z_0)
\]

## Definitions
- **Starting state:**  
  \( S_0 = \bar{z}_0 \)

- **State at time \( t \):**  
  \( S_t = S_{t-1} \cdot A_t \),  
  where \( \cdot \) denotes concatenation.

- **Action:**  
  \( A_t \in V \)

- **Policy/Agent:**  
  The LLM \( \pi \), where:  
  \( A_t = \pi(S_t) \)

- **Environment/Transition Function:** 
The environment or transition function is defined as:

\[
P(S_{t+1}, R_{t+1} \mid S_t, A_t) =
\begin{cases} 
    S_{t+1} = S_t \cdot A_t, & \text{if } A_t \neq \text{EOS token} \\
    R_{t+1} = 0, & \\
    \\
    S_{t+1} = \phi \, (\text{end of rollout}), & \text{if } A_t = \text{EOS token} \\
    R_{t+1} = \gamma(S_t), &
\end{cases}
\]

where \( \gamma(S_t) \) is the reward model.



