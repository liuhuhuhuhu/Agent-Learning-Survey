# Paper ID
BREW2025

# Title
Improving Language Agents through BREW

# Authors / Year / Venue
Shashank Kirtania et al.
2025
arXiv

# Coder
Student 3

# Cluster
SelfImprove (Lesson Extraction)

# Framework layer(s)
Evolution


# 1. The problem 

Current language agents repeatedly solve similar tasks from scratch because they do not accumulate reusable knowledge across episodes. Existing approaches either rely on expensive policy optimization or maintain memories that are difficult to inspect, update, or retrieve effectively.


# 2. The core idea
BREW proposes learning a structured knowledge base directly from an agent's past experiences instead of updating model weights. Rather than storing entire trajectories, it extracts concept-specific behavioral insights, organizes them into modular knowledge documents, and continuously refines them through a reward-guided search process. The resulting knowledge base becomes a persistent memory that improves future task execution.


# 3. How it works 
- Generate task trajectories using an LLM agent and evaluate them with task-specific graders and human-defined behavior rubrics.
- A Reflector Agent extracts reusable concept–insight pairs from successful and failed trajectories.
- Similar concepts are clustered into meta-concepts, and an Integrator Agent builds one knowledge document for each concept.
- The knowledge base is optimized with Expand-and-Gather Monte Carlo Tree Search (EG-MCTS), which searches for the best combination of knowledge documents.
- During future tasks, the agent retrieves relevant concept documents from the knowledge base to guide planning and decision making.


# 4. How they evaluate it

The authors evaluate BREW on three realistic agent benchmarks:

- OSWorld (computer-use agents)
- τ²-Bench (tool-use conversations)
- SpreadsheetBench (spreadsheet manipulation)

Compared with baseline agents and previous memory systems (Cognee and Agent-Mem), BREW improves task success by roughly 10–20%, reduces tool/API calls by 10–15%, and consistently shortens execution trajectories while maintaining similar computational cost.


# 5. Why it matters for OUR review

BREW is a representative Evolution-layer paper because it studies how agents transform experiences into reusable knowledge rather than simply storing past interactions. Unlike earlier work such as Reflexion and ExpeL, BREW introduces a modular concept-level knowledge base together with a principled optimization algorithm (EG-MCTS), making learned experience easier to retrieve, update, and interpret. It connects naturally to papers such as ERL, ReasoningBank, and Memp that also investigate long-term experiential learning.


# 6. Limitations / open questions 

BREW depends on high-quality trajectory generation, grading, and concept extraction; errors in these stages can propagate into the knowledge base. In addition, optimizing the knowledge base through MCTS introduces extra computational overhead during training and has only been validated on a limited set of application domains.


# 7. One-sentence takeaway

BREW enables language agents to continuously improve by transforming past interaction trajectories into an optimized, concept-level knowledge base that can be retrieved and refined over time.


# Coding flags 

memory: 1
learning: 1
reflection: 1
tools: 1
multi_agent: 0
