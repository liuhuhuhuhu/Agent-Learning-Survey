# Wang2024

**Title:** Agent Workflow Memory (AWM)

**Authors / Year / Venue:** Zora Zhiruo Wang, Jiayuan Mao, Daniel Fried, Graham Neubig / 2024 / arXiv

**Coder:** S3

**Cluster:** SelfImprove

**Framework layer(s):** Evolution, Memory


## 1. The problem

Current LLM agents solve each task independently and rarely reuse successful procedures from previous experiences. As a result, they struggle with long-horizon tasks and cannot continuously improve over time by accumulating reusable knowledge.


## 2. The core idea

The paper introduces Agent Workflow Memory (AWM), which extracts reusable workflows from successful task trajectories and stores them as memory. Instead of retrieving complete demonstrations, AWM summarizes common subroutines into generalized workflows that can be reused across future tasks. The workflow memory is continuously expanded as the agent gains more experience.


## 3. How it works

- Execute tasks and collect complete action trajectories.
- Evaluate whether a trajectory successfully solves the task.
- Use an LLM to summarize reusable subroutines into abstract workflows instead of storing full demonstrations.
- Store workflows in agent memory and retrieve them to guide future reasoning.
- Continuously update workflow memory in both offline (training examples) and online (streaming tasks) settings.


## 4. How they evaluate it

The authors evaluate AWM on two web-agent benchmarks: **WebArena** and **Mind2Web**.

Results show that AWM improves the success rate by **51.1% (relative)** on WebArena and **24.6% (relative)** on Mind2Web compared with strong baselines. It also generalizes well across unseen tasks, websites, and domains while requiring fewer interaction steps.


## 5. Why it matters for OUR review

This paper provides an important mechanism for the **Evolution Layer** by showing how agents can continuously accumulate reusable procedural knowledge. Unlike retrieval methods that reuse entire examples, AWM extracts reusable workflows that become long-term skills. It connects naturally with papers such as **ReasoningBank**, **ERL**, and **Memp**, which also focus on experience accumulation and continual agent improvement.


## 6. Limitations / open questions

The quality of workflow memory depends on the correctness of generated trajectories and the workflow induction process. The approach is mainly validated on web navigation tasks, leaving its effectiveness on broader reasoning or tool-use domains as an open question.



## 7. One-sentence takeaway

Instead of memorizing complete demonstrations, agents should continuously extract and reuse abstract workflows that become reusable procedural knowledge.


## Coding flags

memory: 1 · learning: 1 · reflection: 0 · tools: 1 · multi_agent: 0
