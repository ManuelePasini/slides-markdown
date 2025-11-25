# STGraph - A spatio-temporal graph for time-series modelling

## STGraph - Overview

- <b>Graph DBMSs</b>
    - Natively built on **index-free adjacency principles**;
    - Optimized for high-performance <i>entity traversal</i>;
    - Efficient on <i>small-volume datasets</i> .
- <b>Time-Series DBMSs</b>
    - Natively built on **Log-Structured Merge Tree** based data structures;
    - Optimized for <i>high-throughput temporal ingestion</i> and efficient management of <i>time-ordered data</i>;
    - Efficient on <i>large-volume datasets</i>.

- Different layouts ➔ different ingestion and workload capabilities...
    -➔ Yet many modern data-intensive applications combine both, e.g., IoT systems, Digital Twins, and pervasive computing.

- **What about an hybrid data structure ?**


## STGraph - Conceptualization

- **RQ1** - How can we separate, within a specific domain, temporal graph data from time-series data?
- **RQ2** - If so, can we embed both data layouts into the same conceptual storage system and provide hybrid capabilities?

:::: {.columns}
::: {.column width="70%"}


![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/stgraph/STGraph.svg)

:::
::: {.column width="30%"}

- <b>Nodes</b>
    - Graph node <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> ;
    - Time-Series node <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#f39c42; border:2px solid #333;"></span> ;
    
- <b>Edges</b>
    - Graph edge   <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> ⟺ <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span>
    - Virtual edge   <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> ⟺ <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#f39c42; border:2px solid #333;"></span>
:::
::::


## STGraph - Implementation

- Implemented in <b>Kotlin</b>.

- **Graph data layout**
    - <b>Index-free adjacency</b> through <b>fixed-size records</b> stored in <i>node, edge,</i> and <i>property</i> files.
    - Properties/edges represented as <b>linked chain of pointers</b>;
        - values > 8 bytes (e.g. strings, geometries) stored in dynamic storage (RocksDB);
    - Time attribute as first citizen;

- **Time-Series data layout**
    - Implemented through <b>AsterixDB</b> (LSM-Tree based);
    - Native spatial capabilities;
    - Primary index on time and secondary index on space;
    - Properties/outgoing edges stored as "fat" graph properties.

## STGraph - Operations

- <b>Search algorithm</b>: temporal DFS, temporal validity through constraint tightening:
    - <div>isValid(Path(n<sub>i</sub>, ..., n<sub>k</sub>)) &iff; ⋂<sub>j=i..k-1</sub> I<sub>e<sub>(n<sub>j</sub>,n<sub>j+1</sub>)</sub></sub> &ne; &empty;, I = validityInterval(n)</div>

- <b>Querying STGraph</b>:

    - Executed in <b>three iterative steps</b>:
        - <b>Path exploration</b> through temporal DFS;
        - <b>Path materialization</b>: if exploring a virtual edge, materialize its virtual nodes;
        - <b>Path filtering</b>.

    - <b>Materializing a virtual node</b>:
        - Each virtual edge traversal entails a temporal query to AsterixDB;
        - Output tuples are materialized as virtual nodes and connected within the graph.

    - <b>Optimizations</b>
        - Naive <b>nested-Loop</b> join strategy;
        - Support for filter pushdown to AsterixDB;
        - Support for spatial join/filtering operations (e.g., ST_INTERSECTS).

## Limitations and Future works

- **As of today**
    - No support for cross time-series operations ;
    - Query to AsterixDB should be asynchronous ;
