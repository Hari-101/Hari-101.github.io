---
title: 'Queries on LLM-based Multi-Agentic System'
date: 2024-10-29
permalink: /posts/2013/08/blog-post-2/
tags:
  - LLM
  - multi-agent
---

Anthropomorphically, its all a single stream of “monologue” for an auto-regressive LLM. We fine-tuned it with Human + Assistant tokens to simulate a “dialogue”. Maybe we need a correspondingly fine-tuned model for better multi-agent systems.

Multi-agent means multiple “different” agents. If they were all the same entity, this would kind of reduce to Self Consistency prompting. What are the possible ways in which we could bring about this differentiation amongst various entities at initialisation? (The differentiation could also stem from the way in which they evolve in the environment.)

1. Start off with different LLM (GPT + Claude + Llama)
   - With similarities across training data, architecture, algorithms, how much of a differentiation will this provide?

2. Same underlying LLM (ex. GPT only)
   1. Separate fine-tuning for each entity
   2. Same fine-tuning but different initial prompt (system prompt?)
      - Persona-type based differentiation
      - Task-based differentiation
      - Mix of i. and ii


Most of the current papers operate at the 2.2 level. What this means is that: lets say we have an LLM p(.|x), then two instances p(.|x1) and p(.|x2) are considered as separate entities/ agents as long as x1 != x2. This could even just be the difference of a single token. 

Ok, lets say we want to transition from a single agent setup to multi-agent setup. So, the hypothesis is that the gains due to division of labor (and its consequences) in humans could carry over to LLM-setting. Multi-agentic LLM setups could be seen as related to decomposition and ensembling prompting strategies. Mixture of Experts is also kind of like multi-agency at the architecture level.

Now that we have many agents, the first concern is overall orchestration. When do you call these separate entities into action?

If you assume that we are operating under the 2.b setup, this tasks translates to the timing of the system prompt swapping ( lets assume a sequential operation). At the end of the day, in the 2.b setup, all you have at the backend is a single LLM (lets say an instruction-tuned chat model) which takes as input a context( a system prompt and sequences of (human, assistant) message pairs) . Agentic frameworks could be decomposed into two parts: 1) LLM API calls 2) Post-processing. So, it all (mostly) boils down to a sequence of LLM API calls and what we need to know is how to automate the “context” filling for each of these calls.

 If you have a well-defined workflow, you could resort to flow engineering, hard-coding the sequence (orchestration) in which the separate agents are called. At a higher level of autonomy, this task of orchestration can also be shifted to an LLM. For example, in the Autogen framework, there is a separate orchestrator agent responsible for this task. It takes as input the conversation history ( What is the best way to feed this conversation history? How to pass this object amongst agents?) till the point and outputs the name of the next agent to take control of the workflow. This is a brittle point in the system since it relies heavily on structured output prediction/ instruction following capabilities of the orchestrator. This is similar to the issues faced during tool calling. Regex, fuzzy word matching can help in making the LLM call stitching more robust.

LangGraph as a framework gives you the low level abstraction to replicate Autogen style framework with it and also further modify/ build on it.

Regarding the conversation history, the basic approach would be to pass the entire conversation history object across all the agents. Even at this level, it becomes important to “sell” a multi-persona interaction to the LLM so that the LLM grasps this and follows along. Entire conversation being passed around could lead to context length limit issues and context pollution. This paves way for customized information between agents.

The data accrued while running a multi-agentic setup could be cleaned ( correct errors) and be used to finetune agents separately leading to more differentiation and possibly better gains ...

# Summary, When we say multi-agent system ...

Imagine questions such as whether multi-agent systems are better than single-agent systems? Or about the assumptions/ defining the setting under which we operate:
1. What exactly classifies as a multi-agent system? How is it different from LLM-compound system?
2. What is the best multi-agentic setup? (Similar to asking which is the best prompting strategy?)
3. Is fine-tuning of the models allowed?
4. Diff base models for each agent or the same model?
5. Who handles the communication/ workflow? Dynamic or hard-coded?
6. Conversation history pre/ post-processing?
7. Multi-persona/ prompt designs?


# Related Reads:
1. [Are multi-LLM-agent systems a thing? Yes they are. But.](https://gist.github.com/yoavg/9142e5d974ab916462e8ec080407365b)
2. [Don't Sleep on Single Agent Systems](https://www.all-hands.dev/blog/dont-sleep-on-single-agent-systems)


