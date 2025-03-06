 
# Day 20: Setting Up Mythic C2 Instance

## Introduction

This session covers setting up **Mythic C2**, a Command and Control (C2) framework.

Uses **Vultr Cloud Provider** for hosting the Mythic C2 instance.
  
**Kali Linux** is also installed for penetration testing.
## Deploying a Server on Vultr

1. **Login** to Vultr and click on **Deploy New Server**.
   
2. Select:

- **Cloud Compute** (Shared CPU)
- **Location:** Singapore
- **OS:** Ubuntu (4GB RAM)
- Disable **Auto Backups & IPv6**
- Set **hostname:** `MyDFIR-Mythic`

3. Deploy the server. 

## Installing Kali Linux

1. **Download Kali Linux** from kali.org.
2. Select **Virtual Machine** version (VMware used in this setup).
3. Extract the downloaded file using **7-Zip**.
4. Locate and open the **.vmx** file in VMware Workstation.
5. Power on the **Kali VM**.

## Setting Up Mythic C2

**Access the Vultr Instance**

Open PowerShell and SSH into the Vultr Mythic Mythic:

```
ssh root@<MyDFIR_mythic_server_ip>
```

Update & Upgrade System
 
```
apt-get update && apt-get upgrade -y
```

**Install Dependencies**
 
Install Docker & Make:

```
 apt-get install docker-compose make -y
```
 
Clone & Install Mythic

```
git clone https://github.com/its-a-feature/Mythic.git
cd Mythic
./install_docker_ubuntu.sh
```

Start Mythic (To solve docker issue restart the docker)

 ```
make
./mythic-cli start
```  

## Fixing Docker Issues

If Docker fails to start, restart the service:

```
systemctl restart docker
```
 
Verify Docker status:

```
systemctl status docker
```

## Configuring Firewall

**Create a Firewall Group** `MyDFIR-Mythic-Firewall`on Vultr.
   
**Allow TCP Traffic** from trusted IPs only:

- TCP **1-65535** (Source: Personal IP)

- TCP **1-65535** (Source: `MyDFIR-WIN-wahab`)

- TCP **1-65535** (Source: `MyDFIR-Linux-Wahab`)

Apply `MyDFIR-Mythic-Firewall` to Mythic Server

## Accessing Mythic C2 Web Interface

Copy the Mythic **server's public IP**.

Open a browser and navigate to:

```
https://<Mythic-server_ip>:7443
```

**Login Credentials**:
 
Default **Username:** `mythic_admin`   

Password stored in the Mythic Server `.env` file:

```
cat .env
```

**Change Operation Name**

Default: `operation-chimera`

Can be renamed (e.g., `operation-kratos`).

## Mythic C2 Dashboard Overview

**Callbacks:** List of connected agents.
   
**Payloads:** Preconfigured exploits.
   
**File Hosting:** Upload/download files.

**Artifacts:** Keylogging, screenshots, credentials, reports.
   
**MITRE ATT&CK Mapping:** Identify attack techniques.
   
**Tags:** Categorize targets.
   
**Dark Mode:** Available for UI preference.
