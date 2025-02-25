# Day 02: ELK Stack – Elasticsearch, Logstash, and Kibana

## Introduction

*ELK Stack:* A set of tools for log management and analysis.

*Purpose:* Centralized logging, security monitoring, and data visualization.

*Tools:*
- **Elasticsearch (E)** – Stores and searches logs.
- **Logstash (L)** – Collects, processes, and forwards logs.
- **Kibana (K)** – Web UI for querying and visualizing logs.

## Elasticsearch

**Database** for storing logs (Windows Event Logs, Syslogs, Firewall Logs, etc.).
Uses **Elasticsearch Query Language (ESQL)** – beginner-friendly.
Supports **REST APIs & JSON** for interaction - Queries can also be made using Kibana’s web console.

## Logstash

**Ingests, transforms, filters, and sends logs to Elasticsearch.**

*Works with data collection tools:*
- **Beats:** Lightweight agents for specific log types:
    - Filebeat (logs)
    - Metricbeat (metrics)
    - Packetbeat (network)
    - Winlogbeat (Windows logs)
    - Auditbeat (audit data)
    - Heartbeat (uptime monitoring)
-  **Elastic Agent:** A unified agent replacing multiple Beats.

**Filtering:** Logstash can filter logs based on criteria (e.g., only logins with Event ID **4624**).

**Parsing:** Extracts key fields from logs (e.g., `SRC_IP` as the source IP address).

## Kibana

Web console for searching and analyzing logs.

*Features:*
- **Visualizations (Kibana Lens)** – Drag & drop for dashboards.
- **Discover Tab** – Log searches using ESQL.
- **Machine Learning** – Anomaly detection.
- **Elastic Maps** – Geospatial analysis.
- **Alerting & Reporting** – Automated alerts based on log data.

## Comparison with Splunk

*Elasticsearch* = Splunk Indexer

*Logstash* = Splunk Heavy Forwarder

*Kibana* = Splunk Web UI (Search Head)

*Beats/Agents* = Splunk Universal Forwarders

## Benefits of ELK Stack

1. **Centralized Logging** – Compliance and incident response.
2. **Flexible Log Ingestion** – Supports multiple input methods.
3. **Visualizations & Dashboards** – Useful for monitoring & reporting.
4. **Scalability** – Can expand based on needs & budget.
5. **Strong Ecosystem & Community Support** – Many integrations available.

## Key Takeaway

- ELK Stack is widely used for **SIEM, monitoring, and log analysis**.
- Many **commercial SIEMs** are built on ELK, making it a valuable skill.
- Recommended for **SOC analysts** to learn for better career prospects.

[Day 03 Setting Up an Elasticsearch Instance](Day%2003%20Setting%20Up%20an%20Elasticsearch%20Instance.md)
