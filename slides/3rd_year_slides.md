
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

## Prescriptive watering: Data-driven optimization of water consumption in kiwifruit orchards

## STGraph: A Multistore for Spatio-Temporal Property Graphs and Time-Series Data . Under review @ VLDB 2027

:::: {.columns}
::: {.column width="60%"}
- A multistore data structure for large spatio-temporal property graphs
    - Graph data model on top of heterogeneous storage
        - Low-evolving data on Graph storage
        - Highly-dynamic data on Time-Series storage
    - Transparent graph query interface.
:::
::: {.column width="40%"}
![STGraph System Architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/arch.svg?raw=true)
:::
::::

:::: {.columns}
::: {.column width="50%"}
![STGraph Data Model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/datamodel.svg?raw=true)
:::
::: {.column width="50%"}
:::
::::


## STGraph: A Multistore for Spatio-Temporal Property Graphs and Time-Series Data

:::: {.columns}
::: {.column width="50%"}
- <b>Property Graph data model</b>:
    - TS events (nodes) can hold edges and properties
    - Edges built at query time
:::
::: {.column width="50%"}
- <b>Hybrid storage</b>:
    - Dedicated Time-Series streaming ingestion of data
    - Query optimization through filter-pushdown
    - Efficient graph traversal & temporal reasoning
:::
::::

![Querying STGraph](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/example.svg?raw=true){.stretch}

## Anomaly Detection in Complex Sensor Networks

- Complex sensor networks are increasingly common
- Anomaly detection in time-series data is a well-known research field
- **What about anomalies that are cross-time series?**

<div style="display: flex; gap: 1rem; justify-content: center;">

<figure style="width: 48%; margin: 0; text-align: center;">
  <img src="https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g_agro.svg?raw=true"
       style="max-height: none !important; width: 100% !important; height: auto !important;">
  <figcaption><em>An example of cross-time series anomaly</em></figcaption>
</figure>

<figure style="width: 48%; margin: 0; text-align: center;">
  <img src="https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/n2g_er.svg?raw=true"
       style="max-height: none !important; width: 100% !important; height: auto !important;">
  <figcaption><em>An example of cross-time series anomaly</em></figcaption>
</figure>

</div>

## LLM-Assisted Metadata Query Answering on Data Warehouses
