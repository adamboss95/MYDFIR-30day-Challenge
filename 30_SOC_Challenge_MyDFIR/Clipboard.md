# Clipboard

## Elastic Security Configuration

elastic password 

```
DRk2C0h0I7jcb5fnWQHA
```

```
Selecting previously unselected package elasticsearch.

(Reading database 121223 files and directories currently installed.)

Preparing to unpack elasticsearch-8.17.2-amd64.deb

Creating elasticsearch group... OK

Creating elasticsearch user... OK

Inpacking elasticsearch (8.17.2)

etting up elasticsearch (8.17.2)

Security autoconfiguration information

Authentication and authorization are enabled.

TLS for the transport and HTTP layers is enabled and configured.

The generated password for the elastic built-in superuser is FsYu+WCAc10c5EmpbSF

If this node should join an existing cluster, you can reconfigure this with '/usr/share/elasticsearch/bin/elasticsearch-reconfigure-node-enrollment-token <token-here>'

after creating an enrollment token on your existing cluster.

You can complete the following actions at any time:

Reset the password of the elastic built-in superuser with /usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic'.

Generate an enrollment token for Kibana instances with '/usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s kibana'

Generate an enrollment token for Elasticsearch nodes with /usr/share/elasticsearch/bin/elasticsearch-create-enrollment-token -s node

### NOT starting on installation, please execute the following statements to configure elasticsearch service to start automatically using systemd

sudo systemctl daemon-reload

sudo systemctl enable elasticsearch.service

### You can start elasticsearch service by execut ing
```

## Enrollment Token

```
root@Challenge-ELK:/usr/share/elasticsearch/bin# ./elasticsearch-create-enrollment-token --scope kibana
```

```eyJ2ZXIiOiI4LjE0LjAiLCJhZHIiOlsiNDUuNzcuMjUwLjE3MTo5MjAwIl0sImZnciI6IjA0YzExZWI2M2RjMjVmNTIyNWFiZGEzYzUxOTAzYTFmMGNhNzIxOGE5MjE5ZjRkNjk2MmFlZWIwN2Y1MzdkMDMiLCJrZXkiOiJ4OFFiTTVVQlpETGhlZmZpMXd5Nzo3ZDlFcG52VFRWaVhzY04tcXU4elpBIn0=```

## Kibaana Encryption Key

xpack.encryptedSavedObjects.encryptionKey: d9fcd01abd54a5a5ea74ff28d0a5d204
xpack.reporting.encryptionKey: cc5a8ed7c9dcf34e93175ac29d2f6c63
xpack.security.encryptionKey: df49dc71246c27a293fed3e8af8f6850