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


![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/ioanninaSlides/dt_graph.svg)

:::
::: {.column width="30%"}

- <b>Nodes</b>
    - Graph node <span style="display:inline-block; width:12px; height:12px; border-radius:50%; background:#8eb3c5; border:1px solid #333;"></span> ;
    - Time-Series node <span style="display:inline-block; width:12px; height:12px; border-radius:50%; background:#f39c42; border:1px solid #333;"></span> ;
    
- <b>Edges</b>
    - Graph edge (to a graph node);
    - Virtual edge (to a Time-Series node)

:::
::::


## STGraph - Implementation

- Implemented in <b>Kotlin</b>.

- **Graph data layout**
    - based on <b>index-free adjacency</b> through <i>nodes, edges,</i> and <i>property</i> files.
    - properties and edges are represented as a <b>linked chain of pointers</b>;
        - values > 8 bytes (e.g. strings, geometries) are stored in a dynamic storage (RocksDB);
    - time dimension as first citizen;
    - supports spatial join operations (e.g., ST_INTERSECTS).

- **Time-Series data layout**
    - Implemented in <b>AsterixDB</b> ;
    - LSM-Tree based;
    - Native spatial capabilities;
    - Primary index on time dimension;
    - Secondary index on spatial dimension.

## STGraph - Operations

- <b>Search algorithm</b>: temporal DFS, temporal validity through constraint tightening:
    - <div>Path(n<sub>i</sub>, ..., n<sub>k</sub>) è valido &iff; ⋂<sub>j=i..k-1</sub> I<sub>(n<sub>j</sub>,n<sub>j+1</sub>)</sub> &ne; &empty;</div>

- <b>Join strategy</b>: Nested-Loop;
- <b>>GraphNode-TSNode</b>
    - Each traversal of a virtual edge entails a query to AsterixDB.
    - Filter pushdown
    - <b>No support for cross time-series operations</b>