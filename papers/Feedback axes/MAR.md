# Ozer2026

**Title:** MAR: Multi-Agent Reflexion Improves Reasoning Abilities in LLMs

**Authors / Year / Venue:**
Onat Ozer, Yuchen Wang, Grace Wu, Daniel Dosti, Honghao Zhang, Vivi De La Rue / 2026 / arXiv

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Evolution


## 1. The problem

Reflexion enables LLM agents to improve through verbal self-reflection without updating model parameters, but its single-agent design introduces systematic limitations. Because the same model generates actions, evaluates failures, and produces reflections, it often reinforces its own misconceptions, suffers from confirmation bias, and repeatedly follows the same flawed reasoning path.


## 2. The core idea

MAR (Multi-Agent Reflexion) replaces Reflexion's single self-reflection module with a structured multi-agent debate. Instead of relying on one critic, multiple persona-based critics independently diagnose failures from different perspectives, while a judge model aggregates their critiques into a unified consensus reflection. The resulting reflection is stored in episodic memory and guides future attempts.


## 3. How it works
- The Actor attempts the task using the standard Reflexion pipeline.
- If the attempt fails, multiple critic agents (e.g., Verifier, Skeptic, Logician, Creative) independently analyze the failure.
- Critics debate and revise their diagnoses over one or two rounds.
- A Judge synthesizes all critiques into a single actionable consensus reflection.
- The consensus reflection is stored in episodic memory and injected into the Actor's next attempt.


## 4. How they evaluate it

The authors first reproduce Reflexion on:

- HotPotQA
- HumanEval

They then evaluate MAR on the same benchmarks.

Headline results:

- Improves HotPotQA Exact Match from **44% to 47%** over reproduced Reflexion.
- Improves HumanEval pass@1 from **76.4% to 82.6%**, a **6.2-point gain**.
- Produces more diverse reasoning paths and significantly reduces degeneration-of-thought compared with single-agent Reflexion.
- Demonstrates that structured multi-agent critique yields more effective verbal feedback than self-reflection alone.


## 5. Why it matters for OUR review

MAR extends verbal reinforcement learning by improving the quality of reflection rather than changing the learning algorithm itself.

Within our framework:

- **Memory:** continues to use Reflexion's episodic memory, but stores higher-quality consensus reflections.
- **Evolution:** introduces multi-agent critique and structured debate to improve self-reflection quality over repeated trials.

Connections to related papers:

- **Reflexion (2023):** MAR is a direct multi-agent extension of Reflexion.
- **Self-Refine (2023):** both perform iterative refinement, but MAR introduces multiple specialized critics.
- **Multi-Agent Debate (MAD):** MAR integrates debate into the episodic memory framework rather than using debate only for final answer selection.
- **ICAL (2024):** ICAL improves memory quality through abstraction, whereas MAR improves memory quality through collaborative reflection.

## 6. Limitations / open questions

MAR substantially increases inference cost because each failed attempt triggers multiple critics, debate rounds, and judge synthesis, resulting in roughly three times more API calls than Reflexion. It also depends on carefully designed personas, and determining the optimal number and diversity of critics remains an open research question.


## 7. One-sentence takeaway

Replacing single-agent self-reflection with structured multi-agent debate produces higher-quality verbal feedback, enabling more reliable self-improvement while preserving Reflexion's training-free paradigm.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **0** | **1** | **0** | **1** |
