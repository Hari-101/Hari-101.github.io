---
title: 'Solving all of World Problems with LLM(Click-Bait?)'
date: 2024-10-28
permalink: /posts/2024/10/solving-world-problems-llm/
tags:
  - cool posts
  - category1
  - category2
---

TLDR: Generate all possible string using a python program, evaluate each one using an LLM-Evaluator. But do we have a good enough verifier? Also pruning the search space with the LLM.

Related: Infinite Monkey Theorem, Automated Theorem Proving (1960s), Levins Universal Search(1973), Program Synthesis by enumeration

For example, our problem at hand could be: How to tackle global warming?

1) Lets assume we have an LLM-as-a-Judge/ Evaluator.
Assumption: Our LLM evaluator is "good"/ "reasonable". ( Define?)
The context length is \\(n\\) and vocabulary is set \\(V\\). Let \\(|V| = v\\). We shall keep the initial \\(m\\) tokens for the instruction and the proposed solution.\
Possible Prompt:\
'''{Expert Prompting?}. Your task is to evaluate the proposed idea for the given problem.\
Here is the problem: {problem}\
Here is the proposed solution: {solution}'''\
The rest \\((N-m)\\) tokens can be used to generate the evaluation response.\
2) Now write a python program to generate all the \\(v^m\\) strings /permutations of the tokens ( Let length of instruction << length of proposed solution). Also assume \\((n-m) << n\\). This just means we want to allott the majority chunk of the context for the proposed solution. (We want a well detailed solution!)\
3) Pass each of the to the LLM evaluator! There you have it, a solution to your problem.

ASSUMPTIONS:
1) The desired solutions are expressible using our natural language. ( Limit is the expressivity of the language itself.) It wont generate new symbols/ token? ( Think integral sign)
2) The solution can be expressed in \\(m\\) tokens.
3) Our LLM-evaluator is good!


