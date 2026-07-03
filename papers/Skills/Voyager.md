

**Title:** Voyager: An Open-Ended Embodied Agent with Large Language Models

**Authors / Year / Venue:**  
Guanzhi Wang et al. / 2023 / arXiv

**Coder (you):**  
S3

**Cluster:**  
SelfImprove

**Framework layer(s):**  
Memory / Adaptation / Evolution


## 1. The problem 

Most LLM agents can complete isolated tasks but cannot continuously learn over long periods. They lack mechanisms to autonomously explore, accumulate reusable skills, and improve through interaction with the environment, making them unsuitable for lifelong learning in open-ended environments such as Minecraft.


## 2. The core idea 

Voyager turns GPT-4 into a lifelong learning embodied agent by combining three mechanisms: an automatic curriculum that continually proposes achievable new tasks, a growing skill library that stores reusable executable programs, and an iterative prompting loop that improves generated code using environment feedback, execution errors, and self-verification.

Instead of updating model parameters, Voyager continually expands its capabilities by accumulating reusable skills through interaction with the environment.


## 3. How it works
- Uses an **automatic curriculum** to propose progressively more challenging tasks according to the agent's current abilities and exploration progress.
- Stores successful programs as reusable skills in an embedding-based **skill library**, enabling retrieval and composition for future tasks.
- Generates executable code through an **iterative prompting mechanism**, refining programs using environment feedback and execution errors.
- Employs **self-verification** with another GPT-4 instance to determine task success and provide critiques when necessary.
- Adds verified skills into long-term memory, allowing continual accumulation and transfer of knowledge across tasks.


## 4. How they evaluate it

The authors evaluate Voyager in the MineDojo Minecraft benchmark against ReAct, Reflexion, and AutoGPT.

Key results include:

- Discovers **3.3× more unique items** than previous methods.
- Travels **2.3× farther** during exploration.
- Unlocks Minecraft technology tree milestones up to **15.3× faster**.
- Successfully transfers learned skills to new Minecraft worlds and solves unseen tasks through zero-shot generalization.

Ablation studies further demonstrate that the automatic curriculum, skill library, and self-verification are all critical components of the system.


## 5. Why it matters for OUR review

Voyager is one of the earliest and most influential examples of a **self-improving LLM agent** that learns continuously without parameter updates.

Within our framework:

- **Memory:** introduces an executable **skill library** as procedural long-term memory.
- **Adaptation:** improves behavior through environment feedback, execution errors, and self-verification.
- **Evolution:** enables continual accumulation, reuse, and composition of increasingly complex skills.

Connections to related papers:

- **Reflexion (2023):** extends self-reflection by adding persistent skill memory and automatic curriculum generation.
- **Generative Agents (2023):** both employ long-term memory, but Generative Agents store experiences while Voyager stores executable skills.
- **Self-RAG:** both use self-evaluation loops, although Self-RAG critiques retrieved evidence whereas Voyager critiques embodied actions and generated code.


## 6. Limitations / open questions
Voyager relies heavily on GPT-4, making it computationally expensive. It can still hallucinate invalid tasks or incorrect code, and the self-verification module is imperfect. The approach is also evaluated only in Minecraft, leaving its generalization to real-world embodied systems as future work.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:

Lifelong LLM agents emerge from combining automatic curriculum generation, reusable skill memory, and iterative self-improvement rather than continual model fine-tuning.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **1** | **0** |

