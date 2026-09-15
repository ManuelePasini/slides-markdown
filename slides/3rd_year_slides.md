
## Introduction

- **Who am I ?** 

    - <b>Manuele Pasini</b>, 3rd year Ph.D. Candidate
    - <b>Supervisor</b>: Matteo Golfarelli, Marco Patella, Davide Maltoni
    - <b>Research interests</b>: 
        - Database / Data engineering
        - Digital Twins & Precisision Agriculture 
    - <b>Thesis</b>: Architectures and Methods for Digital Twin Platform

:::: {.columns}
::: {.column width="50%"}
![An example of a data pipeline](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd3rdyear/dataplat.png?raw=true)
:::
::: {.column width="50%"}
![Digital Twin functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt.png?raw=true)
:::
::::

## Digital Twins: Concept & State of the Art

- **Definition**: physical entity + virtual representation, connected via **bidirectional** data flow
  - Digital Model → Digital Shadow → Digital Twin (Kritzinger et al.)
- No universally accepted definition (Wuni et al.: 358 definitions surveyed)
- Reference architectures:
  - 3-component model (Grieves) → **5D model**: physical entity, virtual model, connection, data, service (Tao et al.)
- Scale: unit-level → system-level → **System of Systems**
- Data is not a by-product — it's the element connecting *every* dimension

---

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