# Day 09: Installing and Configuring Sysmon

## 1. Introduction

**Goal**: Install Sysmon on Windows server and confirm it generates logs.

## 2. Connect to Windows Server 

**Steps**:

  1. Use Remote Desktop to connect to the Windows server `Challenge-WIN-Haji` (IP and credentials provided).
  2. Open Microsoft Edge and download Sysmon.

## 3. Download Sysmon

**Steps**:

Google "Sysmon" and select the first link (learn.microsoft.com).

Directly download form this link [Download Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

## 4. Extract Sysmon

**Steps**:

1. Navigate to the Downloads folder.
2. Right-click Sysmon and select "Extract All".
3. Confirm three binaries are extracted.

## 5. Download Configuration File

- **Steps**:

1. Google "Sysmon Olaf configuration" and select the GitHub link.
2. In GitHub repository select the [sysmonconfig.xml](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml)
3. Download the [sysmonconfig.xml](https://github.com/olafhartong/sysmon-modular/blob/master/sysmonconfig.xml) file.
4. Save the configuration file in the Sysmon directory.

## 6. Open PowerShell

**Steps**:

1. Open PowerShell as Administrator.
2. Navigate to the Sysmon directory using `cd`.

## 7. Install Sysmon

**Steps**:

1. Run the command

```
./sysmon64.exe -accepteula -i sysmonconfig.xml
```

1. Confirm Sysmon service is running in Services.
2. Check Event Viewer for Sysmon logs.
	- Expand **Applications and Services Logs**.
	- Find the **Microsoft > Windows > Sysmon > Operational** log and view the Sysmon log entries.
## 8. Verify Installation

**Steps**:

1. Open Event Viewer.
2. Navigate to Applications and Services Logs > Microsoft > Windows > Sysmon > Operational.
3. Confirm that logs are generated.

[Day 10 Ingesting Sysmon and Microsoft Defender Logs into Elasticsearch](Day%2010%20Ingesting%20Sysmon%20and%20Microsoft%20Defender%20Logs%20into%20Elasticsearch.md)