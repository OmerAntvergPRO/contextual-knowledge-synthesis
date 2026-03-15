# Adaptive Multi-Agent RAG for Autonomous Literature Synthesis

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

This repository implements a novel framework for autonomous scientific knowledge synthesis. By leveraging multi-agent orchestration and graph-augmented retrieval (G-RAG), the system identifies knowledge gaps across heterogeneous literature sources, synthesizes coherent research summaries, and generates novel hypotheses.

## Overview

Traditional RAG systems often fail in the scientific domain due to the high density of cross-references and the evolution of terminologies. This project addresses these challenges through:

1.  **Graph-Augmented Retrieval:** Integrates citation networks with semantic embeddings to preserve structural context.
2.  **Multi-Agent Refinement:** Employs a 'Critic' agent to audit synthesized summaries for hallucinations and technical accuracy.
3.  **Cross-Domain Mapping:** A specialized component to identify analogies between disparate research fields (e.g., Biology and Information Theory).

## Project Structure

```text
├── src/
│   ├── core/
│   │   ├── knowledge_graph.py   # Construction and traversal of citation graphs
│   │   ├── retrieval.py         # Hybrid search engine (Vector + Graph)
│   │   └── synthesizer.py       # Knowledge fusion logic
│   ├── agents/
│   │   ├── researcher.py        # Primary inquiry agent
│   │   └── critic.py            # Hallucination detection & verification
│   └── utils/
│       └── arxiv_client.py      # ArXiv API wrapper for real-time data
├── notebooks/
│   └── exploratory_synthesis.ipynb
├── tests/
│   └── test_knowledge_graph.py
├── requirements.txt
└── README.md
```

## Getting Started

### Installation

```bash
pip install -r requirements.txt
```

### Usage

Initialize the knowledge synthesis engine:

```python
from src.core.knowledge_graph import KnowledgeGraph
from src.agents.researcher import ResearcherAgent

# Initialize graph with a seed topic
graph = KnowledgeGraph(seed="Quantum Neural Networks")
agent = ResearcherAgent(graph=graph)

# Perform autonomous synthesis
report = agent.synthesize(inquiry="What are the primary bottlenecks in scaling QNNs for NLP?")
print(report)
```

## Methodology

The pipeline uses a specialized "Inquire-Verify-Synthesize" cycle. The **Researcher Agent** retrieves documents and constructs a local subgraph of relevant concepts. The **Critic Agent** then verifies the logical transitions between concepts before the **Synthesizer** generates the final report.

## Future Directions

- Integration with Semantic Scholar API for deeper citation mapping.
- Fine-tuning a domain-specific encoder for technical LaTeX parsing.

## License

Distributed under the MIT License. See `LICENSE` for more information.
