# Day 17: Creating a Dashboard for RDP Activity

## 1. Introduction

**Goal**: Learn how to create a dashboard focusing on RDP activity generated from a Windows server and table visualization.

**Task**: Create a map similar to the SSH Authentications map, but focusing on Windows Server authentication attempts related to RDP and create table visualization.

## 3. Steps to Create the Dashboard


**Navigate to Elastic web GUI**: Click on the hamburger icon and select Maps.

**Query Setup**: Use the saved search query for event code `4625` (failed logins) and agent name.

```
event.code:4625 AND agent.name:"MyDFIR-WIN-wahab"
```

**Add Layer**: Click on Add Layer, select Choropleth, and choose World Countries for the EMS boundary.

**Data View**: Select data view and join field ``source.geo.country_iso_code``.

**Country ISO Code**: Use the country ISO code for the abbreviation.

**Save Map**: Title it "RDP Failed Authentication".

**Add to Dashboard**: Select the existing dashboard `MyDFIR-RDP Authentication Activity`

## 4. Creating a Query for Successful Authentications 

### Modify Query

**Event Code**: Change from `4625` to `4624` for successful logins.
**Logon Types**: Focus on logon types `10` and `7`.

```
event.code:4624 and (winlog.event_data.LogonType:10 or winlog.event_data.LogonType:"7") and agent.name:"MyDFIR-WIN-wahab"
```

### Save and Add to Dashboard

**Save Query**: Title it `RDP Successful Authentication`.

**Duplicate Dashboard**: Duplicate the existing dashboard and update the query. and name of the new map `RDP Successful Authentication` and replace the query with the modified query.
## 5. Enhancing the Dashboard

### Adding a Table

**Fields to Include**: Time, source IP, username, and country.

**Use Queries**: use saved search  queries for both failed and successful activities.

**Add Table to Dashboard**: Include the table with usernames, source IPs, and country names for quick reference.

## 6. Creating Visualizations

### 6.1 SSH Failed Authentications Table

**Create Visualization**: Click on Create Visualization and select Table.

**Query**

```
system.auth.ssh.event : * and agent.name:"MyDFIR-Linux-Wahab" and system.auth.ssh.event : "Failed"
```

**Add Fields**: Include timestamp, source IP, username, and country name.

**Configure Rows**: Set top values to 10 and uncheck "group remaining values as other".

**Sort Records**: Sort by count of records in descending order.

**Save Visualization**: Title it `SSH Failed Authentications (Table)`

### 6.2 SSH Successful Authentications Table

**Duplicate Visualization**: Duplicate the SSH failed Authentications table.

**Update Title**: Change to `SSH Sucessful Authentications (Table)`.

**Modify Query**: Update the query to focus on successful authentications.

```
system.auth.ssh.event : * and agent.name:"MyDFIR-Linux-Wahab" and system.auth.ssh.event : "Accepted"
```

### 6.3 RDP Failed Authentications Table

**Duplicate Visualization**: Duplicate the SSH failed Authentications table.

**Update Title**: Change to `RDP Failed Authentications`.

**Modify Query**: Update the query to focus on RDP failed authentications.

```
event.code:4625 AND agent.name:"MyDFIR-WIN-wahab"
```

### 6.4 RDP Successful Authentications Table

**Duplicate Visualization**: Duplicate the RDP failed Authentications table.

**Update Title**: Change to `-RDP Successful Authentications`.

**Modify Query**: Update the query to focus on RDP successful authentications.

```
event.code:4624 and (winlog.event_data.LogonType:10 or winlog.event_data.LogonType:"5") and agent.name:"MyDFIR-WIN-wahab"
```

## 7. Finalizing the Dashboard

**Review and Save**: Ensure all visualizations are correctly configured and save the dashboard.

**Summary**: The dashboard now includes visualizations for both SSH and RDP failed and successful authentications.

