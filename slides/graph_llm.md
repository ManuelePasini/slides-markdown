# Graph + LLM state of the art

## Large Language Models on Graphs: A Comprehensive Survey - TDKE, December 2024

Three types of graphs:
    - Pure Graphs without Textual Information
    - Text-Attributed Graphs: nodes or edges are associated with semantically rich text information
    - Text-Paired Graphs: have textual descriptions defined for the entire graph structure.

## Large Language Models on Graphs: A Comprehensive Survey - TDKE, December 2024

** Input graph into LLM **:


- <b>Plainly verbailizing graph</b>: Verbalizing the graph structure in natural language (e.g., describe edges and adjacency lists)
- <b>Paraphrasing graph</b>: paraphrase the graph structure into more natural or concise sentences.

    ```
    [125] find that
    by prompting LLMs to generate a format explanation of the raw graph inputs for itself (Format-Explanation) or to pretend to play a role in a natural task (Role Prompting), the performance on some problems can be improved but not systematically.
    [130] explores the effect of grounding the pure graph in a real-world scenario, such as social networks, friendship graphs, or co-authorship graphs. In such graphs, nodes are described as people, and edges are relationships between people.
    ```

- <b> Encoding Graphs Into Implicit Feature Sequences </b>:  Usually train a graph encoder to encode the graph structure into a
sequence of features and fine-tuning the LLMs to adapt to the new input format.

## Large Language Models on Graphs: A Comprehensive Survey - TDKE, December 2024

** Applications **

- <b>Direct answering</b>: just provide me an answer.
    - On verbalized/paragraphed graphs...
        - LLMs can answer easy questions (e.g., connectivity, neighbor identification, graph size counting) but fail to answer more complex questions (e.g., cycle detection and Hamiltonian pathfinding).
    - On encoded graphs...
        - Drastic performance improvement on problems including substructure counting, maximum triplet sum, shortest path, and bipartite matching.
- <b>Heuristic Reasoning</b>: Perform a series of intermediate reasoning steps that might heuristically lead to the correct answer
    - Reasoning step-by-step: Chain of Thouhg (CoT) like, improves performances on simpler problems (e.g., cycle detection, shortest-path) but fails on complex problems(e.g, hamiltonian PF, topological sorting).
    - Retrieving subgraphs as evidence</b>: when not all graph is relevant to the task, LLM retrieve the subgraphs as evidence first and then perform reasoning on it.
        - Build-a-Graph: encourages LLMs to reconstruct the relevant graph structures and then perform reasoning on them. This
        - Context-Summarization: encourages LLMs to summarize the key nodes, edges, or sub-graphs and perform reasoning.
    - Searching on Graphs</b>: e.g., DFS, BFS.
        - At each step LLM decides if answer the question or explore one node through an edge (good for scaling in graph size)
- <b>Algorithmic Reasoning</b>: prompts the LLMs to recall the algorithms that are relevant to the questions and then perform reasoning step by step according to the algorithms. bad results


** Overall, no consensus on how to represent graphs **