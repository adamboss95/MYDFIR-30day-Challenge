


| IOA                                                                                                                 | IOC                        |
| ------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| Proactive                                                                                                           | Reactive                   |
| Credential theft=> means if credentials are stolen cyberattack is in progess                                        | IPAddress                  |
| Credential exploitation => after credential theft, next step is exploitation of the network or system.              | Vulnerability Exploitation |
| Lateral Movement => attacker moving lateraly, trying to exploit the credentials stolen to move to different segment | Malware Injection          |
| c2 communications                                                                                                   | Cyber Threat Signatures    |
| Data Exfiltration                                                                                                   | Static                     |

IOC limitations:
- IOC detection compares potential threats to a database of known attack signatures






### IOA (Indicators of Attack)

- **Focus:** Detects ongoing or imminent attacks by identifying suspicious behaviors or patterns.
    
- **Proactive:** Helps identify potential threats before they cause significant damage.
    
- **Example:** Unusual network traffic, unauthorized access attempts, or abnormal user behavior.
    

### IOC (Indicators of Compromise)

- **Focus:** Identifies evidence that a system or network has already been compromised.
    
- **Reactive:** Used after an attack has occurred to investigate and respond to security incidents.
    
- **Example:** Malware signatures, unusual files, or unauthorized changes to system configurations.
    

### Key Differences:

- **Timeframe:** IOAs are used during the early stages of an attack, while IOCs are used after an attack has occurred.
    
- **Purpose:** IOAs help detect and prevent attacks, while IOCs help investigate and mitigate the impact of breaches.
    
- **Nature:** IOAs are proactive and behavior-based, while IOCs are reactive and evidence-based.





### Real-Life Scenarios for IOA (Indicators of Attack) and IOC (Indicators of Compromise)

#### Scenario for IOA (Indicators of Attack):

Imagine an employee at a company receives a phishing email that tricks them into clicking a malicious link. The company's cybersecurity system detects unusual behavior, such as:

- **Suspicious Network Traffic:** The employee's computer starts communicating with an unknown external server.
    
- **Unauthorized Access Attempts:** The system logs show multiple failed login attempts to access sensitive data.
    

These actions are **Indicators of Attack (IOA)** because they suggest an ongoing or imminent attack. The cybersecurity team can intervene, investigate, and prevent potential damage by blocking the malicious traffic and securing the employee's account.

#### Scenario for IOC (Indicators of Compromise):

Later, the cybersecurity team conducts a routine audit and discovers:

- **Malware Signatures:** Specific malware files are found on the network.
    
- **Unusual File Modifications:** Critical system files have been altered without authorization.
    
- **Unauthorized Data Access:** Logs show that sensitive data was accessed by an unauthorized user.
    

These signs are **Indicators of Compromise (IOC)** because they provide evidence that the network has already been compromised. The team can then take steps to contain the breach, remove the malware, and strengthen security measures to prevent future incidents.