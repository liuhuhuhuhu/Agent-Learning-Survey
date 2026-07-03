# Allard2026.md

Paper ID: Allard2026

Title:
Experiential Reflective Learning for Self-Improving LLM Agents

Authors / Year / Venue:
Marc-Antoine Allard, Arnaud Teinturier, Victor Xing, Gautier Viaud
2026
ICLR 2026 MemAgents Workshop

Coder:
S3

Cluster:
SelfImprove

Framework layer(s):
Memory / Evolution


## 1. The problem 

Current LLM agents usually solve each task independently and fail to accumulate useful experience over time. Existing experiential learning methods often require multiple rollouts, repeated retries, or store all experiences indiscriminately, making them inefficient and difficult to scale in practical deployments. :contentReference[oaicite:1]{index=1}


## 2. The core idea

ERL (Experiential Reflective Learning) enables an agent to improve by reflecting on each completed task only once. Instead of storing entire trajectories, the agent summarizes each experience into a reusable heuristic containing both an explanation of success or failure and a general guideline. When solving a new task, ERL retrieves only the most relevant heuristics and injects them into the prompt to guide future reasoning. :contentReference[oaicite:2]{index=2} :contentReference[oaicite:3]{index=3}


## 3. How it works

- After every task, the agent analyzes its execution trajectory together with the success/failure signal.
- The reflection is converted into a structured heuristic consisting of an analysis and a transferable guideline with explicit trigger conditions and recommended actions.
- All heuristics are stored in a persistent heuristic pool instead of storing raw trajectories.
- For a new task, an LLM retrieves the most relevant heuristics according to task similarity, diversity, and guideline quality.
- The selected heuristics are injected into the system prompt before execution to improve future performance. :contentReference[oaicite:4]{index=4}


## 4. How they evaluate it

The authors evaluate ERL on the Gaia2 benchmark (Search and Execution splits) using a ReAct agent as the baseline and compare it with ExpeL, AutoGuide, and few-shot trajectory prompting.

ERL achieves the best overall success rate (56.1%), outperforming the ReAct baseline by +7.8% and ExpeL by +5.2%. Additional experiments show that:
- heuristic retrieval is more effective than retrieving raw trajectories,
- LLM-based retrieval performs better than embedding retrieval,
- heuristics learned from failures and successes contribute differently depending on the task type. :contentReference[oaicite:5]{index=5} :contentReference[oaicite:6]{index=6}


## 5. Why it matters for OUR review

This paper is an important example of the Evolution Layer because it studies how agents transform past experience into reusable knowledge. Rather than memorizing trajectories, ERL extracts transferable reasoning heuristics, making it closely related to Reflexion, ExpeL, and ReasoningBank. It also demonstrates that selective retrieval of learned experience is critical for continual self-improvement. :contentReference[oaicite:7]{index=7}


## 6. Limitations / open questions 

ERL depends on reliable success/failure feedback and assumes that useful heuristics can be extracted immediately after each task. It does not address long-term heuristic maintenance, conflict resolution between stored heuristics, or memory scaling as the experience pool grows. :contentReference[oaicite:8]{index=8}


## 7. One-sentence takeaway

Instead of remembering every experience, LLM agents improve more effectively by distilling each experience into reusable heuristics and retrieving only the most relevant ones for future tasks.


# Coding flags
memory: 1

learning: 1

reflection: 1

tools: 0

multi_agent: 0
