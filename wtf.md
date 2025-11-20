## wtf

- Take a graph, embed id node-wise in a vectorial space (as a text).
- Connect the node embeddings through edges in the original graph.
-> you have a vector graph which you can conduct similarity queries on

- Embed a question, find the most similar node and explore edges w.r.t.:
    - semantic distance:
        - explore just the top-k most similar connected nodes
        - explore all nodes until distance < X
    - semantic + edges:
        - ???