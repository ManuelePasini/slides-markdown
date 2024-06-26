


# Towards a Process-Driven Design of Data Platforms

<hr style="border: none; border-top: 1px solid #000;">

<div style="text-align:center">
<span style="font-size: larger;">Matteo Francia, Matteo Golfarelli, <b>Manuele Pasini</b></span>

*{m.francia, matteo.golfarelli, manuele.pasini} @unibo.it*

25/03/2024


:::: {.columns}
::: {.column width="20%"}
![](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/big.png?raw=true)
:::
::::

</div>



# A Cloud Data Platform

<!--is an infrastructure that facilitates the ingestion, storage, management, and exploitation of large volumes of data.
-->
- Is a *centralized* infrastructre composed of *independent* and *well-integrated* services meeting the *end-to-end* needs of data pipelines:
    - *Centralized*: a data platform is conceptually a single and unified component;
    - *Independent*: changes in a a service do not affect others;
    - *Well-integrated*: services have interfaces enabling a frictionless composition;
    - *End-to-end*: services cover the entire data life cycle.

Cloud DP are built out of *service ecosystems* offered by *Cloud Service Providers* (CSPs).

![Some of the AWS Services](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/aws_services.png?raw=true)

# Data platforms for analytics

Data analytics nowadays mostly rely on cloud infrastructures.

:::: {.columns}
::: {.column width="40%"} 

- Some CSPs categorize their services in relation to the role they play in an analytical data pipeline...
    - ... So data pipelines might serve as pivotal points in the design of data platforms!
    - But even for experienced data pipeline designers, this is a non trivial task...

:::

::: {.column width="60%" }
![Some of the Google Cloud Platform Services](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/master/slides/images/cloud_platform.bmp)
:::
::::


 
<!--
:::: {.columns}
::: {.column width="50%"}

:::{.fragment}
![Some of the AWS Services](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/aws_services.png?raw=true)
:::
:::

::: {.column width="50%"}
:::{.fragment}
![Some of the Google Cloud Platform Services](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/cloud_platform.png?raw=true)
:::
:::
::::
-->
# Challenges in building data platforms

- CSPs offer *services with overlapping functionalities*;
- CSPs offer *different service categorizations*;
- *Evolution* of cloud ecosystems is fast;
- Third parties can publish their own services on marketplaces (e.g., AWS Marketplace).

As if it was not hard enough...

- *Multiple solutions could fulfill the desiderata*:
    - It requires vertical knowledge on the design of data pipelines...
    - ... And also deep knowledge of CSPs' ecosystems.
- Several abstract big data architectures are available (e.g., NIST, Lambda, and Kappa):
    - They not address their deployment!

:::{.fragment data-fragment-index=3}
<span style="font-size: larger">
**Research question**: *given an ecosystem of services, which is the optimal subset enabling a data platform?*
</span>
:::

# Process-driven design

:::: {.columns}
::: {.column width="58%"}
The description of data-driven processes should drive such activity!

- *Data pipelines* encode many constraints on the choices to be made...
- ... And outline data flows!

**Research goal**: *methodology to aid designers* in selecting the services necessary to implement clients' data pipelines out of the "unstructured" lists of services from CSPs.

