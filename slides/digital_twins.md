
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

- **Mode**:
  - Online (?)
  - Offline (?)

## From [IoTAbench, ICPE 2015](https://dl.acm.org/doi/10.1145/2668930.2688055)

![IoTABench data model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/data_model/iota_model.png?raw=true)

- Total readings: counts the total number of readings (i.e., rows) for the given time period.

- Total consumption: sums the resource consumption for the given time period.

- Peak consumption: Create a sorted list of the aggregate consumption in each ten minute interval in the given time period. 

- Top consumers: create a list of the distinct consumers, sorted by their total (monthly) consumption.

- Time of Usage Billing: calculate the monthly bill for each consumer based on the time of usage.

## From [SmartBench, VLDB 2020](https://dl.acm.org/doi/abs/10.14778/3407790.3407791)

:::: {.columns}
::: {.column width="50%"}

- Coverage (s &in; Sensors): returns the location of a given sensor s.

- InverseCoverage(L, &tau;), where L is a list of locations, and &tau; is a sensor type: lists all sensors that can generate observations of a given type &tau; that can cover the locations specied in L.

- Observations (S &in; Sensors, $t_b$, $t_e$): selects observations from sensors in the list of sensors S during the time range [$t_b$; $t_e$].

- C Observations (&tau; , cond, $t_b$, $t_e$): selects observations generated by sensors of given type &tau; in the time range [$t_b$; $t_e$] that satisfy the condition cond.

- Statistics(S &subseteq; Sensors, A, F, $t_b$, $t_e$): retrieves statistics (e.g., average) based on functions specifed in F during the time range [$t_b$; $t_e$]. The statistics are generated by firstrst grouping the data by sensor, and further by the value of the attributes in the list A

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


## Other benchmarks

##### Spatial DB

- The SEQUOIA 2000 Storage Benchmark, <b style="color: blue;">SIGMOD 1993</b>
- Building a ScalableGee-SpatialDBMS: Technology, Implementation,and Evaluation <b style="color: blue;">SIGMOD 1997</b>

##### Time Series DB

- TS-Benchmark: A Benchmark for Time Series Databases, <b style="color: blue;">ICDE 2021</b>
- SciTS: A Benchmark for Time-Series Databases in Scientific Experiments and Industrial Internet of Things,  <b style="color: blue;">International Conference on Scientific and Statistical Database Management 2022 (SSDBM) </b>
- TSM-Bench: Benchmarking Time Series Database Systems for Monitoring Applications, <b style="color: blue;"> VLDB 2023 </b>

##### Spatio-Temporal

- BerlinMOD: A benchmark for moving object databases, <b style="color: blue;">VLDB Journal 2009</b>
- Benchmarking moving object functionalities of DBMSs using real-world spatiotemporal workload, <b style="color: blue;">International Conference on Mobile Data Management 2022</b>
- Performance Evaluation of MongoDB and PostgreSQL for spatio-temporal data, <b style="color: blue;">EDBT/ICDT Workshops 2019</b>
- How to manage massive spatiotemporal dataset from stationary and non-stationary sensors in commercial DBMS?, <b style="color: blue;">Knowledge and Information Systems 2024</b>

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
- A table for each node/vertex label

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

# Spatio Temporal DBMS

## [A Survey on Spatio-temporal Data Analytics Systems, ACM Surveys 2022](https://dl.acm.org/doi/full/10.1145/3507904)  

-  Categorizes spatio-temporal DBMSs in groups:
    - Spatial DBMS:
      - RDBMS
      - No-SQL DBMS
    - Big data spatio-temporal processing infrastructures
      - Hadoop based infrastructures
      - Spark based infrastructures
      - No-SQL infrastructures
    - Programming languages
      - DASK
      - RAPIDS

## Spatial DBMS

:::: {.columns}
::: {.column width="50%"}

### RDBMS

![Taxonmy of RDBMS for spatio-temporal data](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/rdbms.png?raw=true)

