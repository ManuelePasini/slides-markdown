
## Introduction

- **Hi!** 

    - <b>Manuele Pasini</b>, 3rd year Ph.D. Candidate
    - <b>Supervisor</b>: Matteo Golfarelli
    - <b>Research interests</b>: 
        - Database / Data Engineering
        - Digital Twins & Precisision Agriculture 
    - <b>Thesis</b>: Architectures and Methods for Digital Twin Platform

:::: {.columns}
::: {.column width="50%"}
![Digital Twin functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt.png?raw=true)
:::
::: {.column width="50%"}
![An example of a generic data platform with its components and layers](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/dataplat.png?raw=true)
:::
::::

## Digital Twins: Concept & State of the Art


:::: {.columns}
::: {.column width="70%"}
- <b>Digital Twin</b> (DT): physical entity (PE) + virtual representation (VE), connected via **bidirectional** data flow
- <b>Reference architectures</b>:
  - 3D model ([M. Grieves](https://link.springer.com/chapter/10.1007/978-3-031-21343-4_4))
  - 5D model ([Tao et al.](https://www.scopus.com/pages/publications/85064443425)): PE, VE, connection, data, service
- **Data is not a by-product** — it's the component connecting every dimension

:::
::: {.column width="30%"}
![[M. Grieves](https://link.springer.com/chapter/10.1007/978-3-031-21343-4_4) 3D Model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt.png?raw=true)
:::
::::


:::: {.columns}
::: {.column width="50%"}
 ![5-Dimensional DT ([Tao et al.](https://www.scopus.com/pages/publications/85064443425))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/5dim.png?raw=true)
:::
::: {.column width="50%"}
![Characterizing Digital Twin data ([Fei, Tao 2023](https://digitaltwin1.org/articles/1-2/v2))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_data.png?raw=true)
:::
::::

## The Challenge: Fragmentation

- Digital Twins adopted across <b>many independent domains</b>:
  - manufacturing, energy, aerospace, healthcare, agriculture, smart cities, transportation...
- No universally accepted definition ([Wuni et al.](https://www.tandfonline.com/doi/full/10.1080/27525783.2025.2600763): 358 definitions surveyed)
- Most application builds its own:
  - architecture and technological stack
  - data representation
- Result: <b>isolated, application-specific Digital Twins </b>
  - data isolation
  - architectural heterogeneity
  - scalability issues

**Fragmentation → limited standardization & interoperability**


## Digital Twin Platform: A Data-Oriented Perspective

- A Digital Twin is a <b>data-intensive application</b>
- **Divide et impera**: separate the <u>software</u> and <u>data</u> dimensions
  - Software dimension → substantial work, increasingly mature
  - Data dimension → far less mature ⇐ <b>focus of my research</b>
- **Standardization should start from data**
- <b>Digital Twin Platform (DTP)</b>:
  - hosts DTs across their lifecycle, but organized around data
  - agnostic to how a DT is implemented — as long as it respects the platform's data models

## SMARTER: Data-driven optimization of water consumption in kiwifruit orchards
<small> Published in [Computers and Electronics in Agriculture](https://www.sciencedirect.com/journal/computers-and-electronics-in-agriculture)</small>

- Two kiwifiruit orchards in Emilia-Romagna
- Data collected from a grid of soil moisture sensors and weather stations
- Soil data is interpolated to obtain a 2-dimensional view of soil moisture

:::: {.columns}
::: {.column width="40%"}

![Grid positioning](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/plant.svg?raw=true)

:::
::: {.column width="60%"}

![From continuous humidity to a discrete representation](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/moisture.png?raw=true)

:::
::::

## SMARTER: Data-driven optimization of water consumption in kiwifruit orchards

:::: {.columns}
::: {.column width="60%"}

- <b> Architecture</b>
    - Data collected and transformed through a Data Platform
    - PID controller + simulation model to determine irrigaton amounts

![An overview of SMARTER](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/smarter.svg?raw=true)

:::
::: {.column width="40%"}
- <b> Results</b>
    - Up to <u>40%</u> in water savings
    - Fruit quality preserved, smaller fruit but of improved quality

![Smarter results](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/smarter_results.svg?raw=true)

:::
::::

## SMARTER: Data-driven optimization of water consumption in kiwifruit orchards

- Beyond the research paper...
    - 13 companies
    - over 30 fields
    - over 60 soil moisture grics
    - 5 years of data collection

:::: {.columns}
::: {.column width="60%"}

- <b> Architecture</b>
    - Data collected and transformed through a Data Platform
    - PID controller + simulation model to determine irrigaton amounts

![SMARTER ER](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/er.png?raw=true)

:::
::: {.column width="40%"}
- <b> Results</b>
    - Up to <u>40%</u> in water savings
    - Fruit quality preserved, smaller fruit but of improved quality

![A more functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/smarter_graph.svg?raw=true)

:::
::::



## STGraph: A Multistore for Temporal Graphs and Time-Series
<small>Currently under review at [53rd International Conference on Very Large Data Bases](https://vldb.org/2027/)</small>

:::: {.columns}
::: {.column width="60%"}

- A multistore solution for large spatio-temporal property graphs 
    - Graph data model on top of heterogeneous storage
        - Low-evolving data on Graph storage
        - Highly-dynamic data on Time-Series storage
    - Transparent graph query interface.

![STGraph Data Model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/datamodel.svg?raw=true)

:::
::: {.column width="40%"}

![STGraph Architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/arch.svg?raw=true)

:::
::::

## STGraph: A Multistore for Temporal Graphs and Time-Series

:::: {.columns}
::: {.column width="50%"}

- <b>Property Graph data model</b>
    - TS events (nodes) can hold edges and properties
    - Edges built at query time

:::
::: {.column width="50%"}

- <b>Hybrid storage</b>
    - Dedicated Time-Series streaming ingestion of data
    - Query optimization through filter-pushdown
    - Efficient graph traversal & temporal reasoning
:::
::::

:::: {.columns}
::: {.column width="60%"}

- <b>Toy Example</b>

![Querying STGraph](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/example.svg?raw=true)

:::
::: {.column width="40%"}

- <b>Results</b>

![Ingestion and query results](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/stgraph_results.svg?raw=true)

:::
::::



## Anomaly Detection in Complex Sensor Networks
<small>Currently under development, in collaboration with Angela Bonifati @ Lyon1</small>
    
:::: {.columns}
::: {.column width="50%"}

- Complex sensor networks are increasingly common (e.g., transportation networks)
- Anomaly detection in single time-series is a well-known research field

:::
::: {.column width="50%"}

- **What about topological anomalies?**
    - Normal behavior taken individually
    - Topological context makes it anomalous

:::
::::

:::: {.columns}
::: {.column width="50%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g_er.svg?raw=true){.medium}

:::
::: {.column width="50%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g_agro.svg?raw=true){.medium}

:::
::::

## Anomaly Detection in Complex Sensor Networks
##### A running example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/1.svg?raw=true){.large}

## Anomaly Detection in Complex Sensor Networks
##### A running example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/2.svg?raw=true){.large}


## Anomaly Detection in Complex Sensor Networks
##### A running example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/3.svg?raw=true){.large}


## Anomaly Detection in Complex Sensor Networks
##### A running example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/4.svg?raw=true){.large}


## Anomaly Detection in Complex Sensor Networks
##### A running example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/5.svg?raw=true){.large}

## Anomaly Detection in Complex Sensor Networks
##### A toy example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)

:::: {.columns}
::: {.column width="33%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/anom_real.svg?raw=true){.medium}

:::
::: {.column width="33%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/anom_top2.svg?raw=true){.medium}

:::
::: {.column width="33%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/anom_top1.svg?raw=true){.medium}

:::
::::

## Anomaly Detection in Complex Sensor Networks
##### A real data example - Series2Graph algorithm from [P. Boniol et al.](https://arxiv.org/abs/2207.12208)


![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g/n2g_real.svg?raw=true){.large}


## LLM-Assisted Metadata Query Answering on Data Warehouses
<small>Published at [28th International Conference on Big Data Analytics and Knowledge Discovery (DAWAK)](https://www.dexa.org/2026/dawak2026.html)</small>