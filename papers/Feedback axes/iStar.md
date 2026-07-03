# Liu2025

**Title:** Agentic Reinforcement Learning with Implicit Step Rewards (iStar)

**Authors / Year / Venue:**
Xiaoqian Liu, Ke Wang, Yuchuan Wu, Fei Huang, Yongbin Li, Junge Zhang, Jianbin Jiao / 2025 / arXiv

**Coder (you):**
S3

**Cluster:**
Foundations

**Framework layer(s):**
Adaptation / Evolution


## 1. The problem 

Training LLM agents with reinforcement learning is challenging because rewards are often sparse, delayed, or even unverifiable in long-horizon interactive environments. Existing process-supervision methods require costly step annotations, rely on noisy reward models, or produce unstable token-level rewards that fail to provide reliable credit assignment.


## 2. The core idea

iStar introduces **Implicit Step Rewards**, which automatically estimate the contribution of each action without requiring explicit step labels. It jointly trains an Implicit Process Reward Model (PRM) and the policy model, using trajectory-level preferences to generate dense step rewards that are combined with episode-level rewards during policy optimization.


## 3. How it works
- The policy model interacts with the environment to collect multi-step trajectories.
- Trajectories are ranked using an outcome reward verifier to construct preferred and rejected trajectory pairs.
- An implicit Process Reward Model (PRM) is trained with a trajectory-based DPO objective to estimate step-level implicit rewards.
- Step-level advantages from implicit rewards are combined with episode-level advantages from outcome rewards for policy optimization.
- The policy and PRM are optimized alternately, creating a self-reinforcing training loop that improves both reward estimation and policy learning.


## 4. How they evaluate it

The authors evaluate iStar on three representative agent benchmarks:

- **WebShop**
- **VisualSokoban**
- **SOTOPIA**

Headline results:

- Achieves state-of-the-art performance on WebShop and VisualSokoban.
- Significantly improves goal completion in SOTOPIA, including open-ended social interactions with unverifiable rewards.
- Improves sample efficiency, training stability, and exploration efficiency compared with GRPO, RLOO, REINFORCE++, PRIME, and GiGPO.
- Demonstrates compatibility with multiple RL algorithms through a plug-and-play credit-assignment mechanism.


## 5. Why it matters for OUR review

iStar addresses one of the central challenges in self-improving agents: **how to assign credit to intermediate actions during long-horizon reinforcement learning**.

Within our framework:

- **Adaptation:** improves policies through dense implicit step rewards instead of relying solely on sparse outcome rewards.
- **Evolution:** alternately optimizes the policy model and the implicit PRM, forming a self-reinforcing improvement loop.

Connections to related papers:

- **PRIME (2025):** both learn implicit reward models, but PRIME predicts token-level rewards, whereas iStar predicts step-level rewards that are more suitable for multi-turn agents.
- **GiGPO (2025):** GiGPO estimates step advantages through same-state grouping, while iStar removes this requirement by learning implicit rewards directly from trajectory preferences.
- **WebAgent-R1 / RAGEN:** iStar can serve as a general credit-assignment module for long-horizon agent RL.
- **Skill-Pro / Voyager:** these works focus on acquiring reusable skills or memories, whereas iStar focuses on optimizing how reinforcement learning updates those skills.


## 6. Limitations / open questions

iStar introduces an additional Process Reward Model that increases training complexity and computational cost. The current framework also separates the PRM and policy model during training, leaving joint optimization and multi-objective reward modeling as future work.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:
Instead of relying only on sparse final rewards, iStar learns implicit step-level rewards from trajectory preferences, enabling more accurate and stable credit assignment for long-horizon LLM agent reinforcement learning.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **0** | **1** | **1** | **0** | **0** |
