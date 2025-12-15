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
    - Yet many modern data-intensive applications combine both, e.g., IoT systems, Digital Twins, and pervasive computing.

- **What about an hybrid data structure ?**


## STGraph - Conceptualization

- **RQ1** - How can we separate, within a specific domain, temporal graph data from time-series data?
- **RQ2** - Can we then merge both data layouts into the same conceptual storage system and provide hybrid capabilities?

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


:::: {.columns}
::: {.column width="60%"}

- <b>Search algorithm</b>: temporal DFS, temporal validity through constraint tightening:
    - <div>
        isValid(Path(n<sub>i</sub>, …, n<sub>k</sub>)) &iff;
        &#8745;<sub>j=i..k-1</sub> I<sub>e(n<sub>j</sub>,n<sub>j+1</sub>)</sub> &#8800; &#8709;, 
        where I<sub>e</sub> = [t<sub>a</sub>, t<sub>b</sub>[
        </div>

- <b>Querying STGraph</b>:

    - Executed in <b>three steps</b>:
        - <b>Search</b>:
            - <b>Pattern matching</b> through temporal DFS;
            - <b>Path instantiation</b>: if exploring a virtual edge, instantiation its virtual nodes;
            - <b>Path Filtering</b>: add path to solution if satisfies constraints.
        - <b>Temporal properties replacement</b>;
        - <b>Aggregate/Join</b>.
:::
::: {.column width="40%"}

- <b>Instantiating a virtual node</b>:
    - Each virtual edge traversal entails a temporal query to AsterixDB;
    - Output tuples are instantiated as in-memory nodes (dummy ID) and connected within the graph.

- <b>Optimizations</b>
    - Support for join operations through naive <b>nested-Loop</b> join;
    - Support for filter pushdown to AsterixDB;
    - Support for spatial join/filtering operations (e.g., ST_INTERSECTS).
    
:::
::::



## Limitations and Future works

- **As of today**
    - No support for cross time-series operations;
    - Supporting only "long" values as TS measurements;
    - Query to AsterixDB is synchronous (shouldn't be);
    - Limited support for AsterixDB capabilities;


## Collaborations

- <b>Physical level</b>:
    - TS data require different data layout than graph data;
        - LSM-Tree-like (e.g., RocksDB)
        - InfluxDB 3.0 on Parquet.
    - Metadata modelling (ausiliary structures);
    - query formalization and optimization; 

- <b>Analytics</b>:
    - TS operators in Cypher/GQL (Graph analytics);
        - shape/patthern matching;
    - Cross time-series operators:
        - Identify plants/grids with similar drying patterns over the last 24h
    - Graph-TS cross-operators:
        - Correlate graph metrics with time-series trends
           - e.g., landslide monitoring sensor network: correlation between pressure measurements and node degree between nearby sensors
        - Correlate soil drying with temperature (spatial join with ARPAE weather stations)
        
- <b>Multistore</b>:
    - Provide a unified language that transparently distributes the execution plan on different engines