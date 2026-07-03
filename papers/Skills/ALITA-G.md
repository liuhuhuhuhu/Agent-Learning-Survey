# Qiu2025b

**Title:** ALITA-G: Self-Evolving Generative Agent for Agent Generation

**Authors / Year / Venue:**
Jiahao Qiu, Xuan Qi, Hongru Wang, et al. / 2025 / arXiv

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Adaptation / Evolution

---

## 1. The problem

Most existing self-evolving agents improve only through prompt refinement, reflection, or limited tool updates. They struggle to transform a general-purpose agent into a domain expert that consistently performs well across a family of related tasks.


## 2. The core idea 

ALITA-G introduces a self-evolution framework that automatically transforms a generalist agent into a domain-specialized agent. It repeatedly executes representative domain tasks, extracts reusable MCP tools from successful trajectories, abstracts them into general-purpose primitives, stores them in an MCP Box, and retrieves the most relevant MCPs through RAG during inference.


## 3. How it works 

- A powerful **Master Agent** repeatedly executes representative tasks within a target domain.
- Successful execution trajectories are converted into reusable MCP tools containing executable code, descriptions, and use cases.
- Raw MCPs are abstracted by parameter generalization, context removal, interface standardization, and documentation enhancement.
- All abstracted MCPs are stored in a reusable **MCP Box**.
- During inference, semantic retrieval selects the most relevant MCPs, which are executed by a specialized agent through a CodeAct loop.


## 4. How they evaluate it

The authors evaluate ALITA-G on:

- GAIA
- PathVQA
- Humanity's Last Exam (HLE)

Headline results:

- **83.03% pass@1** and **89.09% pass@3** on GAIA validation, establishing a new state of the art.
- Higher accuracy than the original ALITA agent while reducing average token usage by approximately **15%**.
- Similar improvements are observed on PathVQA and HLE.
- Multiple MCP-generation rounds produce richer MCP Boxes, leading to progressively stronger domain-specialist agents.


## 5. Why it matters for OUR review

ALITA-G extends the idea of self-improving agents from accumulating reusable tools to automatically generating complete domain-specialist agents.

Within our framework:

- **Memory:** introduces the MCP Box as a persistent repository of reusable domain-specific capabilities.
- **Adaptation:** repeatedly generates, abstracts, filters, and retrieves MCPs according to domain tasks.
- **Evolution:** transforms a general-purpose agent into increasingly capable domain specialists through continual MCP accumulation.

Connections to related papers:

- **Voyager (2023):** both accumulate reusable executable capabilities, but Voyager learns skills during embodied exploration, whereas ALITA-G learns reusable MCPs from representative task collections.
- **ASI (2025):** both store executable reusable capabilities; ASI focuses on online program induction during task execution, while ALITA-G performs offline task-driven MCP generation and specialization.
- **ALITA (2025):** ALITA dynamically creates tools online for arbitrary tasks, whereas ALITA-G generates an optimized specialist agent by building a curated MCP Box for an entire task domain.


## 6. Limitations / open questions

ALITA-G requires representative domain task collections to build effective MCP Boxes, making specialization dependent on task coverage. As MCP Boxes grow larger, redundancy increases and performance improvements gradually saturate, suggesting that future work should focus on MCP pruning and continual maintenance.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

ALITA-G enables a general-purpose agent to become a reusable domain specialist by automatically generating, abstracting, retrieving, and accumulating MCP tools from representative task collections.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **1** | **0** |

