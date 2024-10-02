
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



# Queries

## Sensoriali

- Dati tutti gli agenti di un certo tipo in un certo environment, trovare tutte le misurazioni dal timestamp X al timestamp Y.

- Dato un environment, trovare le rilevazioni di tutti i device dal timestamp X al timestamp Y

- Dato un environment, dammi tutti i measurement dei device di un certo tipo che superano una data soglia.

- Dato un poligono, trovare tutti gli agent che hanno fatto task all'interno del poligono

##### From [IoTAbench](https://dl.acm.org/doi/10.1145/2668930.2688055)

- Total readings: counts the total number of readings (i.e., rows) for the given time period.

- Create a sorted list of the aggregate consumption in each ten minute interval in the given time period.  -> Create a sorted list of the average measurement (?) in each hour interval in the given time period.  

- Top consumers: create a list of the distinct consumers, sorted by their total (monthly) consumption. -> Top agent: create a list of the distinct agents, sorted by their total (monthly) measurements.

- Time of Usage Billing: calculate the monthly bill for each consumer based on the time of usage. -> Time of Task: calculate the monthly time spent doing tasks for each agent.



## Data architectures

1. Metamodello Agritech (PostgreSQL ?)
2. Wide-Column (?)
3. Grafo + Relazionale (PostgreSQL + Apache AGE)
4. Graph + Time Series (GraphDB + (ClickHouse || InfluxDB))


## Scaletta
- Come funziona modellazione dati nel GIS?

### PostGIS

#### Spatial Functions
- Routing. With pgRouting and road data you can find optimal routes and do different network analytics;
- Polygon skeletonization. This function enables you to build the medial axis of a polygon on the fly;
- Geometry subdivision. Dividing your geometries for further processing can significantly speed up your processes;
- Clustering. Find clusters and patterns from your data. With the AI hype at peak, the k-means might be even more interesting for some than before…

 ![PostGIS Geometry Hierarchy](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/postgis/geometry_hierarchy.png?raw=true)
