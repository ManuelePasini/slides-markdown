# Architectures and Methods for Digital Twin Platforms

## Introduction to Digital Twins

 - Differences between digital shadow, digital model, Digital Twin (DT)
 - Still a buzzword, but enclosing on a definition...
 - 4 components: phyisical model, virtual model, communication services and the data

:::: {.columns}
::: {.column width="50%"}
![Differences between twins](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/twin_model_shadow.png?raw=true)
:::
::: {.column width="50%"}
![DT components](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt.png?raw=true)
:::
::::

## Introduction to Digital Twins

- While concept of data as a core component is arising..
- ... Still left unconsidered in most research papers.
- ... However, some standard models are emerging
- e.g.: Fei Tao, Univ. of Beijing

:::: {.columns}
::: {.column width="60%"}

 ![5-Dimensional DT (Fei, Tao 2020)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/5dim.png?raw=true)

:::
::: {.column width="40%"}

![Virtual Entity architecture (Fei, Tao, 2020)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/digital_model.png?raw=true)

:::
::::

## A Digital Twin for Precision Agriculture

- Five year ongoing project (also in PNRR - Spoke 9) in precision irrigation of orchards
- Demo available at https://big.csr.unibo.it/projects/smarter/
- Paper submitted to [Computer and Electronics in Agriculture](https://www.sciencedirect.com/journal/computers-and-electronics-in-agriculture) (September 2025).

:::: {.columns}
::: {.column width="60%"}
![Soil moisture distribution within a monitored plant](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd2ndyear/dt_agro.png?raw=true)
:::
::: {.column width="40%"}
![Example of controlling action to the physical entity - applying irrigation](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd2ndyear/action_agro_dt.png?raw=true)
:::
::::



## A Data Platform fostering collaboration between DTs

- Within PNRR Agritech – Spoke 3, a Data Platform fostering collaboration and integration across research projects has been implemented.

- In defining integration policies and standards, several data requirements were identified:

    - <b>Heterogeneous data</b>: covering both structured and unstructured formats, including images.

    - <b>Interconnected data</b>: capturing physical entities together with the IoT networks describing them.

    - <b>Temporal aspects</b>: many datasets display time-series characteristics.

    - <b>Spatial aspects</b>: data are often geo-referenced.

![Excerpt of the Agricolture Data Platform](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/phd2ndyear/agriplatform.png?raw=true)

- **Currently working on its evolution**

## From application-oriented to domain-oriented

- Can we abstract from application-level solutions to domain-level solutions? (e.g. from having a platform to support a DT application, to having a platform to support Agricolture Digital Twins)

<b style="color: blue;">Takeaway from previous phase </b>: a Digital Twin (DT) can be represented through data pipelines that collect, process, and transform data into insights.

**Research question**: given a data pipeline, can we identify the set of data platform services required to support it?

<b>References</b>:

Matteo Francia, Matteo Golfarelli, Manuele Pasini — Towards a Process-Driven Design of Data Platforms. In <b>DOLAP</b>, pp. 28–35, 2024.

Matteo Francia, Matteo Golfarelli, Manuele Pasini — Process-Driven Design of Cloud Data Platforms. <b>Information Systems Journal</b>, Manuscript No. INFOSYS-D-24-00444.

- <b style="color: blue;">But something was missing..</b>

## Modelling Digital Twin Data

- Highly interconnected entities (e.g., a fruit tree and the IoT network describing it) naturally suggest the use of graph DBMSs for efficient storage and querying…
    - ... yet, they cannot cope with the volume of such data
- Time-Series DBMSs efficiently handle large volumes of temporal data...
    - ... but fall short in capturing the complex dynamics of relationships among entities.
- Even the previous Data Platform Design often suggested multiple storage technologies, tailored to the needs of different DTs…
- Yet, no multi-store solution has achieved broad adoption in the literature.

- **What about an hybrid data structure?**

## An Hybryd data structure enabling Digital Twin Data

- Combining the strength of Graph and Time-Series DBMS with a novel, hybrid data structure.

![Graph+TimeSeries Hybrid data model](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/refs/heads/master/slides/images/ioanninaSlides/dt_graph.svg)

- A query workload representative of typical DT applications has been defined.
- The data structure has been implemented in Kotlin and evaluated against state-of-the-art techinques with promising results.
- The paper is curently in writing and to be submitted to [VLDB 2026](https://vldb.org/2026/)

## Other publications

## Other activities

:::: {.columns}
::: {.column width="50%"}

##### Tutoring

- 95631 - MACHINE LEARNING AND DATA MINING - 6 cfu (a.a. 23/24)
- 95631 - MACHINE LEARNING AND DATA MINING - 6 cfu (a.a. 24/25)
- 95631 - MACHINE LEARNING AND DATA MINING - 6 cfu (a.a. 25/26)

##### Summer schools

- 6th ACM Europe Summer School on Data Science, Ioannina (Greece)

##### Conferences

- Project meeting Spoke 3 PNRR Agritech
- EDBT/ICDT 2024 Joint Conference


:::
::: {.column width="50%"}

##### External activities

- Teaching Relational Database, 30 hrs, ITS Olivetti (2023/2024)
- Teaching NoSQL Database, 30 hrs, ITS Olivetti (2024/2025)
- Teaching NoSQL Database, 30 hrs, ITS Olivetti (2025/2026)
- Consultancy on Digitalization in Precision Agriculture, iFarming s.r.l.

##### Bachelor Thesis advisor

- Denis Nikaj (Progettazione e prototipazione di un'applicazione web per l'irrigazione di precisione), March 2024.
- Davide Speziali  (Progettazione e realizzazione di un simulatore per l'irrigazione di precisione), December 2024.
- Federico Capponi (Progettazione e prototipazione di un sistema di irrigazione di precisione), July 2025.

:::
::::