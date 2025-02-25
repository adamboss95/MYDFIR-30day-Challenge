### Cyber Kill Chain
The **Cyber Kill Chain** is a model developed by Lockheed Martin to describe the stages of a cyberattack, from initial reconnaissance to achieving the attacker's objectives

#### Seven Stages of Cyber Kill Chain
**Reconnaissance:** The attacker gathers information about the target to find vulnerabilities
**Weaponization:** The attacker creates malware or tools to exploit the identified vulnerabilities
**Delivery:** The attacker delivers the weaponized payload to the target system, often through phishing emails or compromised websites
**Exploitation:** The attacker exploits the vulnerabilities to gain access to the target system
**Installation:** The attacker installs additional tools or malware to maintain access and control over the system
**Command and Control (C2):** The attacker establishes a command and control channel to remotely control the compromised system
**Actions on Objectives:** The attacker achieves their goals, such as data exfiltration, destruction, or disruption

Example:
**WannaCry** exploited a vulnerability in Microsoft Windows called **EternalBlue**, which was originally developed by the U.S. National Security Agency (NSA)
#### **WannaCry ransomware attack**:

##### Steps of the Cyber Kill Chain:

1. **Reconnaissance:**
    
    - Attackers identified systems primarily running Microsoft's Windows 7 and Windows Server 2008 as their targets. They gathered information about these systems to find vulnerabilities.
        
2. **Weaponization:**
    
    - The attackers weaponized the EternalBlue exploit, which took advantage of a vulnerability in Microsoft's implementation of the Server Message Block (SMB) protocol (CVE-2017-0144). They created the WannaCry ransomware using this exploit.
        
3. **Delivery:**
    
    - The ransomware was delivered via phishing emails and malicious downloads. Users unknowingly downloaded and executed the ransomware.
        
4. **Exploitation:**
    
    - Upon gaining access to a system, the EternalBlue exploit was used to compromise the target. This allowed the ransomware to execute on the victim's machine.
        
5. **Installation:**
    
    - The ransomware then encrypted user files, effectively locking them and making them inaccessible to the user.
        
6. **Command & Control (C2):**
    
    - After successful installation, the ransomware connected to an external server operated by the attackers to report a new infection and to update its encryption algorithms.
        
7. **Actions on Objectives:**
    
    - The ransomware displayed a ransom note, demanding payment in Bitcoin to decrypt the files. Victims were forced to pay the ransom to regain access to their files.
