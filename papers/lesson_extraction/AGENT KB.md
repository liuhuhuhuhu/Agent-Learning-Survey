# Paper ID
Tang2025

# Title
AGENT KB: Leveraging Cross-Domain Experience for Agentic Problem Solving

# Authors / Year / Venue
Xiangru Tang et al. / 2025 / arXiv

# Coder
S3

# Cluster
Memory

# Framework layer(s)
Memory / Evolution

## 1. The problem

Current agent memory systems are largely framework-specific, preventing experiences learned by one agent framework from being reused by others. As a result, agents repeatedly solve similar problems independently instead of benefiting from collective experience. :contentReference[oaicite:1]{index=1}

## 2. The core idea

The paper introduces AGENT KB, a plug-and-play knowledge base that allows heterogeneous agent frameworks to share experiences without retraining. Instead of storing raw execution traces, AGENT KB converts trajectories into structured experience representations that can be retrieved and adapted during future tasks. A two-stage Reason–Retrieve–Refine pipeline and a disagreement gate ensure that retrieved knowledge improves planning while avoiding harmful interference. :contentReference[oaicite:2]{index=2}

## 3. How it works

- Agent trajectories from different frameworks are abstracted into standardized experience representations.
- Experiences are stored in a shared knowledge base that continuously evolves through addition, deduplication, ranking, and eviction.
- During planning, the system retrieves relevant experiences to generate an initial execution plan.
- During execution, another retrieval stage uses failure feedback to refine the plan.
- A disagreement gate filters retrieved experiences to prevent incompatible knowledge from degrading reasoning. :contentReference[oaicite:3]{index=3}


## 4. How they evaluate it

The authors evaluate AGENT KB on GAIA, Humanity's Last Exam (Bio/Chem), GPQA, and SWE-bench using multiple agent frameworks, including smolagents, OpenHands, OWL, and SWE-Agent. Across nearly all benchmarks, AGENT KB consistently improves task performance without requiring retraining. For example, GPT-4.1-based smolagents improve from 55.2% to 73.9% on GAIA (pass@3), while OpenHands improves from 24.3% to 45.7% on SWE-bench Lite. :contentReference[oaicite:4]{index=4}


## 5. Why it matters for OUR review

This paper is important because it extends agent memory beyond individual systems and introduces a shared experience infrastructure for lifelong agent improvement. Unlike previous work that focuses on self-reflection within a single agent, AGENT KB enables experience transfer across heterogeneous frameworks, making it highly relevant to both the Memory Layer and the Evolution Layer of our survey. It also complements papers such as Reflexion, ExpeL, and ReasoningBank by emphasizing reusable collective knowledge rather than individual reasoning traces. :contentReference[oaicite:5]{index=5}


## 6. Limitations / open questions 

The effectiveness of AGENT KB depends on the quality of automatically extracted experiences and the retrieval mechanism. Although the paper proposes conflict resolution and memory eviction, it does not fully address long-term memory organization, knowledge conflicts, or experience quality control at very large scales. :contentReference[oaicite:6]{index=6}


## 7. One-sentence takeaway

A shared, evolving knowledge base allows different agent frameworks to accumulate and reuse collective experience, enabling continual improvement without retraining.



# Coding flags

memory: 1

learning: 1

reflection: 0

tools: 1

multi_agent: 0
