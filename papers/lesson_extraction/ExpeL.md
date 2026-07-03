

**Paper ID:** Zhao2024

**Title:** ExpeL: LLM Agents Are Experiential Learners

**Authors / Year / Venue:**
Andrew Zhao et al.
AAAI 2024

**Coder (you):**
Student 3

**Cluster:**
SelfImprove

**Framework layer(s):**
Evolution


## 1. The problem

Most existing LLM agents solve tasks independently and do not accumulate knowledge across different tasks. Although methods such as Reflexion improve performance through retries on a single task, they cannot retain reusable experience that helps future tasks. :contentReference[oaicite:1]{index=1}


## 2. The core idea 

ExpeL enables an agent to learn from experience without updating model parameters. During training, the agent collects successful and failed trajectories, summarizes them into high-level natural language insights, and stores successful trajectories in memory. During inference, it retrieves relevant past experiences together with the extracted insights to guide decision making on new tasks. :contentReference[oaicite:2]{index=2}


## 3. How it works

- The agent repeatedly interacts with training tasks and stores both successful and failed trajectories in an experience pool.
- It compares successful and failed trajectories to extract general lessons, while also identifying common patterns across multiple successful trajectories.
- The extracted lessons are maintained as editable natural language rules using operations such as **ADD**, **EDIT**, **UPVOTE**, and **DOWNVOTE**.
- Successful trajectories are indexed with vector retrieval so that similar experiences can be recalled for future tasks.
- During evaluation, the agent combines retrieved demonstrations with the extracted insights to solve unseen tasks in a single attempt. :contentReference[oaicite:3]{index=3}


## 4. How they evaluate it

The authors evaluate ExpeL on **HotpotQA**, **ALFWorld**, and **WebShop**, comparing it against Act, ReAct, and Reflexion. Across all three domains, ExpeL consistently achieves higher success rates, demonstrating that combining reusable insights with experience retrieval produces better generalization than either strategy alone. The paper also evaluates transfer learning from HotpotQA to FEVER and shows positive knowledge transfer across tasks. :contentReference[oaicite:4]{index=4}


## 5. Why it matters for OUR review

This paper is an important example of the Evolution layer because it demonstrates how agents can transform task experience into reusable knowledge. Rather than relying only on reflection or long-term memory, ExpeL explicitly extracts transferable lessons and reuses them across tasks. It connects naturally with Reflexion (single-task reflection), AWM (workflow memory), ERL (lesson extraction), and later reasoning-memory methods such as ReasoningBank and Memp. :contentReference[oaicite:5]{index=5}


## 6. Limitations / open questions 

The method currently focuses on text-based environments and assumes that extracted insights remain within the model's context window. As experience grows, scalable retrieval and long-term management of accumulated insights remain open challenges. :contentReference[oaicite:6]{index=6}


## 7. One-sentence takeaway

Instead of updating model parameters, ExpeL teaches an LLM agent to improve over time by extracting reusable lessons from its own experience and recalling them when solving future tasks.


# Coding flags 

memory: 1

learning: 1

reflection: 1

tools: 0

multi_agent: 0
