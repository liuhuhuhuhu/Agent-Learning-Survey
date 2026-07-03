# Paper Summary

**Paper ID:** Ouyang2026

**Title:** *ReasoningBank: Scaling Agent Self-Evolving with Reasoning Memory*

**Authors / Year / Venue:** Siru Ouyang et al. / 2026 / arXiv

**Coder:** Student 3

**Cluster:** SelfImprove

**Framework layer(s):** Memory, Evolution


## 1. The problem 

Current LLM agents usually solve each task independently and fail to learn from accumulated experience. Existing memory systems mainly store raw trajectories or successful workflows, making them difficult to transfer across tasks and unable to benefit from failures. 

## 2. The core idea 

ReasoningBank stores reusable reasoning strategies rather than complete interaction trajectories. After each task, the agent summarizes successful and failed experiences into structured memory items, retrieves relevant memories for future tasks, and continuously updates its memory through an iterative learning loop. The paper further introduces Memory-aware Test-Time Scaling (MaTTS), which uses multiple explorations to produce richer memories instead of simply selecting the best answer. 

## 3. How it works 
* Retrieve the most relevant memory items before solving a new task using embedding-based retrieval.
* Execute the task with retrieved reasoning strategies injected into the system prompt.
* Use an LLM-as-a-Judge to determine whether the trajectory succeeds or fails.
* Distill both successful strategies and failure lessons into structured memory items (title, description, content).
* Continuously consolidate new memory into ReasoningBank and improve future performance; MaTTS further enhances memory quality through parallel self-contrast or sequential self-refinement. 

## 4. How they evaluate it

The authors evaluate ReasoningBank on **WebArena**, **Mind2Web**, and **SWE-Bench Verified** using Gemini-2.5 and Claude-3.7 models. Compared with trajectory memory (Synapse), workflow memory (AWM), and memory-free baselines, ReasoningBank consistently achieves higher task success rates while requiring fewer interaction steps. Adding MaTTS provides further improvements, especially on challenging cross-domain and long-horizon tasks. 

## 5. Why it matters for OUR review

This paper is a key reference for the **Evolution Layer**, particularly the **lesson extraction** component. Instead of storing experiences directly, it converts experience into reusable reasoning knowledge, demonstrating how agents can gradually improve through memory accumulation. It also connects naturally with other self-improvement methods such as Reflexion, ExpeL, and AWM, but differs by explicitly learning from both successes and failures.  

## 6. Limitations / open questions

The framework relies on LLM-generated judgments to identify successful and failed trajectories, which may introduce noisy or incorrect memories. Memory management remains relatively simple, leaving questions about memory pruning, retrieval efficiency, and long-term scalability in persistent agent systems. 

## 7. One-sentence takeaway

ReasoningBank enables self-evolving agents by transforming both successful and failed experiences into reusable reasoning strategies rather than simply storing past interactions.

# Coding flag

| Field           | Value | Reason                                                                                     |
| --------------- | ----- | ------------------------------------------------------------------------------------------ |
| **memory**      | **1** | Core contribution is a structured reasoning memory.                                        |
| **learning**    | **1** | Supports continual/test-time learning through iterative memory updates.                    |
| **reflection**  | **1** | Learns from both successes and failures using LLM-as-a-Judge and self-refinement in MaTTS. |
| **tools**       | **0** | Does not focus on tool learning or skill acquisition.                                      |
| **multi_agent** | **0** | Single-agent framework.                                                                    |


