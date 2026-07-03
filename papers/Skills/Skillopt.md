# Yang2026

**Title:** SkillOpt: Executive Strategy for Self-Evolving Agent Skills

**Authors / Year / Venue:**
Yifan Yang, Ziyang Gong, Weiquan Huang, Qihao Yang, et al. / 2026 / arXiv

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Adaptation / Evolution


## 1. The problem

Most existing agent skills are either manually written, generated in one shot, or loosely refined through self-revision. These approaches lack a principled optimization process and often fail to consistently improve skills under execution feedback, making skill evolution unstable and difficult to reproduce. :contentReference[oaicite:0]{index=0}


## 2. The core idea

SkillOpt treats an agent skill as a trainable external artifact rather than static instructions. Inspired by deep learning optimization, it introduces a text-space optimizer that iteratively edits a skill document using execution trajectories, validation gating, bounded textual updates, rejected-edit memory, and epoch-wise meta updates, allowing stable optimization without modifying model weights. :contentReference[oaicite:1]{index=1}


## 3. How it works 

- Executes tasks using the current skill and collects rollout trajectories, including successes, failures, tool calls, and execution traces.
- A separate optimizer model analyzes trajectory minibatches and proposes structured **add / delete / replace** edits to the skill document.
- Candidate edits are ranked under a bounded textual learning-rate budget before being applied.
- Every updated skill is evaluated on a held-out validation split; only skills that improve validation performance are accepted.
- Rejected edits are stored as negative feedback, while epoch-wise slow/meta updates summarize long-term editing patterns for future optimization. :contentReference[oaicite:2]{index=2}


## 4. How they evaluate it

The authors evaluate SkillOpt on:

- SearchQA
- SpreadsheetBench
- OfficeQA
- DocVQA
- LiveMathematicianBench
- ALFWorld

Experiments cover:

- Seven target models (GPT and Qwen families)
- Three execution settings (Direct Chat, Codex, Claude Code)

Headline results:

- Best or tied-best performance on **all 52 evaluated (model, benchmark, harness) combinations**.
- Improves GPT-5.5 by **+23.5 points** over the no-skill baseline in Direct Chat.
- Achieves **+24.8 points** improvement inside Codex and **+19.1 points** inside Claude Code.
- Optimized skills transfer successfully across models, execution harnesses, and related benchmarks without retraining.


## 5. Why it matters for OUR review

SkillOpt reframes skill evolution as a **controlled optimization problem** rather than ad hoc self-refinement.

Within our framework:

- **Adaptation:** learns better procedural knowledge through iterative text-space optimization.
- **Evolution:** continuously refines skills through validation-guided updates and long-term optimization history.

Connections to related papers:

- **Voyager (2023):** Voyager accumulates new skills; SkillOpt instead optimizes an existing skill document.
- **AutoSkill / MUSE-Autoskill:** these focus on creating and managing reusable skills, whereas SkillOpt focuses on improving one domain-specific skill through training-like optimization.
- **GEPA / TextGrad:** optimize prompts; SkillOpt optimizes persistent skill artifacts with explicit validation gates and learning-rate control.

Unlike previous work, SkillOpt introduces optimization concepts analogous to gradient descent—learning rate, validation, rejected updates, and momentum—into skill evolution.


## 6. Limitations / open questions 

SkillOpt optimizes a single domain-specific skill rather than discovering entirely new capabilities or tools. Its performance also depends on sufficient rollout trajectories and a powerful optimizer model, making optimization relatively expensive during the offline training stage.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

Agent skills can be optimized like neural network parameters by treating skill documents as trainable external states and applying stable text-space optimization with validation-guided updates.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **0** | **1** | **1** | **0** | **0** |

