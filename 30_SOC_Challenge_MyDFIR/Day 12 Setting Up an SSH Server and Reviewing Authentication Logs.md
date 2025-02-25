# Day 12: Setting Up an SSH Server and Reviewing Authentication Logs

## 1. Introduction

**Goal**: Set up an SSH server in the cloud and review authentication logs in real time.

## 2. Set Up SSH Server

**Steps**:

1. Go to vulture.com and sign in.
2. Click on **Deploy** > **Deploy New Server**.
3. Select **Cloud Compute** > **Shared CPU**.
4. Choose **Singapore** and **Ubuntu 24.04**.
5. Select **1 CPU and 1 GB of memory**.
6. Disable auto backups and IPv6.
7. Name the server `Challenge-Linux-Steve`.
8. Click on **Deploy Now**.

## 3. Access the Server

**Steps**:
 
1. Wait for the server to be ready.
2. Open a PowerShell session.
3. SSH into the server: `ssh root@<IP_address>`.
4. Accept the connection and enter the password.

## 4. Update and Upgrade Repositories

**Commands**:

1. `apt-get update`
2. `apt-get upgrade -y`

## 5. Review Authentication Logs

**Steps**:

1. Navigate to the log directory: `cd /var/log`.
2. List the logs: `ls`.
3. View the authentication log: `cat auth.log`.

## 6. Filter Authentication Logs

**Commands**:

1. Filter for failed attempts: `grep -i failed auth.log`.
2. Filter for root user: `grep -i root auth.log`.
3. Extract IP addresses using cut command:

```
grep -i failed auth.log | grep -i root auth.log | cut -d ' ' -f 9 auth.log
````