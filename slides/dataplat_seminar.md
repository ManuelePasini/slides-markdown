# Data Platforms - A 3D View

<hr style="border: none; border-top: 1px solid #000;">

<div style="text-align:center">
<span style="font-size: larger;"><b>Manuele Pasini</b></span>

*manuele.pasini@unibo.it*

09/12/2025

Slides at: tinyurl.com/dataplatseminar

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

        - Data engineering;
        - Data integration;
        - Precision Agriculture:
            - Irrigation management;
            - Data Platform for italian agriculture domain @[Agritech](https://agritechcenter.it/it/).

## A case study - The Agritech PNRR Project

- **Goal**: Build a data platform to foster collaboration and integration between different agriculture research projects.

:::: {.columns}
::: {.column width="25%"}

- In short:
    - 6 research partners;
    - multidisiplinary projects;
    - different goals;

- Considerations:
    - Requirements might not always be clear;
    - analysis goals could evolve through time!

- <b>Main challenges</b>:
    - Data governance;
    - Resource governance;
    - Unforseen events.

:::
::: {.column width="75%"}

![Agritech project](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_first.svg?raw=true)

:::
::::

## About Governance...

###### Requirement gathering

We needed to identify key data aspects!

- Process:
    - Two meetings with each partner;
    - Questionaire filling;
    - 10 minutes presentation on their project;
    - Clear questions on the type of data managed.

**Desired output**: document key data aspects (5Vs) and processing requirements (e.g., GPUS) for each stakeholder.

## About Governance...

:::: {.columns}
::: {.column width="40%"}

###### Output

- Domain analysis:
    - Project volatility;
    - non-communicating partners;
    - data shattered through different formats;
    - no common ground for interoperability.

- Identified data aspects:
    - **V**ariety: vector, image, multispectral, and sensor data.
    - **V**olume: from small sensor data to large drone missions.
    - **V**eracity: manual collection and sharing.
    - Strong temporal and spatial connotations.


:::
::: {.column width="60%"}


![Agritech project](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_second.svg?raw=true)


:::
::::

## Towards a mesh architecture

:::: {.columns}
::: {.column width="70%"}

- <b>Centralized integration would be a nightmare</b>!
    - 1 ETL procedure x stakeholder;
    - hard to enforce data quality;
    - limited scalability (w.r.t. stakeholders).

- <b>Hybrid solution</b>:
    - Centralized storage;
    - <b>Governance</b> through adherence to [FIWARE](https://www.fiware.org/) Smart Data Models;
        - JSON descriptor attached to data;
        - Common glossary of terms;
        - geo-properties standardization.
    - Stakeholder responsible of quality adherence;
    - **Data as a product!**

:::
::: {.column width="30%"}

![FIWARE Agrifood Smart Data Model example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/FIWARE.png?raw=true)

:::
::::

# Agritech architecture

:::: {.columns}
::: {.column width="60%"}

![Agritech Conceptual Architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_conceptual.svg?raw=true)

:::
::: {.column width="40%"}

![Agritech functional architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_first.png?raw=true)

:::
::::


# Before talking deploy, we have a problem!

*Someting came up, we need to think about a migration first...*
*Slides at: tinyurl.com/dataplatmigration*

# Now let's talk deploy!

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
- **Docker** (or Kubernetes in production environments)!

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
    - greater portability.


:::
::: {.column width="55%"}

![Container vs. Virtual Machines](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/virtualization.jpg?raw=true)

:::
::::

## Docker Swarm

- Swarm mode is an advanced feature for managing a cluster of Docker daemons.

:::: {.columns}
::: {.column width="50%"}

- <b>Characteristics</b>:
    - Integrated Orchestration;
    - multi-host networking;
    - load balancing;
    - scaling features;
    - service discovery;
    - rolling updates.

:::
::: {.column width="50%"}

![Docker swarm architecture](https://docs.docker.com/engine/swarm/images/swarm-diagram.webp)

:::
::::

## Building a Data Platform

- Platform services as <b>Docker services</b>.
- Logically organized in <b>stacks</b>, manageable throguh <b>Portainer</b>.

:::: {.columns}
::: {.column width="50%"}


![Docker swarm architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/top_view.jpg?raw=true)

:::
::: {.column width="50%"}

![Docker stack example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/stack.png?raw=true)

:::
::::




- This is the **what**, but... 
- ... Too many things in one-flat schema, we need to add another dimension.


## A perspective change - Vertical View

![Vertical view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/vert_view.jpg?raw=true)

- Now we know the **where**...
- What about the **how** ?

## Connecting the wires - Functional View

:::: {.columns}
::: {.column width="50%"}

- <b>Processing Module</b>:
    - <b>Platform processes</b>: internal to the platform, used for providing users tools&data (e.g. download SENTINEL-2 images)
    - <b>User processes</b>: specific to a user (e.g. UniPR), black-box to the platform. Interact through APIs.
- <b>Metadata Module</b>: Support governance policies (e.g., FIWARE)
- <b>Storage Module</b>: Heterogeneous and hierarachical set of storage systems (e.g., Hadoop, MongoDB, PostgreSQL)
- <b>APIs Module</b>: defines how users interacts with the platform services.

- **Apache Airflow** as platform quarterback!

:::
::: {.column width="50%"}

![Functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/func_view.jpg?raw=true)

:::
::::

## Let's put things toghether

![Data Platform as a whole](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/ortho.svg?raw=true)

- [A bigger version](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/ortho.png?raw=true)

## SMARTER - Irrigation optimization of fruit orchards 

![Smart Irrigation Data Pipeline](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/watering.svg?raw=true)

## Agritech - A Data Platform for Italian Precision Agriculturew

![Agritech actual functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech.svg?raw=true)

## Agritech - Towards further structure

![Agritech future functional view](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/agritech_ods.svg?raw=true)

# *Thanks!*

Questions?
