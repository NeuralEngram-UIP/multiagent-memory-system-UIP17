# 🧠 MultiAgent Ebbinghaus Memory-Based Model

A multi-agent AI system with biologically-inspired memory management based on **Ebbinghaus's Forgetting Curve**.

---

## 📌 Project Overview

This project implements a biologically-inspired multi-agent memory system designed around the principles of human cognitive forgetting and reinforcement. It is based on **Ebbinghaus's Forgetting Curve**, which models how memory retention decreases over time unless actively reinforced.

The system consists of multiple collaborative AI agents that share a structured memory ecosystem. Each agent generates, retrieves, and updates memory entries while a centralized memory store manages persistence and decay. Over time, less frequently accessed information naturally fades, while important and repeatedly reinforced information becomes stronger and more persistent.

A dedicated **decay engine** continuously evaluates memory strength using time-based degradation and reinforcement signals. This ensures that the system does not behave like a static database, but rather like a dynamic cognitive system that evolves based on usage patterns.

The **orchestrator** coordinates communication between agents, ensuring controlled memory sharing, conflict resolution, and efficient routing of contextual information. This enables scalable multi-agent interaction while maintaining memory consistency and relevance.

Overall, the system is designed to simulate realistic memory behavior in AI systems, improving long-term reasoning, reducing noise, and enabling more human-like adaptive intelligence.

---

## 🏗️ Architecture

```
Orchestrator
    ├── Agent 1 ──┐
    ├── Agent 2 ──┼──► Shared Memory Store ──► Decay Engine
    └── Agent N ──┘
```

- **Agents** independently process tasks and generate memory entries.
- All entries flow into a **Shared Memory Store**.
- The **Decay Engine** continuously scores and ages every entry in that store.
- The **Orchestrator** sits above everything, routing requests and resolving conflicts between agents.

---

## 📂 Modules

| Module          | Description                                         |
|-----------------|------------------------------------------------------|
| `agents/`       | Individual agent definitions and roles                |
| `memory/`       | Memory storage schema and retrieval logic              |
| `decay/`        | Ebbinghaus decay function and scoring                   |
| `orchestrator/` | Multi-agent coordination and routing                    |
| `evaluation/`   | Testing, metrics, and evaluation scripts                 |
| `api/`          | REST API layer for external interaction                  |

---

## ⚙️ How It Works

1. **Agent Interaction** — Each agent receives input, processes context, and generates memory entries based on its role and task.
2. **Memory Creation & Storage** — Important information is stored in the shared memory system with metadata such as timestamp, importance score, and usage frequency.
3. **Memory Scoring** — Each memory is assigned a dynamic score based on:
   - Recency of access
   - Frequency of reinforcement
   - Importance level assigned by agents
4. **Decay Process** — The decay engine continuously applies the Ebbinghaus forgetting function to reduce memory strength over time for unused data.
5. **Reinforcement Cycle** — Frequently accessed memories are strengthened, slowing down their decay and increasing their retrieval priority.
6. **Retrieval & Coordination** — The orchestrator ensures agents retrieve the most relevant memories while maintaining consistency across the system.
7. **Optimization Loop** — Over time, the system self-optimizes by retaining only high-value memory entries and discarding low-relevance data.

---

## 🧬 Ebbinghaus Forgetting Curve

The core decay model is inspired by the classical forgetting curve equation:

```
R = e^(-t / S)
```

Where:
- **R** — Memory retention (strength) at a given time
- **t** — Time elapsed since last reinforcement/access
- **S** — Relative memory strength (influenced by importance and reinforcement frequency)

Each reinforcement event increases **S**, flattening the curve and slowing future decay — mimicking how repeated recall strengthens human memory.

---

## 🩺 Application: Alzheimer's Patient Companion

This system can be conceptually used to simulate memory degradation patterns similar to Alzheimer's disease, where memory retention gradually weakens and recall becomes inconsistent over time.

By modeling controlled memory decay, it becomes possible to study how information loss affects decision-making and recall behavior in cognitive systems.

**Key simulation ideas:**
- Gradual reduction in memory retention strength over time
- Increased likelihood of forgetting rarely accessed information
- Fragmented recall where partial or related memories are retrieved instead of complete ones
- Difficulty in forming long-term stable memories without reinforcement

Such models can help in research-oriented studies of memory degradation patterns and in designing systems that remain robust even under constrained or unreliable memory conditions.

---

## 🚀 Getting Started

### Prerequisites
- Python 3.10+
- pip / virtualenv

### Installation
```bash
git clone https://github.com/<your-username>/multiagent-ebbinghaus-memory.git
cd multiagent-ebbinghaus-memory
python -m venv venv
source venv/bin/activate   # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

### Running the System
```bash
python -m orchestrator.main
```

### Running the API
```bash
uvicorn api.main:app --reload
```

---

## 🧪 Evaluation

Run tests and evaluation metrics to observe decay behavior and retrieval accuracy:

```bash
python -m evaluation.run_tests
```

Metrics tracked may include:
- Retention accuracy over time
- Recall precision/recall for reinforced vs. non-reinforced memories
- Decay curve visualization per memory entry

---

## 🗺️ Roadmap

- [ ] Add configurable decay profiles per agent
- [ ] Visualization dashboard for memory strength over time
- [ ] Support for external vector database backends
- [ ] Multi-modal memory (text, image, audio) support
- [ ] Fine-grained conflict resolution strategies in the orchestrator

---

## 🤝 Contributing

Contributions are welcome! Please open an issue to discuss proposed changes before submitting a pull request.

---

## 📄 License

This project is licensed under the MIT License. See the `LICENSE` file for details.

---

## 🙏 Acknowledgements

Inspired by Hermann Ebbinghaus's pioneering research on human memory and forgetting curves, adapted here for multi-agent AI system design.
