# Day 22: Creating Alerts and Dashboards for Mythic Activity

## 1. Introduction

**Goal**: Create an alert and dashboard to detect Mythic activity generated on Day 21.

## 2. Setting Up the Alert

**Steps**:

**Access Elastic Web GUI**:
   
- Click on the hamburger icon and select "`Discover`".
- Create a new search to reset the view.

**Query for Mythic C2 Activity**:
   
- Search for the binary `svchost-Wahab.exe`.
- Adjust the time range to 30 days to capture all relevant events.
- Sort events from old to new.

**Identify Relevant Events**:
   
- Look for events with event code 11 (file creation).
- Note the target file name, username, and process GUID.


**Focus on Process Create Events**:
   
- Change the query to look for event code 1 (process create).
- Copy the SHA-1 hash and use VirusTotal for open-source intelligence (OSINT) checks.

**Create Alert Criteria**

- Use the original file name `apollo.exe` and `SHA-256` hash in the query.
- Ensure the query only triggers on process create events.

```
event.code:1 and (winlog.event_data.OriginalFileName:"Apollo.exe" or   winlog.event_data.Hashes:*4B9414B7F5C3EB1B83ED8D1B98A0C298229977A67BE784DE5E09D2D647D75152*)
```

**Save the Search**

- Save the search as `MyDFIR Mythic Apollo Process Create`.
## 3. Building the Alert

**Steps**:

**Create a New Rule**:
   
- Go to `Detection Rules` under the security section.
- Create a new rule using a custom query.
- Paste the saved query and specify required fields like
	- `timestamp`
	- `winlog.event_data.User`
	- `winlog.event_data.ParentImage`
	- `winlog.event_data.ParentCommandLine`
	- `winlog.event_data.Image`
	- `winlog.event_data.CommandLine`
	- `winlog.event_data.CurrentDirectory`
	- 

**3. Finalize and Enable Rule**:
 
- Name the rule `MyDFIR Mythic Apollo Process Create Detected`
- Set severity to critical and configure the rule to run every 5 minutes.
- Enable the rule.

## 4. Creating the Dashboard

**Steps**:

**1. Define Dashboard Panels**:

- Process creates `event ID 1` for PowerShell, CMD, and rundll32.
- External network connections `event ID 3`.
- Windows Defender activity `event ID 50001`.

**2.Create Queries for Panels**:
   
**a. Process Creates**:

*Query:* 

```
event.code:1 and event.provider:"Microsoft-Windows-Sysmon" and  (Powershell or cmd or rundll32)
```

*Fields to Include:*

- `timestamp`
- `winlog.event_data.User`
- `winlog.event_data.ParentImage`
- `winlog.event_data.ParentCommandLine`
- `winlog.event_data.Image`
- `winlog.event_data.CommandLine`
- `winlog.event_data.CurrentDirectory`

**External Network Connections**:

*Query:*

```
event.code:3 AND event.provider:"Microsoft-Windows-Sysmon" AND winlog.event_data.Initiated:true and not winlog.event_data.Image:*MsMpEng.exe
```

*Fields to Include:*

- `winlog.event_data.Image`
- `winlog.event_data.SourceIp`
- `winlog.event_data.DestinationIp`
- `winlog.event_data.DestinationPort`

**Windows Defender Activity**:

 *Query:* 

```
event.code:5001 and event.provider:"Microsoft-Windows-Windows Defender" 
```

*Fields to Include:*

- `host.hostname`
- `winlog.event_data.Product Name`
- `event.code`
 
**3. Build Dashboard**:

- Go to "Dashboards" and create a new dashboard.
- Add visualizations for each query.
- Add the relevant field for each and save.
## 6. Finalizing the Dashboard

**Steps**:

**Save and Title the Dashboard**:
    
- Name the panels appropriately: 
- `Process Created (PowerShell, CMD, rundll32)`
- `Process Initiated Network Connections`
- `Microsoft Defender Disabled`
- Save the dashboard as `MyDFIR Suspicious Activity`

[Day 23 Introduction to Ticketing Systems](Day%2023%20Introduction%20to%20Ticketing%20Systems.md)