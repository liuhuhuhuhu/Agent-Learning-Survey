# Lin2026

**Title:** MUSE-Autoskill: Self-Evolving Agents via Skill Creation, Memory, Management, and Evaluation

**Authors / Year / Venue:**
Huawei Lin, Peng Li, Jie Song, Fuxin Jiang, Tieying Zhang / 2026 / arXiv

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Adaptation / Evolution


## 1. The problem 

Existing automatic skill-learning methods typically treat skills as isolated and static artifacts. They focus on skill generation but overlook long-term management, structured memory, systematic evaluation, and continual refinement, limiting skill reuse and sustained agent improvement.


## 2. The core idea

MUSE-Autoskill proposes a unified **skill lifecycle** that manages skills throughout their entire lifespan. Instead of viewing skills as one-off outputs, the framework enables agents to create, store, retrieve, evaluate, refine, merge, and prune skills while maintaining dedicated skill-level memory that accumulates experience across tasks.


## 3. How it works

- Creates new executable skills on demand using a built-in **skill_create** mechanism when existing skills are insufficient.
- Stores reusable skills in a structured **Skill Bank** together with metadata and dedicated skill-level memory.
- Evaluates every newly created skill through unit tests and execution feedback before registration.
- Automatically refines failed skills, merges redundant skills, and prunes obsolete ones to maintain the quality of the Skill Bank.
- Maintains hierarchical memory (short-term, long-term, and skill-level memory) together with adaptive context compression for long-horizon tasks.


## 4. How they evaluate it

The authors evaluate MUSE-Autoskill on **SkillsBench**, a benchmark containing 51 real-world tasks across Science & Engineering, Data Analysis, Document Processing, and Operations & Planning.

Headline results:

- Achieves **68.40%** overall accuracy with human-provided skills, outperforming Codex (67.28%) and Hermes (61.21%).
- Automatically generated skills improve overall performance from **53.19% to 60.35%**.
- On the 35 tasks where skills are successfully generated, Phase-2 accuracy reaches **87.94%**, exceeding the human-skill baseline.
- Generated skills transfer effectively to another agent (Hermes), improving its accuracy by **10.51 percentage points**.
- Generated skills also reduce inference cost by lowering token usage and latency compared with human-written skills.


## 5. Why it matters for OUR review

MUSE-Autoskill extends previous self-improving agent research by treating skills as **long-lived, managed assets** rather than temporary outputs.

Within our framework:

- **Memory:** introduces hierarchical memory with a novel skill-level memory attached to every skill.
- **Adaptation:** supports automatic skill creation, retrieval, evaluation, refinement, merging, and pruning.
- **Evolution:** enables continual capability improvement through lifecycle-managed skills accumulated over time.

Connections to related papers:

- **Voyager (2023):** both maintain growing executable skill libraries, but MUSE formalizes the complete lifecycle of skills.
- **AutoSkill (2024):** extends automatic skill generation with persistent memory and lifecycle management.
- **ALITA (2025):** ALITA focuses on creating reusable MCP capabilities, whereas MUSE focuses on continuously maintaining and evolving executable skills.
- **ALITA-G (2025):** both build reusable capability repositories, but MUSE emphasizes skill lifecycle management instead of domain-specialist agent generation.


## 6. Limitations / open questions

The framework currently depends on successful initial task execution before new skills can be generated, limiting coverage when difficult tasks cannot be solved without prior skills. Some generated skills also contain task-specific assumptions that reduce robustness and generalization beyond the source benchmark.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

Skills should be treated as long-lived, testable, memory-aware assets that are continuously created, evaluated, refined, managed, and reused throughout an agent's lifetime rather than as one-off generated artifacts.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **1** | **0** |

