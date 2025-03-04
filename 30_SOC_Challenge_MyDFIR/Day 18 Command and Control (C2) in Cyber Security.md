# Day 18: Command and Control (C2) in Cyber Security

## 1. Introduction

**Goal**: Understand Command and Control (C2) and its significance in cyber security.

## 2. Command and Control (C2)

**Definition**: Techniques used by adversaries to communicate with systems under their control within a victim's network.

**Importance**: Allows attackers to perform additional actions to achieve their objectives (e.g., stealing credentials, moving laterally, stealing sensitive information, executing ransomware).

## 3. Common Tools and Frameworks

**Metasploit:**

- **Framework**: Popular in Kali Linux.
- **Owner**: Rapid7.
- **Features**: Contains various exploits and auxiliaries.

**Cobalt Strike:**

- **Product**: Commercial, built for adversary emulation by Fortra.
- **Usage**: Common in compromised environments.
- **Detection**: Resources available (e.g., DFIR Report).

**Sliver:**

- **Framework**: Open-source by Bishop Fox.
- **Connections**: Supports mTLS, HTTP, HTTPS, DNS, WireGuard.
- **Alternative**: Designed as an open-source alternative to Cobalt Strike.

**Mythic:**

- **Usage**: Used in the 30-day challenge.
- **Build**: Golang, Docker, Docker Compose, web browser UI.
- **Features**: Tracks payloads and C2 profiles, supports 21 different agents.

## 5. Next Steps

**Tasks**:

- Craft an attack on a Windows server.
- Set up a Mythic server.
- Deploy an agent to establish a successful C2 session.

[Day 19 Creating an Attack Diagram](Day%2019%20Creating%20an%20Attack%20Diagram)