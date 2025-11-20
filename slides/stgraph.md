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

- Different data layouts imply different ingestion and workload capabilities...

- Yet many modern data-intensive applications combine both, e.g., IoT systems, Digital Twins, and pervasive computing.

- **What about an hybrid data structure ?**


## STGraph - Conceptualization

- Can we separate data by temporal granularity to support hybrid modeling across time-series and temporal graph systems?
- If so, can we embed two different data-layout into the same conceptual storage system and provide hybrid capabilities?

:::: {.columns}
::: {.column width="70%"}


![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/stgraph/STGraph.svg)

:::
::: {.column width="30%"}

- <b>Nodes</b>
    - Graph node <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> ;
    - Time-Series node <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#f39c42; border:2px solid #333;"></span> ;
    
- <b>Edges</b>
    - Graph edge <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> -> <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span>
    - Virtual edge <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#8eb3c5; border:2px solid #333;"></span> -> <span style="display:inline-block; width:16px; height:16px; border-radius:50%; background:#f39c42; border:2px solid #333;"></span>
:::
::::


## STGraph - Implementation

- Implemented in <b>Kotlin</b>.

- **Graph data layout**
    - Based on <b>index-free adjacency</b> through <b>fixed-size records</b> stored in <i>nodes, edges,</i> and <i>property</i> files.
    - Properties and edges are represented as a <b>linked chain of pointers</b>;
        - values > 8 bytes (e.g. strings, geometries) are stored in a dynamic storage (RocksDB);
    - Time dimension as first citizen;

- **Time-Series data layout**
    - Implemented through <b>AsterixDB</b> (LSM-Tree based);
    - Native spatial capabilities;
    - Primary index on time and secondary index on space;
    - Properties and outgoing edges are stored as "fat" graph properties.

## STGraph - Operations

- <b>Search algorithm</b>: temporal DFS, temporal validity through constraint tightening:
    - <div>isValid(Path(n<sub>i</sub>, ..., n<sub>k</sub>)) &iff; ⋂<sub>j=i..k-1</sub> I<sub>e<sub>(n<sub>j</sub>,n<sub>j+1</sub>)</sub></sub> &ne; &empty;, I = validityInterval(n)</div>

- <b>Querying STGraph</b>:
    - Naive <b>nested-Loop</b> join strategy ;
    - <b>Spatial join operations</b> (e.g., ST_INTERSECTS);

    - <b>Traversing a virtual edge</b>:
        - Entails a query to AsterixDB ;
        - Supports filter pushdown ;
        - <b>Query results are materialized as virtual nodes in the graph at query time.</b>

    -<b> Two steps</b>:
        - <b>Graph materialization</b>: retrieve virtual nodes and edges.
        - <b>Query solving</b>.

- **As of today**
    - <b>No support for cross time-series operations</b> .
