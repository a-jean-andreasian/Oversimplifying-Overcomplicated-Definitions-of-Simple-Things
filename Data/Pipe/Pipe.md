_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian._

---

### Content

- [What are Pipes?](#what-are-pipes)
- [Types of Pipes in the Data Pipeline](#types-of-pipes-in-the-data-pipeline)

---

## **What are Pipes?**

Pipes are used to collect and transfer data.

Connected pipes are called pipelines.

---

## **Types of Pipes in the Data Pipeline**

| **Type**                                                                | **Role**                                                                         | **Example**                                                     |
|-------------------------------------------------------------------------|----------------------------------------------------------------------------------|-----------------------------------------------------------------|
| [**Collection Pipe**](Types%20of%20Pipes/Collection%20Pipe.md)          | **Gathers raw data** and **can do basic transformation** (like adding metadata). | [Beats](../../Tools/Beats/Beats.md)                             |
| [**Transport Pipe**](Types%20of%20Pipes/Transport%20Pipe.md)            | **Streams** data **without modification**. _(Temporary delivery, not storage.)_  | [Redis Streams](../../Tools/Redis%20Streams/Redis%20Streams.md) |
| [**Transformation Pipe** ](Types%20of%20Pipes/Transformation%20Pipe.md) | **Streams and modifies** data _(parses, filters, adds metadata)._                | [Logstash](../../Tools/Logstash/Logstash.md)                    |
| [**Processing Pipe**](Types%20of%20Pipes/Processing%20Pipe.md)          | **Streams and processes** data _(analyzes, aggregates, computes)._               | [Flink](../../Tools/Flink/Flink.md)                             |


