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

![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/ioanninaSlides/dt_graph.svg)

## STGraph - Implementation

- Implemented in Kotlin;

- <b>Graph data layout</b>
    - based on <b>index-free adjacency</b>;
    - time dimension as first citizen;
    - properties and edges are represented as a <b>linked chain of pointers</b>;
    - properties values bigger than 8 bytes (e.g. strings, geometries) are stored in a dynamic storage (RocksDB).
    - supports spatial operations (e.g., ST_INTERSECTS)

- <b>Time-Series data layout</b>
    - Implemented in AsterixDB BDMS
    - LSM-Tree based data layout
    - Native spatial capabilities.
    - Primary index on time dimension
    - Secondary index on spatial dimension
