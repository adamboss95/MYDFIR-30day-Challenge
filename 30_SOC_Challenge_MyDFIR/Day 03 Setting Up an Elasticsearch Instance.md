# Day 03: Setting Up an Elasticsearch Instance

## 1. Creating a Virtual Private Cloud (VPC)

- Sign up on **[Vultr](https://www.vultr.com/)** (use $300 credit if available).
- Navigate to **Products > Network > VPC 2.0**.
- Click **"Add VPC"** and configure:
    - **Location**: Ensure all VMs are in the same location (e.g., Singapore).
    - **IPv4 Range**: Set `172.31.0.0/20`.
    - **Name**: Example: `MyDFIR-SOC-Challenge`.
    - Click **"Add Network"**.

## 2. Deploying the Virtual Machine (VM)

- Click **"Deploy"** > **"Deploy New Server"**.
- **Location**: Same as VPC (e.g., Singapore).
- **Image**: **Ubuntu** (64-bit).
- **Server Size**: **4 vCPUs, 16GB RAM**.
- **VPC Selection**: Choose the `MyDFIR-SOC-Challenge`.
- **Hostname**: Example: `MyDFIR-ELK`.
- Click **"Deploy"** and wait until status is **Running**.

## 3. Connecting to the VM

Open **PowerShell** and use SSH:

```
ssh root@<your-public-IP>
```
    
Accept the connection (`yes`) and enter the copied password.

**Update the system**:
   
```
apt-get update && apt-get upgrade -y
```

## 4. Installing Elasticsearch

Download Elasticsearch:
 
```
wget <ElasticSearch-Deb-Package-URL>
```

```
wget https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-8.17.2-amd64.deb
```

Install:
   
```
dpkg -i elasticsearch-<version>.deb
```

```
dpkg -i elasticsearch-8.17.2-amd64.deb
```

**Save Security Auto-Configuration Details** (contains superuser credentials).

### Reset Elasticsearch Password (if needed)

```
/usr/share/elasticsearch/bin/elasticsearch-reset-password -u elastic
```

## 5. Configuring Elasticsearch

Open the configuration file:

```
nano /etc/elasticsearch/elasticsearch.yml
```


Modify the following settings:

**Network Host**:

uncomment the network host line and edit.

```
network.host: <public-IP>
```

```
network.host: 45.77.250.171
```

**HTTP Port** 

uncomment the port line also. (leave as default `9200`).

Save and exit (`Ctrl + X`, `Y`, `Enter`).


## 6. Setting Up a Firewall

Go to **Vultr > VM Settings > Firewall**.

Click **"Manage"** > **"Add Firewall Group"**.

-  Name: `30-Day-MyDFIR-SOC-Challenge`.
- Restrict SSH to your IP only.

Assign the firewall to the VM under **Compute > VM > Settings > Firewall **.
- Select the new added firewall & update the firewall setting.
## 7. Starting Elasticsearch Service

Run the following commands:
   
```
systemctl daemon-reload 
systemctl enable elasticsearch.service
systemctl start elasticsearch.service
```

**Check Status**:
   
```
systemctl status elasticsearch.service
```

Ensure it is **active and running**.

[Day 04 Installing and Configuring Kibana](Day%2004%20Installing%20and%20Configuring%20Kibana.md)
