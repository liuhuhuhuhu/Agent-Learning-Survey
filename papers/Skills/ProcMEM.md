# Mi2026

**Title:** Skill-Pro: Learning Reusable Skills from Experience via Non-Parametric PPO for LLM Agents

**Authors / Year / Venue:**
Qirui Mi, Zhijian Ma, Mengyue Yang, Haoxuan Li, Yisen Wang, Haifeng Zhang, Jun Wang / 2026 / ICML 2026

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Adaptation / Evolution


## 1. The problem 

Most LLM agents rely on on-the-fly reasoning, repeatedly solving similar problems from scratch even after encountering them many times. Existing memory-based agents mainly store episodic experiences (e.g., trajectories or reflections), which still require expensive reasoning at retrieval time instead of enabling direct procedural execution.


## 2. The core idea 
Skill-Pro proposes replacing episodic memory with reusable procedural memory. Instead of storing interaction histories, it transforms successful experiences into executable Skills consisting of activation conditions, execution procedures, and termination conditions. These skills are continuously refined through a parameter-free optimization framework called **Non-Parametric PPO**, allowing agents to improve without updating LLM weights.

## 3. How it works 

- Formalizes reusable procedural skills using a **Skill-MDP**, where each skill contains activation, execution, and termination conditions.
- Collects interaction trajectories and extracts **semantic gradients** from hindsight analysis instead of parameter gradients.
- Uses **Non-Parametric PPO** with a PPO-style trust-region verification ("PPO Gate") to validate candidate skills before adding them into memory.
- Maintains a compact procedural memory using online scoring, refinement, duplicate removal, and score-based pruning.
- Retrieves procedural skills directly during future decision making, reducing redundant reasoning and improving execution efficiency.


## 4. How they evaluate it

The authors evaluate Skill-Pro on:

- ALFWorld
- TextArena (Mastermind)
- Berkeley Function Calling Leaderboard (BFCL v4)

Headline results:

- Achieves substantially higher skill reuse rates than trajectory-based memory methods.
- Requires only **816 stored tokens**, dramatically reducing memory size while outperforming other memory systems.
- Demonstrates strong in-domain, cross-task, and cross-agent generalization.
- Outperforms ReAct, RAG, Expel, A-MEM, AWM, and G-Memory in both efficiency and task performance.

## 5. Why it matters for OUR review

Skill-Pro represents one of the clearest formulations of **procedural memory** for LLM agents.

Within our framework:

- **Memory:** introduces an explicit procedural memory based on executable Skills rather than episodic trajectories.
- **Adaptation:** continuously improves skills through semantic-gradient optimization and trust-region verification.
- **Evolution:** maintains an evolving skill pool through refinement, online scoring, and pruning.

Connections to related papers:

- **Voyager (2023):** both accumulate executable skills, but Skill-Pro provides a formal Skill-MDP and principled optimization framework.
- **MUSE-Autoskill (2026):** both maintain reusable skill repositories, but MUSE emphasizes lifecycle management, whereas Skill-Pro emphasizes procedural memory and optimization.
- **SkillOpt (2026):** SkillOpt optimizes textual skill documents, while Skill-Pro optimizes executable procedural skills through Non-Parametric PPO.
- **SkillWeaver (2025):** SkillWeaver learns browser APIs, whereas Skill-Pro proposes a general procedural memory architecture applicable across domains

## 6. Limitations / open questions (1–2 sentences)

Skill-Pro assumes that useful procedural knowledge can be represented explicitly as natural-language skills, which may limit applicability to highly dynamic or open-ended environments. Its semantic-gradient optimization also depends on reliable trajectory analysis and multiple candidate evaluations, introducing additional computational overhead.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

Instead of remembering experiences, agents should remember executable procedures, and these procedural skills can be continually optimized through parameter-free semantic updates rather than weight training.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **0** | **0** |
