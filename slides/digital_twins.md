
# Digital Twins (DT)
 - Differences between digital shadow, digital model, digital twin
 - Enclosing on a definition...
 - 3 components: phyisical model, virtual model, communication services

:::: {.columns}
::: {.column width="50%"}
![Differences between twins](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/twin_model_shadow.png?raw=true)
:::
::: {.column width="50%"}
![DT components](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt.png?raw=true)
:::
::::

# DT in literature - #1

:::: {.columns}
::: {.column width="50%"}
 - Still a buzzword
 - Rising number of publications
 - Mostly non IT papers
 - Not really twins...

:::
::: {.column width="50%"}
![DT by year (Fei, Tao 2022)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_by_year.png?raw=true)
:::

::::

<div></div> 

:::: {.columns}
::: {.column width="50%"}
  ![DT by journal (Fei, Tao 2022)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_by_journal.png?raw=true)
:::
::: {.column width="50%"}
  ![DT by goal (Fei, Tao 2022)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/goal.png?raw=true)
:::
::::


# DT in literature - #2

 - Mostly manufacturing, smart cities, health domain
 - Still mostly application oriented, focused on visualization (e.g. Unity3D)
 - While concept of data as a core component is arising..
 - ... Still left unconsidered in most research papers.
 - However, some standard models are emerging...
 - Most cited: Fei Tao, Univ.  of Beijing

:::: {.columns}
::: {.column width="50%"}
 ![5-Dimensional DT (Fei, Tao 2020)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/5dim.png?raw=true)
:::
::: {.column width="50%"}
![Virtual Entity architecture (Fei, Tao, 2020)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/digital_model.png?raw=true)
:::
::::

# DT in industry
  - <b>Azure Digital Twins</b>
  - <b>AWS IoT Twin Maker</b>
  - <b>Digital Twin Consortium</b>

# Azure Digital Twins
  - FIWARE like
  - Digital Twin Definition Language (DTDL) - JSON-LD/NGSI-LDgi
  - Offers interfaces to control the physical device (not supported)
  - Native support for Azure Data Explorer (Relational, time-series, ingestion & analytics)
  - Not clear if it facilitates or provides integration with Azure big data services.

:::: {.columns}
::: {.column width="50%"}
  ![Example of DTDL](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dtdl.png?raw=true)
:::
::: {.column width="50%"}
 ![Azure DT Platform](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/azure_dt_historical.png?raw=true)
:::
::::

# AWS IoT Twin Maker
  - Similar to Azure Digital Twins (also JSON Entity-Component model)
  - Different JSON semantics
  - Also graph representation
  - Native support for Grafana, AWS IoT Site Wise (which leverages AWS Timestream, a time-series DB)

