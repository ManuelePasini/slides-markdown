
## Introduction

- **Who am I ?** 

    - <b>Manuele Pasini</b>, 3rd year Ph.D. Candidate
    - <b>Supervisor</b>: Matteo Golfarelli, Marco Patella, Davide Maltoni
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

- <b>Digital Twin</b> (DT): physical entity + virtual representation, connected via **bidirectional** data flow
- No universally accepted definition ([Wuni et al](https://www.tandfonline.com/doi/full/10.1080/27525783.2025.2600763).: 358 definitions surveyed)
- <b>Reference architectures</b>:
  - <b>5D model</b> ([Tao et al.](https://www.scopus.com/pages/publications/85064443425)): physical entity, virtual model, connection, data, service
- Scale: Single -  Digital Twins Ecosystems
- **Data is not a by-product** — it's the element connecting every dimension

:::: {.columns}
::: {.column width="50%"}
 ![5-Dimensional DT (Fei, Tao 2020)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/5dim.png?raw=true)
:::
::: {.column width="50%"}
![Digital Twin Data ([Fei, Tao 2023](https://digitaltwin1.org/articles/1-2/v2))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_data.png?raw=true)
:::
::::

## Digital Twin Data & Open Challenges

- DT data is highly **heterogeneous**: structured / unstructured, sensor / simulation / imagery
- Shaped by domain: manufacturing, automotive, agriculture → different needs
- Big-data traits: **volume, variety, velocity** + data **quality/veracity**
- Two complementary challenges:
  - **Standardization** → shared building blocks (DT) / infrastructure & data models (DTE)
  - **Interoperability** → technical, syntactic, semantic, ... levels (Acharya et al.)
- ⇒ Fragmentation is the current bottleneck for Digital Twin **Ecosystems**

---

## A Data-Oriented Perspective

- **Divide et impera**: software and data dimensions are modular, not independent
- Standardization & interoperability, decomposed:
  - software side → increasingly mature
  - **data side → the harder, less mature half** ⇐ focus of this thesis
- **Digital Twin Platform (DTP)**:
  - *is* a software environment, hosting DTs across their lifecycle
  - but organized **around data**, not around DT-specific software
  - agnostic to how a DT is built — if it respects the platform's data models
- Two pillars:
  - **Data Platforms** → infrastructural standardization
  - **Data Models & Governance** → semantic interoperability