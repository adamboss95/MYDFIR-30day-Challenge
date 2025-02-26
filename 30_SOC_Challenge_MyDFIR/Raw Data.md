### Default port assignments

When Elasticsearch or Fleet Server are deployed, components communicate over well-defined, pre-allocated ports. You may need to allow access to these ports. Refer to the following table for default port assignments:

| Component communication        | Default port |
| :----------------------------- | :----------- |
| Elastic Agent → Fleet Server   | 8220         |
| Elastic Agent → Elasticsearch  | 9200         |
| Elastic Agent → Logstash       | 5044         |
| Elastic Agent → Kibana (Fleet) | 5601         |
| Fleet Server → Kibana (Fleet)  | 5601         |
| Fleet Server → Elasticsearch   | 9200         |
| RDP Default port               | 3389/TCP     |
|                                |              |