- Due to the I/O bottleneck, lack of parallelism and scalability, the performance of these systems deteriorated with the increasing volume of data.
- PostgreSQL -> PostgresXL
- MobilityDB was developed as an extension of PostgreSQL/PostGIS, providing support for storing and querying moving objects data (trajectory). This support includes spatio-temporal data types, indexing techniques, and query operations. Recently, MobilityDB emerged as a distributed system by integrating with Citus for
processing massive trajectory data


:::
::: {.column width="50%"}

### No-SQL DBMS

![Taxonmy of No-SQL DBMS for spatio-temporal data](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/nosql.png?raw=true)

 - Currently, the spatial support of NoSQL databases lacks available spatial operations compared to spatial RDBMSs.

:::
::::

## RDBMS vs NoSQL for Spatial Data
[Performance Evaluation of MongoDB and PostgreSQL for Spatio-temporal Data, EDBT/ICDT Workshops 2019](https://ceur-ws.org/Vol-2322/BMDA_3.pdf)

:::: {.columns}
::: {.column width="30%"}

##### Dataset Size
- 11 GB, 43 288 vessels, 146.491.511 records
- MongoDB: 116 GB
- PostgreSQL: 32 GB

:::
::: {.column width="35%"}

##### Dataset Schema

 ![](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/mongo_postgre_dataset_schema.png?raw=true)

:::

::: {.column width="35%"}

##### Spatio-temporal Queries

- Find coordinates of different amount of vessels from 1/May/2016 - 31/July/2016 (entire time window) within the whole bounded area, Q1;
- Find coordinates of vessels for different time windows  within the whole bounded area, Q2;
- Find coordinates of vessels for different geographical polygons within the entire time window, Q3.

:::

::::
-  MongoDB stores data in GeoJson format, each record has many extra characters + unique auto created ObjectId. PostgreSQL ingests data as CSV, with adding the_geom column that contains the POINT geometries for latitude and longitude.

##### Results

 - The results show that PostgreSQL with the PostGIS extension, outperforms MongoDB in all queries.


## Big spatio-temporal data processing infrastructures

:::: {.columns}
::: {.column width="50%"}

### Hadoop based

![Taxonmy of Hadoop based systems for spatial data](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/hadoop.png?raw=true)

- Due to the lack of spatio-temporal data types, partitioning, and indexing techniques, Hadoop-GIS & SpatialHadoop suffer querying spatio-temporal datasets
- ST-Hadoop was developed by considering attributes of discrete spatio-temporal point data, not trajectory data. So data might be wrong-sharded when indexed.
- Summit is an extension of ST-Hadoop to include data types, partitioning and indexing techniques, and operations, for processing trajectory data. 
- Bakli et al. [27] have proposed HadoopTrajectory, which adds a diverse set of data types and operators into the core of Hadoop to store and process trajectory data.

:::
::: {.column width="50%"}

### Spark-based

![Taxonmy of Spark based systems for spatial data](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/spark.png?raw=true)

- First five spatial data processing solutions are not fully compliant with the ISO standard and OGC specifications.
- STARK integrates spatio-temporal support to Spark RDDs
- DiStRDF is a distributed system for processing spatio-temporal RDF data; however, these last two focus on discrete data points and not trajectories.
- TrajSpark does not have any support for SQL-like queries.
- UITraMan has added an off-heap key-value store, Chronicle Map
- Among TrajSpark, DITA, and UITraMan, only TrajSpark alleviates the overhead of repartitioning the whole dataset when a new batch of dataset arrives. Thus, TrajSpark achieves near real-time trajectory processing capability. Besides, this newbatch of data is loaded as RDDs in Spark, which are immutable, and any updates on RDD create a new RDD, which is costly.
- Dragoon [93] is a hybrid system for processing both historical (offline) and streaming (online) trajectories. The offline module of Dragoon
is similar to UITraMan, but Dragoon has utilized Chronicle Map in such a way that it works for both historical and streaming trajectories.
- <b> All these systems are for processing vector spatial and spatio-temporal data. None of these systems has support for raster data except Apache Sedona. </b>
- Beast supports both vector and raster data with multidimensional data types and partition and index structures.

:::
::::

## Big spatio-temporal data processing infrastructures

### NoSQL based

![Taxonmy of NoSql based big systems for spatial data](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/spatiotemp_dbms/nosql_big.png?raw=true)

- GeoMesa linearizes the keyspace by transforming multi-dimensional data (location, timestamp) into 1D keys using space-filling curves.
- JUST incorporates leverages HBase, GeoMesa, and Spark. Introduces two new indexing techniques, Z2T and XZ2T and efficient compression mechanism that improves the query performance significantly.
- TrajMesa, horizontal storage schema (H-Store) is proposed. Allowing to store an entire trajectory in one-row with compression.
 
## Recent literature

- SpaceTimeDB (commercial, (?))
- Springbok, ICDE 2024
- CUPID, Future Generation Computer Systems 2024
- TMan, ICDE 2024

### Other Research Trends

##### ML for query optimization

- Spatial Query Optimization With Learning, VLDB 2024

##### Indexing

- A Time-Identified R-Tree: A Workload-Controllable Dynamic Spatio-Temporal Index Scheme for Streaming Processing, International Journal of Geo-Information 2024


## A case study for Digital Twins

- Graph + TimeSeries (Apache AGE + PostgreSQL + PostGIS + Timescale)
- MobilityDB (PostgreSQL + PostGIS + trajectory data support)
- Beast 
- CUPID
- Springbok

## Case study 0 - Apache Age + TimescaleDB + PostGIS

### Emerged considerations
 - Given a FIWARE document, what's a Property and what's an Edge? - It's an edge if it links to an NGSI URN
    - Should the graph enforce some kind of schema?  E.g. metamodel - I beleve so but dunno
    - If not, Do I have to check wether a FIWARE key-value pair links to a node?
      - But then, I have to check all properties, understand if its an edge or a property, remove it from the entity if it's an edge, check if the edge destination already exists and if it does not, create it and link it to the source node-
    - What about device composition? e.g. moisture grid
 - What about Ids? Apache AGE uses its own custom IDs that <b> cannot </b> be disabled
 - <b> What happens when a new measurements comes by?</b>
    - I have to check if such node exists, if not, it's a new edge, if it is
 - An entity comes in: there's already a node with such id; is it an update? Is it a measurement?

### Modellazioni Measurement

 - AgriRobot non è un device, come capisco se qualcosa ha dei measurement da storicizzare?
 - Agri robot non storicizza le controlled property, come faccio a capire cosa devo storicizzare?

### Problemi sui dati

 - I dati dei pinotech hanno il dateObserved sbagliato ("Z" alla fine della data)
 - Per creare un arco, devo prima avere entrambi i nodi altrimenti non funzia

## Age Middleware

- Builds a connection to a Apache Age + PostGIS + Timescale DBMSs.
- Processes JSON entities following the NGSI schema.

  ##### Entity required schema

  - "id": follows the NGSI standard (urn-ngsi-[...]) and define the existence of an entity in the graph
  - "type": defines the label of the node/edge in the graph.

  ##### Entity optional schema

  - "hasDevice": defines device composition. Each value of this key needs to be a json representing an entity.

##### Building the graph

- Each distinct entity (unique "id") gets mapped into the graph as a node.
- Each entity key that has an ID as a value becomes an edge with the key as the edge label.
- If an entity with the given "id" exists, update such entity in the graph

##### Parsing into measurement

Measurement = TimescaleTable(timestamp, device_id, controlledProperty, value, raw_value)

- A mapping can defined for each entity "type": it's a Python functions that extracts the measurements from a JSON entity with the Measurement table structure

## Environment setup

CREATE EXTENSION IF NOT EXISTS age;
CREATE EXTENSION IF NOT EXISTS postgis;
LOAD 'age';
SET search_path = ag_catalog, “$user”, public;

CREATE TABLE measurements(
	timestamp timestamp,
	device_id text,
	controlled_property text,
	location geometry,
	value float,
	raw_value text
)
SELECT create_hypertable('measurements', 'timestamp');

ALTER TABLE measurement
ADD PRIMARY KEY(timestamp, device_id, controlled_property)

CREATE INDEX location_index
  ON measurements
  USING GIST (location);

## Problematiche

Tre cause delle problematiche:
- Modellazione concettuale (e.g. no tipo di device in measurements)
- Architetturale (Apache Age)
- Ottimizzazione query (e.g. no tabella location ausiliaria)


### Espressività

- Mancanza di un'interfaccia uniforme sul modello, devi interfacciarti e integrare due tipologie di modelli dati diversi
- No storicizzazione di ciò che non è measurement

### Modellazione

- Se parti dal grafo arrivi ad un punto in cui joini sul relazionale, va fatta attenzione alla query su grafo in quanto è molto facile ritorni un insieme di valori ridondanti che fanno esplodere il tempo computazionale
- Cosa succede sul grafo se il nodo esiste già? Lo aggiorno, ma in che modo? Sovrascrivo il vecchio? Aggiungo le diff? E le diff in negativo vanno tolte? Cosa succede ai suoi archi? Se nella nuova versione non vedo un arco?

### Random considerations (constantly updated)

## [TimescaleDB](https://docs.timescale.com/use-timescale/latest/extensions/)

- Build upon a PostgreSQL instance.
- Based on <b>hypertables</b>:
  - Logical table
  - Organizes the data in chunks (of a predefined time range) based on some time/bigint column of the table (B-Tree)
  - Other columns can be added in partitioning columns 
  - Support for distributed hypertables
  - Supports a large set of PostgreSQL extensions (e.g. PostGIS, PostGIS_Raster)

![Table organization in chunks](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/timescale/chunks.png?raw=true)


## TimescaleDB - Query language

:::: {.columns}

::: {.column width="50%"}

- Uses standard SQL with a more operators/functions:
  - time_bucket('1 hour', column_name): same as date_trunc in PostgreSQL but with custom granularity
  - ...

  - [Hyperfunctions](https://docs.timescale.com/api/latest/hyperfunctions/):
    - Time-weighted averages;
    - Percentile approximation;

:::

::: {.column width="50%"}

![Hyperfunctions list](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/timescale/hyperfunctions.png?raw=true)

:::

::::

## TimescaleDB - Further functionalities

:::: {.columns}

::: {.column width="50%"}

- <b>Hybrid row-column oriented data model</b>: define a retention period where data older will be stored as column-oriented data.
  - Column-Oriented data can still be performed DML/DDL operations upon.

![Timescale hybrid model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/timescale/hybrid_model.png?raw=true)

:::

::: {.column width="50%"}

##### TimescaleDB - Hybrid model optimizations

- <b>segmentby</b>: partion data inside chunk on [column1, ...]

![Segmentby example - partition by device id](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/timescale/segmentby.png?raw=true)
  
- <b>orderby</b>: orders data within a chunk based on time and stores metadata w.r.t min/max values in the chunk (similar to Databricks data-skipping)

Together: data is first grouped by the segmentby column, then ordered based on the orderby parameter, and finally divided into smaller, timestamp-ordered “mini-batches,” each containing up to 1,000 rows.

:::

::::

## TimescaleDB - Further functionalities

##### Continuous aggregates

- Like a continuous materialized view
- Automatically (in background) maintain the results from the query.
- Refreshed automatically in the background as new data is added, or old data is modified.

##### Tiered storage

Move least-accessed data into a different tablespace, in order to reduce the volume of data in highly-accessed data

![Tiered architecture example](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/timescale/tiered_storage.png?raw=true)

## InfluxDB

- Not based upon the relational model (organizes data in tags and fields)
- Not really CRUD db: more like a CR-ud, prioritizing the creating and reading data over update and destroy

## InfluxDB - Data Model

- <b>Bucket</b>: Named location where time series data is stored. A bucket can contain multiple measurements.
  - <b>Measurement</b>: Logical grouping for time series data. Points in a given measurement share the tags. A measurement contains multiple tags and fields.
    - <b>Tags</b>: Key-value pairs with values that differ, but do not change often. Tags are meant for storing metadata for each point–for example, something to identify the source of the data like host, location, station, etc.
    - <b>Fields</b>: Key-value pairs with values that change over time–for example: temperature, pressure, stock price, etc.
    - <b>Timestamp</b>: Timestamp associated with the data. When stored on disk and queried, all data is ordered by time.

- <b>Point</b>: Single data record identified by its measurement, tag keys, tag values, field key, and timestamp.
- <b>Series</b>: A group of points with the same measurement, tag keys, and tag values.

 ![InfluxDB data model](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/influx_db/data_model_explained.png?raw=true)

## InfluxDB - Storage Engine

- Writes and retrieves data from disk; four components:
  - Write Ahead Log (WAL):  retains data when storage engine restarts. Ensures data is durable in case of unexpected failure.
  - Cache: in-memory copy of data points currently stored in the WAL.
    - Organizes points by key (measurement, tag set, and unique field)
    - Gets queried at runtime and merged with the data stored in Time Structured Merge (.tsm) files
  - Time Structured Merge Tree (.tsm) files 
  - Time Structured Index (.tsi) files
- Each write requests follows:
  - Is appended to the end of the WAL file;
  - The write request is stored in an in-memory cache and data is sorted by key (measurement name, tag set and unique field key).
  - Once cache's size is above a threshold, a snapshot is taken and saved as .tsm file. Corresponding WAL entries are removed
- .tsi files are created with a similar procedure WAL + cache.

## InfluxDB - Time Structured Merge Tree (TSM)

- Specialization of a Log-Structured Merge Tree
- Stores each series data in a columnar format
- To improve efficiency, the storage engine only stores differences (or deltas) between values in a series.
- <b>Series</b>: A group of points with the same measurement, tag keys, and tag values.

![InfluxDB TSM organization](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/influx_db/data_model.png?raw=true)

## InfluxDB - Time Structured Merge Index (TSI)


## InfluxDB - Query language

- Flux: non-SQL-like syntax
- InfluxQL: SQL-like but with less operatiors (e.g. no UNION, JOIN and HAVING)

## Timescale vs. InfluxDB

- Schema variability: while on a TimescaleDB table schema has to be defined upfront (can't add dimensions to a non-empty table), InfluxDB is much more flexible
- SQL JOINs aren’t available for InfluxDB measurements in InfluxQL, they are with Flux. [doc](https://docs.influxdata.com/influxdb/v1/concepts/crosswalk/)

## Overall

- Timeseries DBMS (TSDBMS) are optimized for temporal data, each TSDBMS follows its own philosophy.
- Very-High frequency of writes
- Most read queries are range-scan queries;
- Very few/none update/delete queries.  
- Focus on data compression (!! since volumes easily become in the order of PB, and since most queries focus on recent data), e.g. retention policies
- Focus on opimizations, e.g. data-skipping, downsampling, user-defined-functions (e.g. hyperfunctions in Timescale)

## Log-Structured Merge Tree (LSM Tree)

- Append only
- Data is first written to an in-memory structure (MemTable), then moved to disk in batches in form of SSTables.

![Writing data in a LSM tree](https://github.com/ManuelePasini/slides-markdown/blob/master/slides/images/dt/influx_db/lsm_tree.png?raw=true)

- <b>MemTable</b>: in-memory temporary sorting area. As it fills up, its contents are flushed to disk in a batch of sorted data structures called Sorted String Tables (SSTables).
- <b>Sorted String Tables (SSTables)</b>: They store data in sorted order, enabling efficient queries and range scans. Each SSTable represents a snapshot of data at a specific point in time.
- <b>Levels</b>: SSTables are organized into levels. Lower levels contain more recent data, while higher levels store compacted data.

- <u><b>Compaction becomes vital!</u></b>