_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---

![img](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ0_Bn1LnLXS9GPLGitGTwo8eQZQt5UZfVUHQ&s)

---

### Content

- [What is Logstash?](#what-is-logstash)
- [Type](#type)
- [Reason](#reason)
- [Must Have?](#must-have)
- [Examples of pipelines with Logstash](#examples-of-pipelines-with-logstash)
- [Example Logstash Configuration](#example-logstash-configuration-logstashconf)
- [Level in pipeline hierarchy](#level-in-pipeline-hierarchy)

---


### **What is Logstash?**

- It is a **data processing pipeline** that collects, transforms, and routes data.
- Supports **parsing, filtering, and enriching** data before forwarding.

Mostly

- **Logstash** is used like a **pipe** before storage or Kafka.
- It **filters, transforms, and directs** data between Kafka and storage.
- Can take data from multiple sources, clean it, and send it where needed.

🡆 **Input Sources:** Kafka, Beats, raw logs, HTTP, databases.  
🡆 **Output Destinations:** Kafka, Elasticsearch, ClickHouse, other storages.

---

### **Type**

Many (one) to many.

---

### **Reason**

Logstash acts as a **processing pipe**, sitting between **Kafka (event stream)** and **Elasticsearch (storage & search
engine)**.  
It ensures that **Elasticsearch can properly accept logs** from Kafka.

---

### **Must have?**

No, but recommended when **data transformation or enrichment** is needed.

---

### **Examples of pipelines with Logstash**

- **Logstash + Kafka → Elasticsearch** (Processing logs before storage).
- **Logstash + Beats → Kafka** (Pre-processing log data before streaming).

---

### **Works With:**

🡆 **Input Sources:** Kafka, Beats, File systems, Redis Streams, Databases, Syslog, HTTP, and more.  
🡆 **Output Destinations:** Elasticsearch, Kafka, Relational/NoSQL Databases, S3, Email, and more.

---

### **Example Logstash Configuration (`logstash.conf`)**

```plaintext
input {
  kafka {
    bootstrap_servers => "kafka:9092"
    topics => ["logs"]
    codec => "json"
  }
}

output {
  elasticsearch {
    hosts => ["http://elasticsearch:9200"]
    index => "logstash-logs-%{+YYYY.MM.dd}"
  }
}
```

---

### Level in pipeline hierarchy

2  