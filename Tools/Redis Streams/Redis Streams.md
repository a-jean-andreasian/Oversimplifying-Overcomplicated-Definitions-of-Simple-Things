_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---

# Redis streams


---

### Content

- [What is Redis Streams?](#what-is-redis-streams)
- [Difference of Redis and Redis Streams](#difference-of-redis-and-redis-streams)
- [Redis Streams in the Ecosystem](#redis-streams-in-the-ecosystem)
- [When does Redis Streams fit?](#when-does-redis-streams-fit)
- [Comparison with Kafka](#comparison-with-kafka)
- [How it Works with Logstash?](#how-it-works-with-logstash)

---



### What is Redis Streams?

- **Redis** is a **key-value store** used for caching, fast lookups, and real-time data.
- **Redis Streams** is **designed for event streaming**, working similarly to **Kafka**, but within Redis.
    - **Redis Streams is NOT a replacement for Kafka**, but can be used when low-latency event processing is required.

- It allows *multiple consumers* to read events in order and process them efficiently.
- It is used to classify as a [transport pipe.](../../Data/Pipe/Types%20of%20Pipes/Transport%20Pipe.md)


🔥 **Best used when logs need to be processed in near real-time before reaching Elasticsearch.**

---

### Difference of Redis and Redis Streams

The main difference between **Redis** and **Redis Streams** is how they handle data:

| Feature                | Redis (Standard)                                        | Redis Streams                                             |
|------------------------|---------------------------------------------------------|-----------------------------------------------------------|
| **Data Structure**     | Key-value store                                         | Log-like append-only stream                               |
| **Purpose**            | Caching, real-time storage, pub/sub, session management | Event streaming, message queues                           |
| **Persistence**        | Optional (RDB, AOF)                                     | Yes (if configured)                                       |
| **Ordering**           | No strict ordering                                      | Guaranteed ordering                                       |
| **Consumption Model**  | Direct lookup (key-based)                               | Consumer groups (like Kafka)                              |
| **Multiple Consumers** | No (unless using Pub/Sub)                               | Yes (via consumer groups)                                 |
| **Use Cases**          | Caching, session store, real-time leaderboard           | Log processing, event-driven architecture, data pipelines |

### **Redis Streams in the Ecosystem**

#### **Relation to Kafka, Logstash, and Elasticsearch**

- **Redis Streams** is a message broker like **Kafka**, but with a simpler, in-memory architecture.
- It can act as an **event queue** before data is processed by **Logstash** or stored in **Elasticsearch**.

---

### **When does Redis Streams fit?**

🡆 **As an Input Source** → Logstash can consume events from Redis Streams.  
🡆 **As an Event Buffer** → Acts as a temporary storage before Kafka or Logstash.  
🡆 **For Real-Time Processing** → Can be read by microservices before logs reach Elasticsearch.

---

### **Comparison with Kafka**

| Feature            | Redis Streams                    | Kafka                          |
|--------------------|----------------------------------|--------------------------------|
| **Persistence**    | In-memory (can persist to disk)  | Disk-based, durable storage    |
| **Scalability**    | Single-node or small clusters    | Horizontally scalable clusters |
| **Data Retention** | Configurable (limited by memory) | Long-term log storage          |
| **Use Case**       | Low-latency event processing     | Large-scale event streaming    |

---

### **How it Works with Logstash?**

📌 **[Logstash](../Logstash/Logstash.md) can pull data from Redis Streams and process it before sending it to Elasticsearch.**

**Example Logstash Input Configuration for Redis Streams**

```plaintext
input {
  redis {
    data_type => "stream"
    key => "log_stream"
    host => "redis"
    port => 6379
  }
}
```

---