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


## A Cloud Data Platform

- Is a *centralized* infrastructre composed of *independent* and *well-integrated* services meeting the *end-to-end* needs of data pipelines:
    - *Centralized*: a data platform is conceptually a single and unified component;
    - *Independent*: changes in a a service do not affect others;
    - *Well-integrated*: services have interfaces enabling a frictionless composition;
    - *End-to-end*: services cover the entire data life cycle.

## A case study - The Agritech PNRR Project

- **Goal**: Build a data platform to Foster collaboration and integration between different agriculture research projects.

:::: {.columns}
::: {.column width="20%"}

- Context:
    - 6 Research partners;
    - Heterogeneous data;
    - <b>Governance issues</b>;
    - <b>Integration issues</b>.


:::
::: {.column width="80%"}

![Agritech project](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/datamesh.jpg?raw=true)

:::
::::


## On a hardware level

:::: {.columns}
::: {.column width="30%"}

- 12 Nodes (and counting...)
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
    - Might face dependencies issues;
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

- Differences between containers and virtual machines...

:::: {.columns}
::: {.column width="45%"}

| **Containers**                                | **Virtual Machines**                             |
|-----------------------------------------------|---------------------------------------------------|
| Share host operating system kernel        | Each VM includes a full guest operating system    |
| Fast startup                              | Slower startup                                    |
| Logical isolation                              | Strong isolation via hypervisor                   |
| Easy scalability                     | More complex to scale                             |
| High workload density                          | Lower density due to higher resource consumption  |


:::
::: {.column width="55%"}

![Container vs. Virtual Machines](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/virtualization.jpg?raw=true)


:::
::::