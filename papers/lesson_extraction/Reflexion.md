# Shinn2023.md

**Paper ID:** Shinn2023

**Title:** Reflexion: Language Agents with Verbal Reinforcement Learning

**Authors / Year / Venue:** Noah Shinn et al. / 2023 / arXiv (later ICLR workshop)

**Coder (you):** Huhu

**Cluster:** SelfImprove

**Framework layer(s):** Evolution, Memory


## 1. The problem 

Most LLM agents can only improve through prompt engineering or expensive model fine-tuning. Existing reinforcement learning methods require large amounts of training data and parameter updates, making it difficult for language agents to learn efficiently from only a few interactions.


## 2. The core idea

Reflexion introduces a verbal reinforcement learning framework that replaces weight updates with natural language feedback. After each attempt, the agent evaluates its performance, summarizes its mistakes into textual reflections, stores these reflections in long-term memory, and conditions future decisions on these experiences. This enables continual improvement during inference without changing model parameters.


## 3. How it works 

- An **Actor** interacts with the environment and generates actions or responses.
- An **Evaluator** determines whether the attempt succeeds using environment rewards, heuristics, or another LLM.
- A **Self-Reflection model** converts the evaluation signal into natural language lessons describing what went wrong and how to improve.
- These reflections are stored in an episodic memory buffer.
- During the next trial, the Actor reads both the current context and stored reflections before generating a new solution.


## 4. How they evaluate it

The framework is evaluated on three representative agent settings:

- **ALFWorld** for sequential decision making
- **HotPotQA** for multi-hop reasoning
- **HumanEval, MBPP, and LeetcodeHardGym** for code generation

Reflexion consistently improves over strong baselines. It increases ALFWorld success by about **22%**, improves HotPotQA reasoning by around **20%**, and achieves **91% pass@1** on HumanEval, outperforming GPT-4 at the time of publication. :contentReference[oaicite:0]{index=0}


## 5. Why it matters for OUR review

This paper is one of the earliest and most influential works on **self-improving LLM agents**. It introduces the idea that language itself can serve as the optimization signal, replacing gradient updates with verbal reflections.

For our Evolution Layer survey, Reflexion establishes the basic "experience → reflection → memory → improved behavior" loop that later systems such as ReasoningBank, ERL, Memp, AutoManual, and Agent KB further extend. It therefore serves as a foundational reference for lesson extraction and reflective learning.


## 6. Limitations / open questions 
Reflexion depends heavily on the quality of self-generated reflections. If the evaluator or reflection model produces inaccurate feedback, the agent may reinforce incorrect behaviors. In addition, its memory is implemented as a simple sliding window rather than a scalable knowledge management system, limiting long-term accumulation of experience.


## 7. One-sentence takeaway

Reflexion demonstrates that language agents can continuously improve during inference by converting failures into natural language experience instead of updating model weights.


# Coding flags

memory: **1**

learning: **1**

reflection: **1**

tools: **1**

multi_agent: **0**
