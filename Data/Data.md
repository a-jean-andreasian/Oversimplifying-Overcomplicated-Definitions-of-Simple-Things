_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian._

---

# What is data?

Any information is data, the user info, the user activity, logs, errors, etc.

If it's stored, processed, transmitted, or used to make a decision - it's data.

People try to categorize it: structured, semi-structured, unstructured; transactional vs. analytical, cold vs. hot.

Actually it's the same thing.


> Note: “Big data” is not a scientific threshold it's a marketing label.

---

# Classification of tools

- [**Pipe**](Pipe/Pipe.md)
    - [**Collection Pipe**](Pipe/Types%20of%20Pipes/Collection%20Pipe.md): Gathers raw data and can do basic [
      _transformation_](Transformation%20vs.%20Processing.md).
    - [**Transformation Pipe**](Pipe/Types%20of%20Pipes/Transformation%20Pipe.md): Streams and [
      _transforms_](Transformation%20vs.%20Processing.md) data.
    - [**Transport Pipe**](Pipe/Types%20of%20Pipes/Transport%20Pipe.md): Streams data without any modification.
    - [**Processing Pipe:**](Pipe/Types%20of%20Pipes/Processing%20Pipe.md) Streams and [
      _processes_](Transformation%20vs.%20Processing.md) data.

---

# Table of tools

| Name                                                             | Type     | Term                     | Responsibility                                    | Description                                                     | Add Feature                                   | Optional Feature | Relation                 | Platform       | Ecosystem         |
|------------------------------------------------------------------|----------|--------------------------|---------------------------------------------------|-----------------------------------------------------------------|-----------------------------------------------|------------------|--------------------------|----------------|-------------------|
| [**Beats**](../Tools/Beats/Beats.md)                             | Pipe     | Collection Pipe          | Collection                                        | Collects raw data (logs, metrics, events) from various sources. | -                                             | Transformation   | One to one               | -              | Elastic           |
| [**Logstash**](../Tools/Logstash/Logstash.md)                    | Pipe     | Transformation Pipe      | Transformation, Transport                         | Transforms and enriches the data.                               | Processing                                    | -                | One to one, Many to many | -              | Elastic           |
| [**Redis Streams**](../Tools/Redis%20Streams/Redis%20Streams.md) | Pipe     | Transport Pipe           | Transport                                         | Acts as a message queue for real-time streaming data.           | -                                             | -                | One to one, Many to many | -              | Redis             |
| [**Apache Flink**](../Tools/Flink/Flink.md)                      | Pipe     | Processing Pipe          | Processing, Transport                             | Processes data in real-time (aggregation, computations).        | Further analysis, aggregation, transformation | -                | Many to many             | -              | Apache            |
| **Apache Spark**                                                 | Pipe     | Processing Pipe          | Further analysis, aggregation, and transformation | Processes large-scale data efficiently.                         | -                                             | -                | Many to many             | -              | Apache            |
| **Apache Kafka**                                                 | Platform | Event Streaming Platform | Event Streaming                                   | Acts as a buffer, receiving and distributing data streams.      | -                                             | -                | One to one, Many to many | -              | Apache            |
| **ClickHouse**                                                   | Storage  | -                        | Storage                                           | Stores and processes analytical data.                           | Search                                        | -                | -                        | -              | ClickHouse        |
| **Elasticsearch**                                                | Storage  | -                        | Storage                                           | Stores processed data and enables search capabilities.          | -                                             | -                | -                        | -              | Elastic           |
| **Hadoop**                                                       | Storage  | -                        | Storage                                           | Stores large-scale processed data.                              | -                                             | -                | -                        | -              | Apache            |
| **Druid**                                                        | Storage  | -                        | Storage                                           | Stores and indexes real-time and historical data.               | -                                             | -                | -                        | -              | Apache / Druid.io |
| **Grafana**                                                      | Tool     | -                        | Visualization (Dashboard)                         | Visualizes final results in dashboards.                         | -                                             | -                | -                        | Multi-platform | Grafana Labs      |
| **Kibana**                                                       | Tool     | -                        | Search, Visualization                             | Queries and visualizes Elasticsearch data.                      | -                                             | Dashboard        | -                        | -              | Elastic           |
| **Prometheus**                                                   | Tool     | -                        | Event Monitoring & Alerting                       | Monitors and collects time-series metrics.                      | -                                             | -                | -                        | -              | CNCF / Prometheus |
| **Superset**                                                     | Tool     | -                        | Dashboard                                         | Provides an interactive dashboard for data visualization.       | -                                             | -                | -                        | -              | Apache            |
