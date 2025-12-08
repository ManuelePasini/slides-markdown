# Data Platforms - Under the hood

<hr style="border: none; border-top: 1px solid #000;">

<div style="text-align:center">
<span style="font-size: larger;"><b>Manuele Pasini</b></span>

*manuele.pasini@unibo.it*

09/12/2025


:::: {.columns}
::: {.column width="20%"}
![](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/big.png?raw=true)
:::
::::

</div>

## Intro

- **Who am I ?** 

    - <b>Manuele Pasini</b>, Ph.D. Candidate in Computer Science and Engineering
    - University of Bologna, [Business Intelligence Group](https://big.csr.unibo.it/)

- **Area of Interest:** 

    - (Almost) the whole data* world.

        - Data engineering (physical level);
        - Data integration;
        - Precision Agriculture:
            - Irrigation management;
            - Data Platform for italian agriculture domain @[Agritech](https://agritechcenter.it/it/).


## A Cloud Data Platform

- Is a *centralized* infrastructre composed of *independent* and *well-integrated* services meeting the *end-to-end* needs of data pipelines:
    - *Centralized*: a data platform is conceptually a single and unified component;
    - *Independent*: changes in a a service do not affect others;
    - *Well-integrated*: services have interfaces enabling a frictionless composition;
    - *End-to-end*: services cover the entire data life cycle.

## A case study - The Agritech PNRR Project

- **Goal**: Build a data platform to foster collaboration and integration between different agriculture research projects.

:::: {.columns}
::: {.column width="25%"}

- In short:
    - 6 research partners;
    - highly heterogeneous data;
    - different goals;

- <b>Main challenges</b>:
    - Data governance;
    - Resource governance;
    - Unforseen events.

:::
::: {.column width="75%"}

![Agritech project](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/datamesh.jpg?raw=true)

:::
::::

## About Governance...

We needed to identify key data aspects!

- Process:
    - Two meetings with each partner;
    - Questionaires;
    - 10 minutes presentation on their project;
    - Clear questions on the type of data managed.

**Goal**: document key data aspects (e.g., 5Vs) and processing requirements for every project stakeholder.

## About Governance...

- Identified key aspects:
    - <b>V</b>ariety: Vector, image, multispectral, and sensor data.
    - <b>V</b>olume: From small sensor sets to large drone missions.
    - <b>V</b>eracity: Managing data quality from non-IT personnel.

- Heterogeneous domain:
    - multidisiplinary projects;
    - non-communicating partners;
    - data collected in standalone excel files;
    - few-to-none common ground for interoperability.

- <b>Project volatility</b>:
    - Analysis goals could evolve through time;
    - data types could vary through time!

## Towards a mesh architecture

:::: {.columns}
::: {.column width="70%"}

- Centralized integration would not be cheap!
    - 1 ETL procedure x stakeholder;
    - hard to enforce data quality;
    - limited scalability (w.r.t. stakeholders)

- <b>Hybrid solution</b>:
    - Centralized storage;
    - adherence to [FIWARE](https://www.fiware.org/) Smart Data Models;
        - JSON descriptor attached to data;
        - Common glossary of terms;
        - geo-properties standardization.
    - **data as a product!**

:::
::: {.column width="30%"}

![FIWARE Agrifood Smart Data Model example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/FIWARE.png?raw=true)

:::
::::

# Agritech conceptual architecture

:::: {.columns}
::: {.column width="70%"}

![Agritech Conceptual Architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/Slide19.jpg?raw=true)

:::
::: {.column width="30%"}

![Agritech functional architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_first.png?raw=true)

:::
::::


# Let's talk deploy!

## On a hardware level

:::: {.columns}
::: {.column width="30%"}

- 12 nodes (and counting...)
    - CPU 20 core w5-2445 @4.6 GHZ
    - 256 GB RAM
    - 12 TB HDD
- 2 GPUs NVIDIA RTX 6000 Ada Generation
- 1 Network File System (3 TB)

:::
::: {.column width="70%"}

![Hardware architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/Slide5.jpg?raw=true)

:::
::::

## On a hardware level


:::: {.columns}
::: {.column width="30%"}

- We don't really want to work on bare metal...
    - Need for <b>fault tolerance</b> mechanisms;
    - Possible dependencies issues;
    - <b> no isolation </b>.
- ... We want to **virtualize**
    - remember the <b>independence</b> constraint.
- **Docker Swarm** !

:::
::: {.column width="70%"}

:::{.fragment}
![Hardware + Docker architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/Slide6.jpg?raw=true)
:::

:::
::::

## A Docker overview

- <b>Docker</b> is a platform for developing, shipping and running isolated application using container based virtualization technology.

:::: {.columns}
::: {.column width="45%"}
- w.r.t. virtual machines (e.g., VMWare):
    - more lightweight;
    - no guest OS;
    - reduced resource consumption;
    - more containers per host;
    - greater portability


:::
::: {.column width="55%"}

![Container vs. Virtual Machines](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/virtualization.jpg?raw=true)


:::
::::

## Docker Swarm

- Swarm mode is an advanced feature for managing a cluster of Docker daemons.

:::: {.columns}
::: {.column width="30%"}

- <b>Characteristics</b>:
    - Integrated Orchestration;
    - Decentralized Management;
    - multi-host networking;
    - load balancing;
    - scaling features;
    - service discovery;
    - rolling updates

:::
::: {.column width="70%"}

![Docker swarm architecture](https://docs.docker.com/engine/swarm/images/swarm-diagram.webp)


:::
::::

## Building a Data Platform

- Platform services as <b>Docker services</b>.
- Logically organized in <b>stacks</b>

:::{.fragment}
![Docker swarm architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/top_view.jpg?raw=true)
:::

- This is the **what**, but... 
- ... Too many things in one-flat schema, we need to add another dimension.


# A perspective change

![Vertical view on BIG Data platform](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/vert_view.jpg?raw=true)

- Now we know the **where**...
- What about the **how** ?

## A functional view

![Functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/func_view.jpg?raw=true)

## test2
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/ortho.png?raw=true)

## test3
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/watering_pipeline.jpg?raw=true)

## test4
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech.jpg?raw=true)

## test5
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_ods.jpg?raw=true)

## test6
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/top_view.jpg?raw=true)

## test7
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/vert_view.jpg?raw=true)
