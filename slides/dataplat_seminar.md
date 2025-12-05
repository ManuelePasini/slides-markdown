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
::: {.column width="25%"}

- In short:
    - 6 research partners;
    - highly heterogeneous data;
    - different goals;

- Main challenges:
    - <b>Governance issues</b>;
    - <b>Sharing issues</b>.


:::
::: {.column width="75%"}

![Agritech project](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/datamesh.jpg?raw=true)

:::
::::


# Let's talk deploy!

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

- <b>Docker</b> is a platform for developing, shipping and running application using container based virtualization technology.

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

## test1
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/func_view.jpg?raw=true)

## test2
![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/ortho.jpg?raw=true)

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
