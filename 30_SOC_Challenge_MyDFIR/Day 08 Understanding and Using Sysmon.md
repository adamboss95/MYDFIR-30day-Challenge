# Day 08: Understanding and Using Sysmon

## 1. Introduction

**Goal**: Learn about Sysmon and its capabilities.
## 2. Importance of Endpoint Visibility

**Visibility**: Crucial for investigating potential compromises.

**Default Logging**: Enabled by default on Windows but insufficient.

**Solution**: Configure auditing settings or install Sysmon.
## 3. What is Sysmon?

**Tool**: Free Microsoft tool, part of the Sysinternals suite.

**Telemetry**: Monitors events like process creations, network connections, file creations.

**Customization**: Uses a configuration file to control logged events.

**Version**: Latest version is 15.15 with 30 event IDs.

## 4. Sysmon Capabilities

**Process Creations**: Logs command lines for parent and current processes.

**Hashes**: Records process hashes for additional context.

**Process GUID**: Correlates events for a bigger picture.

**Network Connections**: Logs source and destination IPs, ports, and involved processes (disabled by default).
## 5. Important Event IDs

**Event ID 1**: Process Creation
- Tracks new processes and command lines.
- Logs file hashes for additional context.

**Event ID 3**: Network Connections
- Disabled by default, must be enabled via configuration file.
- Tracks network connections, source and destination IPs, ports.

**Event IDs 6, 7, 8**: Driver, Image Load, Create Remote Thread
- Identifies potential defense evasion techniques like process injection.
- Event ID 7 (Image Load) is disabled by default.

**Event ID 10**: Process Access
- Common for detecting credential access attempts on LSASS process.

**Event ID 22**: DNS Query
- Tracks domain requests, useful for identifying compromised endpoints.

[Read More About Sysmon](https://learn.microsoft.com/en-us/sysinternals/downloads/sysmon)

[Day 09 Installing and Configuring Sysmon](Day%2009%20Installing%20and%20Configuring%20Sysmon.md)