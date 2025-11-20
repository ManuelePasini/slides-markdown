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
::: {.column width="50%"}


![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/ioanninaSlides/dt_graph.svg)

:::
::: {.column width="50%"}

- <b>Nodes</b>
    - Graph node;
    - Time-Series node;
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
    - Implemented in <b>AsterixDB BDMS</b> ;
    - LSM-Tree based data layout ;
    - Native spatial capabilities ;
    - Primary index on time dimension ;
    - Secondary index on spatial dimension .

## STGraph - Operations

- <b>Search algorithm</b>: 
    - Temporal DFS, temporal feasibility check based on constraint tightening:
    -  <div>[t<sub>A</sub><sup>s</sup>, t<sub>A</sub><sup>e</sup>) &cap; [t<sub>B</sub><sup>s</sup>, t<sub>B</sub><sup>e</sup>) &ne; &empty; &iff; 
        max(t<sub>A</sub><sup>s</sup>, t<sub>B</sub><sup>s</sup>) &lt; min(t<sub>A</sub><sup>e</sup>, t<sub>B</sub><sup>e</sup>)</div>
    - <div>
  [t<sub>A</sub><sup>s</sup>, t<sub>A</sub><sup>e</sup>) &cap; [t<sub>B</sub><sup>s</sup>, t<sub>B</sub><sup>e</sup>) &ne; &empty; &iff; max(t<sub>A</sub><sup>s</sup>, t<sub>B</sub><sup>s</sup>) &lt; min(t<sub>A</sub><sup>e</sup>, t<sub>B</sub><sup>e</sup>)
</div>
    - <div>
  I<sub>a</sub> &cap; I<sub>b</sub> &ne; &empty;
</div>


- <b>Join strategy</b>: Nested-Loop;
-  **GraphNode-TSNode**
    - Each time a traversal goes through a virtual edge