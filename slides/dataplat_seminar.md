# Data Platform - Under the hood

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

Cloud DP are built out of *service ecosystems* offered by *Cloud Service Providers* (CSPs).

![Some of the AWS Services](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/aws_services.png?raw=true)


## On a hardware level

:::: {.columns}
::: {.column width="70%"}

- 12 Nodes (to be increased...)
    - CPU 20 core w5-2445 @4.6 GHZ
    - 256 GB RAM
    - 12 TB HDD
- 2 GPUs NVIDIA RTX 6000 Ada Generation
- 1 Network File System (3 TB)

:::
::: {.column width="30%"}

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
    - remember the **independence** constraint.

:::
::: {.column width="70%"}

:::{.fragment}
![Hardware + Docker architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dataplat_seminar/Slide6.jpg?raw=true)
:::

:::
::::