:::: {.columns}
::: {.column width="70%"}
  ![Key concept and components AWS IoT Twin Maker ([documentation here](https://docs.aws.amazon.com/iot-twinmaker/latest/guide/what-is-twinmaker.html))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/aws_dt.png?raw=true)
:::
::: {.column width="30%"}
 - <b>Component</b> JSON documents that describe the connection between a data source and AWS IoT Twin Maker. They access external datasource via a Lambda function defined in the JSON
 - Each workspace is assigned an S3 Bucket
:::
::::
 
# DT Data Related Aspects

# DT Data - Modeling
 - Focused on entities last state
 - In literature, wide spread of AutomationML, XML, etc.
 - Mostly graphs (too many connections between data)
 - Initially pure linked data and semantic graphs (RDF, ontologies)
 - New standards (JSON-LD, NGSI-LD) to seamelessly integrate semi-structured data, property graphs and semantic graphs (also supported by RDF)

# DT Data - A brief history 
![Simplified technology history](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/history.png?raw=true)

# NGSI-LD (Next Generation Service Interface – Linked Data)
  - Evolution of NGSI v2, powered by FIWARE
  - Defines a [metamodel](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.06.01_60/gs_CIM009v010601p.pdf) and APIs ([Swagger URL](https://swagger.lab.fiware.org/)) for property graphs
  - “id” now must be an URN (or an URI HTTP)
  - The entity must have a “type” attribute which represent the class of
  the entity
  - The class must then be defined in the @context
  - @context implicitly includes the core @context of NGSI-LD: 

:::: {.columns}
::: {.column width="60%"}
![NGSI-LD Metamodel](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/NGSI_LD_metamodel.png?raw=true)
:::

::: {.column width="40%"}
![NGSI-LD Entity Example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/ngsi_example.png?raw=true)
:::
::::
 
# NGSI-LD vs. NGSIv2  

![Comparison NGSIv2 - NGSI-LD](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/ngsi_ngsild.png?raw=true)


# JSON-LD
  - Make JSON machine-readable again!
  - Defined to merge semantic data and commonly used JSON documents
  - Standard for encoding linked data
  - FIWARE is evolving as well... ([Orion-LD](https://github.com/FIWARE/context.Orion-LD?tab=readme-ov-file))

![JSON-LD Example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/json_ld_example.png?raw=true)

# DT Data - Architectures
  - Most papers don't even mention it!
  - When they do, they focus on entities last-state.
  - <b>Is it really different from a Lambda-like big data architecture?</b>
  - e.g. Digital Twin Consortium

 ![[Digital Twin Consortium Architecture](https://www.digitaltwinconsortium.org/)](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_cons_arch.png?raw=true)

# DT Data - Lifecycle
 - Something is starting to pop out
 - "Trash" literature ? (non IT academics, e.g. [Dihan et. al., 2024](https://www.sciencedirect.com/science/article/pii/S2405844024025349?via%3Dihub))
 - Are we reinventing the wheel?

:::: {.columns}
::: {.column width="50%"}
 ![Digital Twin Data ([Fei, Tao 2023](https://digitaltwin1.org/articles/1-2/v2))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_data.png?raw=true)

:::

::: {.column width="50%"}
 ![Data Methodology ([Fei, Tao 2023](https://digitaltwin1.org/articles/1-2/v2))](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/dt_lifecycle.png?raw=true)
:::
::::


# What next?

:::: {.columns}
::: {.column width="50%"}
 - <b> Data Architectures </b>
   - Focus on historical data
   - Digital Twins Platforms (!!!)

 - <b> Data modeling </b> (on two different abstraction levels)
   - Meta-Models for historicized data in a DT (domain driven?)
   - Standardazing a wider concept (e.g. interoperability between different DT)
  
 - <b> Methodology </b>
    - Watering Digital Twin
:::

::: {.column width="50%"}
![P.h.D. Proposal timeline](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/gantt.svg?raw=true)
:::
::::

# Carbonaro 17/09

- Loro usano property-knowledge graph
- Open word assumption: solo in AND ...
- CONSTRUCT (è quello che utilizzo per le "implementedBy")
- Hanno necessità di separare ciò che è corrente e ciò che è passato.
- SWRL + SPARQL
- Utilizzano GraphDB  (hanno provato)
- Dov'è il confine tra ciò che è nuovo e ciò che è passato? Tradeoff tra quanto velocemente cambiano le cose? Un sensore che cambia ogni 10ms non posso storicizzare.



# Benchmark workload

## Aspects
- **Dimensions**
  - Spatial
  - Temporal
- **Workload**:
  - Operational
  - Analytical

## From [IoTAbench, ICPE 2015](https://dl.acm.org/doi/10.1145/2668930.2688055)

![IoTABench data model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/data_model/iota_model.png?raw=true)

- Total readings: counts the total number of readings (i.e., rows) for the given time period.

- Create a sorted list of the aggregate consumption in each ten minute interval in the given time period.  -> Create a sorted list of the average measurement (?) in each hour interval in the given time period.  

- Top consumers: create a list of the distinct consumers, sorted by their total (monthly) consumption. -> Top agent: create a list of the distinct agents, sorted by their total (monthly) measurements.

- Time of Usage Billing: calculate the monthly bill for each consumer based on the time of usage. -> Time of Task: calculate the monthly time spent doing tasks for each agent.

## From [SmartBench, VLDB 2020](https://dl.acm.org/doi/abs/10.14778/3407790.3407791)

:::: {.columns}
::: {.column width="50%"}

- Coverage (s &in; Sensors): returns the location of a given sensor s.

- InverseCoverage(L, &tau;), where L is a list of locations, and &tau; is a sensor type: lists all sensors that can generate observations of a given type &tau; that can cover the locations specied in L.

- Observations (S &in; Sensors, $t_b$, $t_e$): selects observations from sensors in the list of sensors S during the time range [$t_b$; $t_e$].

- C Observations (&tau; , cond, $t_b$, $t_e$): selects observations generated by sensors of given type &tau; in the time range [$t_b$; $t_e$] that satisfy the condition cond.

- Statistics(S &subseteq; Sensors, A, F, tb, te): retrieves statistics (e.g., average) based on functions specifed in F during the time range [$t_b$; $t_e$]. The statistics are generated by firstrst grouping the data by sensor, and further by the value of the attributes in the list A

- Trajectories($t_b$, $t_e$, $l_b$, $l_e$): retrieves the names of users who went from location $l_b$ to location $l_e$ during the time interval [$t_b$; $t_e$]

- CoLocate($u$ &in; Users, $t_b$, $t_e$): retrieves all users who were in the same Location as user $u$ during the specifoed time period.

- TimeSpent($u$ &in; Users, &eta;, tb, te): retrieves the average time spent per day by subject $u$ in locations of type
&eta;,

- Continuous Query(&tau;, &alpha;, &beta;): retrieves, after every &alpha; seconds (hop size), the minimum, maximum, and average occupancy levels of locations of type &tau; in the last &beta; seconds (window size).

:::
::: {.column width="50%"}

![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/data_model/smartbench_user.png?raw=true)

![SmartBench data model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/data_model/smartbench_sensor.png?raw=true)

:::
::::

## Additional custom queries

- Dati tutti gli agenti di un certo tipo in un certo environment, trovare tutte le misurazioni dal timestamp X al timestamp Y.

- Dato un environment, trovare le rilevazioni di tutti i device dal timestamp X al timestamp Y

- Dato un environment, dammi tutti i measurement dei device di un certo tipo che superano una data soglia.

- Dato un poligono, trovare tutti gli agent che hanno fatto task all'interno del poligono


## Final queries v.0.1

:::: {.columns}
::: {.column width="65%"}

**Q1** Total measurements ($t_b$, $t_e$): counts the total number of measurements for each device during the period [$t_b$; $t_e$].

**Q2** Average hourly measurements (&eta;, [$t_b$; $t_e$]): Create a sorted list of the average measurement of type &eta; in each hour interval in the given period [$t_b$; $t_e$].

**Q3** Monthly measurements($A$): Create a list of the distinct agents $a$ &in; $A$, sorted by their total (monthly) measurements.

**Q4** Latest known agents location ($A$): Return the latest location for each agent $a$ &in; $A$.

**Q5** Observations (&tau; , $cond$, $t_b$, $t_e$): selects measurements generated by agents of given type &tau; in the time range [$t_b$; $t_e$] that satisfy the condition $cond$.

**Q6** InverseCoverage($A$, $L$, &eta;) lists all agents $a$ &in; $A$ that generated measurements of a given type &eta; in the polygon specified by the set of points $L$.

**Q7** Time in environment ($A$, $l$): Return the times for which agents $a$ &in; $A$ were in an environment $l$.

**Q8** Latest measurement in environment($A$, $l$): Return the latest measurement for each agent $a$ &in; $A$ that performed measurements in a given environment $l$.

**Q9** Trajectories($t_b$, $t_e$, $l_b$, $l_e$): retrieves the names of agents who went from location $l_b$ to location $l_e$ during the time interval [$t_b$; $t_e$]

**Q10** CoLocate($a$ &in; A, $t_b$, $t_e$): retrieves all agents who were in the same environment as agent $a$ during the specified time period.

:::
::: {.column width="35%"}

![Workload overview](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/workload.png?raw=true)
:::
::::



## Data architectures

1. Metamodello Agritech (PostgreSQL ?)
2. Wide-Column (?)
3. Grafo + Relazionale (PostgreSQL + PostGIS + Apache AGE)
4. Graph + Time Series (GraphDB + (ClickHouse || InfluxDB))
5. AeonG (?)


# PostGIS

## Spatial Functions
- Routing. With pgRouting and road data you can find optimal routes and do different network analytics;
- Polygon skeletonization. This function enables you to build the medial axis of a polygon on the fly;
- Geometry subdivision. Dividing your geometries for further processing can significantly speed up your processes;
- Clustering. Find clusters and patterns from your data. With the AI hype at peak, the k-means might be even more interesting for some than before…

 ![PostGIS Geometry Hierarchy](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/postgis/geometry_hierarchy.png?raw=true)

## Indexing
 - Indexes have to perform quickly in order to be useful. So instead of providing exact results, as B-trees do, spatial indexes provide approximate results. The question “what lines are inside this polygon?” will be instead interpreted by a spatial index as “what lines have bounding boxes that are contained inside this polygon’s bounding box?”

 - The most common implementations are the [R-Tree](http://www.gitta.info/SpatPartitio/en/html/ObjOriDecomp_learningObject2.html) and Quadtree (used in PostGIS), but there are also grid-based indexes and GeoHash indexes implemented in other spatial databases.

 ![BBox Example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/postgis/bbox.png?raw=true)

 - The way the database efficiently answers the question “what lines intersect the yellow star” is to first answer the question “what boxes intersect the yellow box” using the index (which is very fast) and then do an exact calculation of “what lines intersect the yellow star” only for those features returned by the first test.

# Apache AGE
- Extends PostgreSQL with graph semantics
- No graph data model!
- Wrapper upon PostgreSQL relational storage
- A table for each node/vertex

 ![Apachce AGE under the hood architecture](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/apache_age/architecture.png?raw=true)

## Setup

Create and load AGE extension

    CREATE EXTENSION IF NOT EXISTS age;
    LOAD 'age';

Allow user access to such path

    SET search_path = ag_catalog, "$user", public;

Create a node A

    SELECT * 
    FROM cypher('test_graph', $$
        CREATE (:label {property:"Node A"})
    $$) as (v agtype);

Create a node B

    SELECT * 
    FROM cypher('test_graph', $$
        CREATE (:label {property:"Node B"})
    $$) as (v agtype);

Create an edge between node A and node B

    SELECT * 
    FROM cypher('test_graph', $$
        MATCH (a:label), (b:label)
        WHERE a.property = 'Node A' AND b.property = 'Node B'
        CREATE (a)-[e:RELTYPE {property:a.property + '<->' + b.property}]->(b)
        RETURN e
    $$) as (e agtype);

Select those edges

    SELECT * from cypher('test_graph', $$
            MATCH (V)-[R]-(V2)
            RETURN V,R,V2
    $$) as (V agtype, R agtype, V2 agtype);