![Methodology for the Design of Data Platforms](https://w4bo.github.io/DOLAP-2024-DataPlat/img/overview.svg)

:::
::: {.column width="40%"}

>   **Three types of users** (stakeholders):
>
>   - *Cloud service providers*: IT experts with in-depth knowledge of services ecosystems;
>   - *Designers*: people with expertise in designing data flows but with no vertical knowledge on service ecosystems;
>   - *Clients* asking for the design of the data platform blueprint.


:::

::::

# (1) Define the service ecosystem

*CSP* identifies *una tantum*: 

:::: {.columns}
::: {.column width="50%"}

The **services** to compose the blueprint of the data platform:

- Not necessarily all of them...
- ... But they must cover the "basic" functionalities for a data platform such as the ones from NIST!

<div style="font-size: 0.6em">
| Solution areas     | Use cases                         | AWS services           |
|--------------------|-----------------------------------|------------------------|
| Advanced analytics | Big data processing               | EMR                    |
|                    | Data warehousing                  | *Redshift*             |
|                    | Dashboards and visualizations     | *QuickSight*           |
|                    | ...                               | ...                    |
| Data management    | Data governance                   | Glue, **S3**, ...      |
|                    | Object storage for data lakes     | **S3**, Lake Formation |
|                    | Backup and archive for data lakes | **S3 Glacier**, Backup |
|                    | ...                               | ...                    |
| Machine learning   | Platform services                 | SageMaker              |
| ...                | ...                               | ...                    |
: Example of services from the AWS website (as of November 2023)
</div>
:::
::: {.column width="50%"}


The **taxonomy of tags** characterizing such services:

- *Bottom-up* feeding: built out of the experience of the CSP and/or automatically extracted using NLP algorithms;
- *Top-down*  feeding: from the literature (e.g., Vs of big data).

<div style="font-size: 0.6em">
|L1|L2|L3|
|-------------------|------------------|---------------------|
| Data Model (All)  | Structured       | Relational          |
|                   |                  | Multidimensional    |
|                   | Semi-structured  | Document            |
|                   |                  | File (text, binary) |
| ...               | ...              | ...                 |
| Data Nature (All) | Spatial          | Vectorial           |
|                   |                  | Raster              |
| ...               | ...              | ...                 |
| Goal (All)        | OLAP             |                     |
|                   | Operational      |                     |
|                   | Machine learning | Classification      |
|                   |                  | Regression          |
| ...               | ...              | ...                 |
: Examples of Tags
</div>


:::
::::
<!--
# "Alternative" bottom-up feeding

![Using ChatGPT](https://github.com/ManuelePasini/slides-markdown/blob/4893698e949da4ee45c95087b170c011a4b9f687/slides/images/alternative_feeding.png?raw=true)
-->
# Service graph

Services are organized in a directed property *service graph*.

- Nodes are engines from the service ecosystem and can be labelled as *preferred*.

    - Each node is characterized with a *set of properties* from the previously determined taxonomy.

- Arcs are alternatively labeled as *{Requires, IsCompatible}*:

    - *Requires*: a service mandatorily relies on another;
    - *IsCompatible*: a service natively interfaces with another.


> :::: {.columns}
> ::: {.column width="55%"}
> ![Excerpt of service graph](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/9990069e4bae6eb4ca3be5034f105fdceff81a8b/slides/images/service_graph.svg)
> :::
> ::: {.column width="45%"}
>
> **Example**
>
> - *IsCompatible*: `SageMaker` natively R/W from/to `Redshift`;
> - *Requires*: `GeoServer` requires `EC2` since it is deployed on it.
>
>
>  $\begin{align}
> props(GeoServer) = \{&(Data Model, File), \\
> (Data Nature, Raster)\}\\
>  \end{align}$
:::
:::



# Input: clients' questionnaries

Clients compile questionnaires about their processes and the main *steps*, *subjects*, and *goals* of their analysis.

> **Example**: deploy a data platform supporting analytic tasks from *8 clients* within the Agritech European project
> 
> Excerpt of one of the workflows:
>
> 1. Data comes from *soil moisture sensor grids*, *weather stations*, and *SENTINEL-2* satellites.
> 1. Sensor and weather data is *uploaded every 15 minutes*, while satellite data is *periodically downloaded*.
> 1. *Soil moisture data* is *interpolated* using mathematical and machine learning techniques.
> 1. The *interpolated data* is stored in *tables* that include the *positions of the sensors*.
> 1. *Vegetation indexes* are computed out of *raw satellite observations* and *integrated with enriched sensor data*.
> 1. *Reports* are periodically generated *out of enriched data*.
> 1. Given an optimal soil moisture matrix, the *enriched data* is used to *decide how much to irrigate the soil*.

<!--
# ... and ChatGPT

:::: {.columns}
::: {.column width="50%"}
![Excerpt of answer](and_gpt_1.png)
:::
::: {.column width="50%"}
![Excerpt of answer](and_gpt_2.png)
:::
::::

- ChatGPT kind of understand the processes but recommends many services
- ... and it recommends to adapt the choice based on the requirements. Back to square 1!
-->
# (2) Formalize the requirements

:::: {.columns}
::: {.column width="45%"}
*Designers* refine the answers and *formalize the processes* into DFDs:

- A *Data Flow Diagram (DFD)* is a directed property graph $G^D$:
    - Nodes are alternatively labeled as *{Agent, Repository, Process}*;
    - Arcs are labeled as *Flow*.
- *DFD* represents flows of data at a *high level of abstraction*:
    - Hide details such as decision points and interactions;
- Knowing *which types* of repositories/processes compose the processes is **enough to return a blueprint**.

:::
::: {.column width="55%"}
> **Example**
>
> ![DFD of the Agritech Case Study](https://w4bo.github.io/DOLAP-2024-DataPlat/img/dfd.svg)
>
> - `Moisture Sensors` streams data into the platform; `Satellite` images are periodically downloaded;
> - `Sensor Data` and `Raw Images` contain heterogeneous data types.

:::
::::

# (3) Enrich the DFD with service tags

Building our blueprint requires to match the DFD and service graphs.

To do so, *the two must share the same characterization*:

- Each process and repository in the DFD is enriched with the tags from the previously identified taxonomy:
    - To characterize them, clients answer an additional set of questions driven by the tag taxonomy.


> **Example**: given a repository from the DFD, designers ask the question:
> "What are the main types of collected data?"
> 
> - [ ] Sensor data
> - [ ] Images
> - [ ] Videos
> - [x] Satellite observations
> - [ ] Tables
> 
> Answering "Satellite observations" tags the repository with the properties `(Volume, Big)`, `(Data Model, File)`, and `(Data Nature, Raster)` since earth observations are data-heavy files (e.g., around 1 GB for 100 $km^2$) and tags the process to download such data as `(Collection, Pull)` since files are downloaded from an FTP server.



# (4) Match the DFD and service graphs

Since DFD and service graphs are characterized by the same taxonomy, we can *automatically* match them!

- A DFD process or repository *matches* (can be implemented by) a service only *if the service has the same or more functionalities*;
    - If no match is found, we force it to a *default* (e.g., a VM where any functionality can be implemented).


> **Example**: given the node `Raw Images` from the DFD where
>   
> $\begin{align}
> props(Raw Images) = \{&(Data Model, File), (Data Nature, Raster)\}
> \end{align}$
> 
> and the nodes `S3` and `GeoServer` from the service graph where
> 
> $\begin{align}
> props(GeoServer) = \{&(Data Model, File), (Data Nature, Raster)\}\\
> props(S3) =        \{&(Data Model, File), (Volume, All)\}
> \end{align}$
> 
> `Raw Images` can be implemented by `GeoServer` but not in `S3` since the former is natively capable of managing geographical raster images.

# Matched graph

The *matched graph* is composed of the union of the graphs plus additional arcs *IsImplementedBy* that represent candidate implementations for the DFD processes/repositories.

> **Example**
> 
> ![Matched graph](https://w4bo.github.io/DOLAP-2024-DataPlat/img/match.svg)
> 
> - `Consume` can be implemented by either `Lambda` or `Kinesis`;
> - `Churn Prediction` and `Athena` can be discarded a priori since they are not reachable.


# (5) Select the optimal services
:::: {.columns}
::: {.column width="50%"}
Out of all matching services, only some of them must be selected:

1. The amount of *selected services is minimized*.
1. *Coverage*: all processes/repositories in the DFD must be covered.
1. *Dependency*: if a service is selected, all its required services must be selected too.
1. *Compatibility*: a service can be selected only if it is compatible with the services selected for the adjacent nodes in the DFD.
1. *Preference*: preferred services should have more chances to be selected.

This is a *facility location optimization* linear programming problem (available on [Github](https://github.com/big-unibo/DataPlatformDesign) w/ Python + CPlex library).

:::
::: {.column width="50%"}


> **Optimal blueprint**
>
> ![Services selected (in bold) for the blueprint of the data platform](https://raw.githubusercontent.com/ManuelePasini/slides-markdown/da1422db0e16e1db09cc4c49b9611f7f1b7d23d6/slides/images/optimal.svg)


:::
::::

# Conclusion and future works

The design of data platforms is a nontrivial task:

- We introduced a **process-driven design methodology** to *aid designers* in selecting the optimal set of services out of a service ecosystem;
- We addressed such **selection as a facility location optimization problem**.

Improvement in multiple aspects:

- **Expressivenes**: matching and selection should consider more complex architectural patterns as well as support additional constraints.
- **User evaluation**: the produced blueprints should be compared with the ones recommended by expert designers. 
- *Resource provisioning*: a complete approach should also consider how many instances of a service are required.
- *Graphs formalization*: the definition both graphs relies on manual work, more automated techniques should be explored.
- *Metadata integration*: the design should also recommend services helping in the management of the platform itself.


# *Thanks!*

Questions?

