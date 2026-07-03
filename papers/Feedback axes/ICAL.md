# Sarch2024

**Title:** VLM Agents Generate Their Own Memories: Distilling Experience into Embodied Programs of Thought

**Authors / Year / Venue:**  
Gabriel Sarch, Lawrence Jang, Michael J. Tarr, William W. Cohen, Kenneth Marino, Katerina Fragkiadaki / 2024 / NeurIPS 2024

**Coder (you):**  
S3

**Cluster:**  
Memory

**Framework layer(s):**  
Memory / Adaptation / Evolution


## 1. The problem

Current VLM agents rely heavily on high-quality expert demonstrations or manually designed in-context examples. Raw trajectories collected from humans or imperfect agents are often noisy, inefficient, and difficult to reuse, limiting continual learning and generalization across new environments.


## 2. The core idea 

ICAL (In-Context Abstraction Learning) enables VLM agents to automatically transform noisy demonstrations into reusable **Programs of Thought**. Instead of memorizing raw trajectories, the agent abstracts optimized action sequences together with high-level reasoning—including task decomposition, causal relationships, state changes, and visual abstractions—and stores them as structured multimodal memories. These memories can later be retrieved for in-context learning or used for supervised fine-tuning.


## 3. How it works

- Collect noisy trajectories from humans or suboptimal policies.
- Use a VLM to refine trajectories by correcting actions and generating Programs of Thought, including causal reasoning, state changes, temporal subgoals, and task-relevant abstractions.
- Execute the optimized trajectory with human-in-the-loop feedback, iteratively revising both actions and reasoning until successful.
- Store successful optimized trajectories and their associated reasoning in a growing multimodal memory library.
- Retrieve relevant memories for Retrieval-Augmented Generation or fine-tune the VLM on accumulated memories for future tasks.


## 4. How they evaluate it

The authors evaluate ICAL on three embodied-agent benchmarks:

- **TEACh** (dialogue-based household instruction following)
- **VisualWebArena** (multimodal web navigation)
- **Ego4D** (egocentric action forecasting)

Headline results:

- Achieves new state-of-the-art performance on TEACh.
- Improves GPT-4V performance on VisualWebArena by **1.6×**.
- Fine-tuned Qwen2-VL achieves **2.8×** improvement over the base model.
- Outperforms few-shot GPT-4V on Ego4D while using **639× less in-domain training data** than supervised methods.
- As the memory library grows, ICAL requires **38.8% fewer environment interactions** and **71.6% less human feedback** for learning new examples.


## 5. Why it matters for OUR review

ICAL demonstrates that an agent can continually improve by transforming experience into reusable structured memories rather than storing raw trajectories.

Within our framework:

- **Memory:** stores multimodal Programs of Thought as reusable long-term memories.
- **Adaptation:** retrieves relevant memories during inference or fine-tuning to solve new tasks.
- **Evolution:** the memory library continuously expands, reducing future human supervision and environment interactions while improving learning efficiency.

Connections to related papers:

- **Reflexion:** stores textual reflections after failures, whereas ICAL stores generalized multimodal reasoning.
- **Voyager:** stores executable code skills; ICAL stores reusable reasoning examples.
- **Generative Agents:** focuses on natural-language episodic memories; ICAL focuses on task-oriented embodied memories.
- **Self-RAG:** reflects over retrieved documents, whereas ICAL reflects over interaction trajectories.


## 6. Limitations / open questions 

ICAL depends on human-in-the-loop feedback during memory construction and assumes a fixed action API. Performance is also constrained by the visual grounding capability of the underlying VLM and may degrade when demonstrations or feedback are highly misleading.


## 7. One-sentence takeaway



ICAL enables VLM agents to continually improve by distilling noisy experiences into reusable multimodal Programs of Thought that function as long-term structured memories.


# Coding flags

| memory | learning | reflection | tools | multi_agent |
| **1** | **1** | **1** | **0** | **0** |
