# 

Principale problema: stanno mettendo mano alla dataplatform aziendale e stanno rifacendo: bigger problem: ingestion
e estrarre dati da sistemi proprietari. SIa saleforce che SAP se devono togliere i dati hanno grossi problemi di billing a cause di lock in.
2 opzioni per analisi:
    - usa i loro tool
    - estrai i dati tramite accrocchi.

Costruire una platform dato un sistema esistente il task tosto è come estrapolare i dati dai sistemi di base e migrarli nei nuovi servizi. Fanno una specie di sampling in cui perdono tanti dati (e.g. campionamento 30min), che se devi fare un analisi comportamentale è bad. 
C'è molta spinta per riportare sul frontend informazioni computate in real time da una data platform, in questi casi 30min sono decisamente tanti.

Pipeline back&forth.
 - dati dabellari strutturati

Sorgente è Salesforce, collection in pull e poi processi.
Change Data Capture rispetto aquello che avevo prima.
Quello che pensano di fare è hashare i campi per i quali vogliono capire se sono cambiati e confrontano gl ihash.
Hanno la parte  storica, e una parte live utilizzata per reporting, eventuali modelli da utilizzare su dati virtuali.

Dopo CDC, tutta la serie storica sul cliente viene portato su un tool su cui viene fatto girare un modello fare AI (xgBoost),  e.g. calcola CLV (custom lifetime value e altri due indici).
Il risulato del modello viene rigirato sulla platform che a sua volta lo ripusha su Salesforce.

Su Google Cloud Platform. **informati su Dataform**, SQLX. permette di fare ETL con source control. Skilled Query e BIGQuery(dove fanno la maggior parte delle trasformazioni). per AI utilizzano Vertex: un notebook schedulato. Puoi schedulare notebook da runnare ad un certo orario con macchine di certa dimensione (tipo databricks). Con Google fanno una riunione ogni due settimane (per consulenze di data platform, engine selection e cosa fare). 
Hanno usato per parecchio e usano AutoML, se non funzia passano a modelli custom (Model Garden (?)): modelli pretrainati che ti mettono a disposizione API per lavorare tipo serverless. 


# ICO
DWH è già nel silver layer
Nel silver i dati sono volatili, 3/4 giorni di vita
La parte bronze è una specie di storicizzazione della parte "effimera" e "Esterna" del viola 

viola arancio - import
arancio grigio - clean

Mosaic AI

Le nostre soluzioni funzionano a livell di orchestrazione, ma soprattutto su databricks e azure la chiave è il compute che decidi di utilizzare

Suddividere il processo in : ingestion - engineering - analisi - elaborazione avanzata

Ci sono tanti piccoli aspetti che non riusciamo a modellare: unity catalog, lineage tra trasformazioni

Databricks