

**Title:** ALITA: Generalist Agent Enabling Scalable Agentic Reasoning with Minimal Predefinition and Maximal Self-Evolution

**Authors / Year / Venue:**
Jiahao Qiu et al. / 2025 / arXiv

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Adaptation / Evolution


## 1. The problem 

Most existing generalist agents rely heavily on manually predefined tools, workflows, and handcrafted components. These predefined capabilities limit scalability, creativity, adaptability, and cross-domain generalization because developers cannot anticipate every tool or workflow required for future tasks.


## 2. The core idea 

ALITA proposes a radically different philosophy based on **minimal predefinition** and **maximal self-evolution**. Instead of equipping agents with large collections of handcrafted tools, ALITA starts with only a lightweight web agent and enables the agent to autonomously discover, generate, verify, package, and reuse new capabilities as reusable Model Context Protocols (MCPs), allowing continuous capability expansion.


## 3. How it works

- Uses a lightweight **Manager Agent** to coordinate reasoning and identify capability gaps during task execution.
- Performs **MCP Brainstorming** to determine whether new external tools are required.
- Searches open-source repositories, automatically generates executable scripts, configures isolated environments, and validates generated tools.
- Packages successful tools into reusable **MCPs (Model Context Protocols)** stored in an internal MCP Box.
- Continuously reuses and expands the MCP library, creating a self-reinforcing cycle of capability evolution.


## 4. How they evaluate it

The authors evaluate ALITA on three benchmarks:

- **GAIA** (general-purpose agent benchmark)
- **MathVista**
- **PathVQA**

Headline results:

- **75.15% pass@1** and **87.27% pass@3** on GAIA validation, ranking among the top-performing generalist agents.
- **74.0%** accuracy on MathVista.
- **52.0%** accuracy on PathVQA.
- Outperforms OpenAI Deep Research, OctoTools, AutoAgent, OWL, and A-World despite using significantly fewer predefined tools.
- Additional experiments show that automatically generated MCPs can be reused by other agent frameworks and even improve the performance of smaller language models.


## 5. Why it matters for OUR review

ALITA shifts the focus of self-improving agents from manually engineered tool ecosystems to autonomous capability generation.

Within our framework:

- **Memory:** stores reusable MCPs as persistent external capabilities.
- **Adaptation:** continuously generates, verifies, and updates new MCPs according to task requirements.
- **Evolution:** the MCP library grows over time, enabling continual capability expansion without manual engineering.

Connections to related papers:

- **Voyager (2023):** both accumulate reusable skills, but Voyager stores executable programs for embodied tasks while ALITA stores reusable MCP services for general-purpose reasoning.
- **ASI (2025):** both automatically generate executable capabilities; ASI induces programmatic skills, whereas ALITA creates reusable MCPs with complete execution environments.
- **OpenHands:** both dynamically generate tools during execution, but ALITA further emphasizes long-term reuse through MCP packaging.


## 6. Limitations / open questions

ALITA depends heavily on the coding and reasoning abilities of the underlying LLM. When weaker models are used, performance drops substantially. In addition, dynamically generated MCPs require reliable execution environments and accurate tool generation, which may not always succeed.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

Rather than manually designing thousands of tools, future generalist agents can continuously evolve by autonomously creating, verifying, and reusing reusable MCP capabilities.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **1** | **0** |
