

**Paper ID:** Chen2024

**Title:** AutoManual: Constructing Instruction Manuals by LLM Agents via Interactive Environmental Learning

**Authors / Year / Venue:** Minghao Chen et al. / 2024 / NeurIPS

**Coder (you):** S3

**Cluster:** SelfImprove

**Framework layer(s):** Evolution



## 1. The problem

Current LLM agents usually improve by storing trajectories, reflections, or skills, but these experiences are often fragmented and difficult to transfer across tasks. Existing methods also rely heavily on offline experience extraction, making them less effective when the environment changes.


## 2. The core idea 

AutoManual enables an agent to continuously build its own instruction manual while interacting with an environment. Instead of simply memorizing past experiences, it extracts reusable rules online, organizes them into a structured manual, and uses this manual to guide future planning and decision making. As the agent gains more experience, the manual is continuously updated and refined.


## 3. How it works

- A **Planner** interacts with the environment by generating executable Python code.
- A **Builder** analyzes interaction trajectories and extracts reusable environmental rules.
- A **Consolidator** merges duplicated rules and removes redundant knowledge to keep the manual concise.
- A **Formulator** reorganizes validated rules into a structured Markdown instruction manual.
- During inference, the Planner retrieves the generated manual to guide future tasks.


## 4. How they evaluate it

The authors evaluate AutoManual on **ALFWorld**, **MiniWoB++**, and **WebArena**, comparing it with ReAct, Reflexion, ExpeL, and AdaPlanner. AutoManual achieves state-of-the-art performance across all three benchmarks, reaching **97.4%** success rate on ALFWorld with GPT-4-turbo while requiring only a single human demonstration.


## 5. Why it matters for OUR review

This paper is an important work in the **Evolution** layer because it studies how agents continuously accumulate and organize environmental knowledge instead of only storing isolated experiences. It complements papers such as **ExpeL**, **BREW**, **ERL**, and **ReasoningBank**, showing another way to convert interaction experiences into reusable knowledge for long-term self-improvement.


## 6. Limitations / open questions 

The framework depends on powerful LLMs to generate reliable rules, and the instruction manual is directly inserted into the prompt, which may not scale well as the manual grows. Future work could combine the manual with retrieval-based memory systems for better scalability.


## 7. One-sentence takeaway

Instead of storing isolated experiences, AutoManual continuously transforms interaction experiences into a structured instruction manual that guides future behavior.


## Coding flags

**memory:** 1 · **learning:** 1 · **reflection:** 1 · **tools:** 1 · **multi_agent:** 0
