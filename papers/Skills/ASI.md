

**Title:** Inducing Programmatic Skills for Agentic Tasks

**Authors / Year / Venue:**
Zora Zhiruo Wang, Apurva Gandhi, Graham Neubig, Daniel Fried / 2025 / COLM 2025

**Coder (you):**
S3

**Cluster:**
SelfImprove

**Framework layer(s):**
Memory / Adaptation / Evolution


## 1. The problem 

Most adaptive web agents learn reusable skills by storing textual workflows or instructions in memory. However, these text-based skills cannot be directly executed or verified, making them difficult to reuse reliably and limiting their effectiveness for long-horizon web tasks.


## 2. The core idea

ASI (Agent Skill Induction) represents agent skills as executable programs instead of free-form text. During online interaction, the agent automatically induces reusable programmatic skills from successful trajectories, verifies them through execution, and stores only verified skills into a skill library. These verified skills can later be called as high-level actions to solve similar tasks more efficiently.


## 3. How it works

- The agent first solves a web task using primitive browser actions such as click, fill, and scroll.
- Successful trajectories are converted into reusable Python functions representing higher-level skills.
- Each generated skill is executed on test trajectories for automatic verification.
- Only verified skills are added into the skill library and become callable actions.
- Future tasks retrieve and compose these verified skills instead of repeatedly generating low-level action sequences.


## 4. How they evaluate it

The authors evaluate ASI on the WebArena benchmark against vanilla web agents and Agent Workflow Memory (AWM).

Key findings include:

- 23.5% higher success rate than static agents.
- 11.3% higher success rate than AWM, which stores textual skills.
- 10.7–15.3% fewer interaction steps due to reusable high-level skills.
- Better performance on long-horizon browsing tasks and stronger transfer to unseen real-world websites through online skill adaptation.


## 5. Why it matters for OUR review

ASI demonstrates that the representation of learned skills is critical for self-improving agents.

Within our framework:

- **Memory:** introduces a program-based skill library containing verified executable skills.
- **Adaptation:** continuously induces, verifies, updates, and reuses skills during online interaction.
- **Evolution:** agents gradually accumulate increasingly complex executable skills that improve long-term capability.

Connections to related papers:

- **Voyager (2023):** both store executable skills rather than textual memories, but Voyager focuses on embodied agents in Minecraft whereas ASI targets web navigation.
- **Agent Workflow Memory (AWM):** ASI directly improves upon AWM by replacing textual workflows with verifiable executable programs.
- **Reflexion (2023):** both rely on iterative improvement, but ASI emphasizes executable skill induction instead of verbal reflection.


## 6. Limitations / open questions 

The induced skills are often website-specific and may become incompatible when interfaces change. Although ASI can adapt online by updating skills, its effectiveness still depends on accurate verification and repeated interaction with the environment.


## 7. One-sentence takeaway

If a reader remembers only one thing about this paper, it should be:
Representing learned skills as verified executable programs, rather than text, substantially improves the reliability, efficiency, and continual adaptation of web agents.



# Coding flags

| memory | learning | reflection | tools | multi_agent |

| **1** | **1** | **1** | **1** | **0** |
