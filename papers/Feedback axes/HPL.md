# Gao2026

**Title:** Solving the Granularity Mismatch: Hierarchical Preference Learning for Long-Horizon LLM Agents (HPL)

**Authors / Year / Venue:**
Heyang Gao, Zexu Sun, Erxue Min, Hengyi Cai, Shuaiqiang Wang, Dawei Yin, Xu Chen / 2026 / ICLR 2026

**Coder (you):**
S3

**Cluster:**
Foundations

**Framework layer(s):**
Adaptation / Evolution


## 1. The problem 

Preference optimization has become an important post-training paradigm for LLM agents, but existing methods suffer from a granularity mismatch. Trajectory-level preference learning provides stable but coarse supervision with poor credit assignment, while step-level preference learning offers fine-grained supervision but is noisy and statistically inefficient for long-horizon tasks.


## 2. The core idea

HPL introduces a hierarchical preference learning framework that combines trajectory-level, step-level, and a novel group-level preference optimization. Instead of treating every action independently, HPL groups semantically related actions into reusable sub-tasks and optimizes them with a dual-layer curriculum that progresses from simple to complex and from easy to difficult preference pairs.


## 3. How it works

- Bootstrap a reference policy through behavior cloning on expert trajectories.
- Generate preference datasets at three granularities: trajectory, action, and action-group.
- Segment expert trajectories into semantically coherent action groups using heuristic, uncertainty-based, or semantic segmentation.
- Construct group-level preference pairs and estimate their rewards with Monte Carlo rollouts.
- Optimize the policy using a combined objective consisting of behavior cloning, trajectory-level DPO, step-level DPO, and group-level DPO, guided by a dual-layer curriculum scheduler.


## 4. How they evaluate it

The authors evaluate HPL on three long-horizon agent benchmarks:

- ALFWorld
- WebShop
- InterCode-SQL

using Qwen2.5-1.5B and Qwen2.5-7B as backbone models.

Headline results:

- HPL consistently outperforms trajectory-level DPO (ETO), step-level DPO (IPR), SFT, and RFT.
- Semantic action grouping achieves the best overall performance.
- The dual-layer curriculum significantly improves learning stability and generalization.
- Ablation studies show that group-level DPO contributes the largest performance gain among all optimization components.


## 5. Why it matters for OUR review

HPL provides a new perspective on learning for long-horizon LLM agents by introducing an intermediate optimization granularity between trajectories and individual actions.

Within our framework:

- **Adaptation:** learns more effective policies by integrating preference signals at multiple granularities.
- **Evolution:** progressively improves policy quality through curriculum learning and hierarchical optimization.

Connections to related papers:

- **ETO (2024):** trajectory-level preference optimization only.
- **IPR (2024):** step-level preference optimization only.
- **iStar (2025):** learns implicit step rewards for credit assignment.
- **HPL (2026):** bridges these approaches by introducing group-level preference learning for semantically meaningful sub-tasks.


## 6. Limitations / open questions 

HPL depends on high-quality action-group segmentation, and semantic segmentation requires powerful external LLMs. The framework also relies on Monte Carlo reward estimation and offline preference datasets, which increase preprocessing cost and may limit scalability.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

HPL resolves the granularity mismatch in long-horizon agent alignment by introducing group-level preference learning and curriculum-guided hierarchical optimization between trajectory-level and step-level supervision.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **0** | **1** | **1** | **0** | **0** |
