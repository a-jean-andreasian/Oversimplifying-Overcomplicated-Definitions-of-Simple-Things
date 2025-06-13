_This paragraph is part of the book *Oversimplifying Overcomplicated Definitions of Simple Things* by Armen-Jean Andreasian._

---
# Beats


### What are Beats?

- [Beats agents](https://www.elastic.co/docs/reference/beats) are [transport pipes](../../Data/Pipe/Types%20of%20Pipes/Transport%20Pipe.md). 
- They are lightweight agents that collect and ship data.
- **Optionally** they can do basic transformation (like adding metadata).

---
### Type

One to one.

---
### 🡆 **Reason**

Beats agents are like small streams, **feeding data into _Kafka_ (the main river)**, or **directly
to _Logstash_ (the processing pipe)**.

---

### Must have?

No.

---
### Examples

* **Filebeat** – Collects and ships log files from the filesystem.
  - *Focus:* Log files

* **Auditbeat** – Collects audit data from the Linux Audit Framework and monitors file integrity.
  - *Focus:* Security and audit data

* **Packetbeat** – Captures and analyzes network packets, providing application-level network monitoring.
  - *Focus:* Network traffic

* **Metricbeat** – Collects system and service-level metrics (CPU, memory, disk, etc.).
  - *Focus:* System and service metrics

* **Winlogbeat** – Collects and ships Windows Event Logs.
  - *Focus:* Windows logs

---
### **Works With:**

🡆 **Input Sources:** N/A (Beats collect data themselves).  
🡆 **Output Destinations:** Kafka, Logstash.

---

- Level : 1