# Day 10: Ingesting Sysmon and Microsoft Defender Logs into Elasticsearch

## 1. Introduction

**Goal**: Ingest Sysmon and Microsoft Defender event logs from Windows Server into Elasticsearch.
## 2. Log into Elasticsearch

**Steps**:

1. Log into your Elasticsearch instance.
2. Click on the **Add Integrations** button on the homepage.

## 3. Add Sysmon Integration

**Steps**:

1. Search for "Windows" and select **Custom Windows Event Log**.
2. Click on **Add Custom Windows Event Logs**.
3. Name the integration (e.g., `Challenge-Win-Sysmon`).
4. Description: `Collect Sysmon logs from windows hosts`.
5. Obtain the channel name from Event Viewer on the Windows server:
    - Open Event Viewer.
    - Navigate to Applications and Services Logs > Microsoft > Windows > Sysmon > Operational.
    - Right-click **Operational** and select **Properties**.
    - Copy the full name (`Microsoft-Windows-Sysmon/Operational`).
6. Paste the channel name into the integration setup.
7. Add the integration to an existing host and select the agent policy (e.g., `MyDFIR-Windows-Policy`).
8. Click on **Save and Continue** and then **Save and Deploy Changes**.

## 4. Add Microsoft Defender Integration

**Steps**:

1. Click on **Add Custom Windows Event Logs**.
2. Name the integration (e.g., `Challenge-Win-Defender`).
3. Description: `Collect Windows Defender logs from widows for Event ID 1116,1117 & 5001`
4. Obtain the channel name from Event Viewer on the Windows server:
    - Navigate to Applications and Services Logs > Microsoft > Windows > Windows Defender > Operational.
    - Right-click **Operational** and select **Properties**.
    - Copy the full name (`Microsoft-Windows-Windows Defender/Operational`).
5. Paste the channel name into the integration setup.
6. Specify event IDs to include (e.g., 1116, 1117, 50001).
7. Add the integration to an existing host and select the agent policy (e.g., `my defer Windows policy`).
8. Click on **Save and Continue** and then **Save and Deploy Changes**.
## 5. Verify Log Ingestion

**Steps**:

1. Click on the hamburger icon and select **Discover**.
2. Search for "sysmon" and check for results.
3. If no results, troubleshoot by:
    - Checking Integrations under Management.
    - Ensuring the correct field name (e.g., `winlog.event_id`).
    - Restarting the Elastic Agent service on the Windows server.
    - Allowing incoming connections to port 9200 on the Elasticsearch instance.
4. Refresh the page and check for logs again.

## 6. Troubleshooting

**Steps**:

1. If CPU and memory values are "N/A" in agent details, it indicates connectivity issues.
2. Allow incoming connections to port 9200 on the Elasticsearch server.
3. Refresh the agent details page and check for updated logs.

