_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean
Andreasian._

---

# Transformation  vs. Processing

Long story short:
- **Transformation**: Prepares data for storage or further processing.  
  *Example: Parsing, filtering, enriching (with metadata).*


- **Processing**: Performs real-time computations and deeper analysis.  
  *Example: Detecting anomalies in event streams, calculating rolling metrics.*

---

| Feature     | **Transformation (Logstash)**                    | **Processing (Flink)**                                                 |
|-------------|--------------------------------------------------|------------------------------------------------------------------------|
| **Purpose** | Modifies, cleans, or formats data                | Performs computations, aggregations, and real-time analysis            |
| **Scope**   | Applies filters, parses logs, enriches data      | Executes business logic, joins data streams, and performs calculations |
| **Latency** | Works on batches or near real-time               | Works on continuous data streams (millisecond-level latency)           |
| **Example** | Converting a timestamp format, extracting fields | Detecting fraud in transactions, computing moving averages             |


So, while **Logstash "transforms and routes" data**, **Flink actually "processes" it** to derive new insights.

---
