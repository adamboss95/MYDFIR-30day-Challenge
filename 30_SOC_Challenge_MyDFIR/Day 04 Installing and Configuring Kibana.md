# Day 04 Installing and Configuring Kibana

## 1. Introduction

- Goal: Set up and install a Kibana instance.
    
- Visit [elastic.co/downloads/kibana](https://www.elastic.co/downloads/kibana) to download Kibana.

## 2. Download and Install Kibana

Select `Deb x86_64` version (as of recording, version 8.15).

Copy the download link and use `wget` to download it in the SSH session:
   
```
wget https://artifacts.elastic.co/downloads/kibana/kibana-8.17.2-amd64.deb
```

Verify the download:

```
 ls
```

Install Kibana:
  
```
dpkg -i kibana-8.17.2-amd64.deb
```
## 3. Configure Kibana

Open the configuration file using `nano`:
  
```
sudo vim /etc/kibana/kibana.yml
```

Modify the following lines:

```
server.port: 5601
server.host: <your_public_IP>
```

Save and exit (`Esc`,`:wq!`) 

## 4. Start and Enable Kibana Service

```
systemctl daemon-reload
systemctl enable kibana.service
systemctl start kibana.service
systemctl status kibana.service
```
## 5. Generate Enrollment Token

Navigate to the Elasticsearch binary directory:
  
```
cd /usr/share/elasticsearch/bin
```
  
Generate the token: 

```
./elasticsearch-create-enrollment-token --scope kibana
```

Copy the generated token for later use.

## 6. Access Kibana Web Interface

Open a browser and go to:

```
http://<your_public_IP>:5601
```

If `Connection Timed Out` occurs:

- Allow necessary ports in the firewall:
 
```
ufw allow 5601
```
 
- Modify `SOC-Simulation` cloud firewall rules to allow ports `1-65535` from your IP.
## 7. Enter Enrollment Token and Login

Paste the copied enrollment token in the web interface.

**Generate verification code in Terminal:**

Navigate to the Kibana binary directory

```
cd /usr/share/kibana/bin
```

Generate the verification code 

```
./kibana-verification-code
```

Enter the displayed verification code.

**Login**
  
Use `elastic` as the username and retrieve the password from the installation log or reset it 

```
cd /usr/share/elasticsearch/bin
```
   
```
./elasticsearch-reset-password -u elastic
```
  
Login to Kibana.
## 8. Configure Encryption Keys

Navigate to the Kibana binary directory

```
cd /usr/share/kibana/bin
```

**Generate encryption keys:**

```
./kibana-encryption-keys generate
```
  
Copy the generated keys and store them.

**Add them to the Kibana keystore:**

Add the key one by one by running binaries and then giving values for each of the key 

```
./kibana-keystore add xpack.encryptedSavedObjects.encryptionKey
```

Paste value

```
./kibana-keystore add xpack.reporting.encryptionKey
```

Paste value

```
./kibana-keystore add xpack.security.encryptionKey
 ```

Paste value
 
**Restart Kibana:**

```
systemctl restart kibana
```

Login again to confirm settings.

[Day 05 Setting Up a Windows Server in the Cloud](Day%2005%20Setting%20Up%20a%20Windows%20Server%20in%20the%20Cloud.md)