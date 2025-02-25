### MITR Attack
the **MITRE ATT&CK** framework is a comprehensive knowledge base of adversary tactics and techniques based on real-world observations.

#### Key Components of MITRE ATT&CK:

1. **Tactics:** The "why" of an attack, representing the adversary's goals (e.g., initial access, execution, persistence).
2. **Techniques:** The "how" of an attack, describing the methods adversaries use to achieve their goals (e.g., phishing, credential dumping).
3. **Sub-techniques:** More specific descriptions of adversarial behavior within a technique.
4. **Procedures:** Specific implementations or real-world examples of techniques and sub-techniques.
#### Key Tactics in the MITRE ATT&CK Framework

1. **Reconnaissance:** Gathering information about the target.
    
2. **Resource Development:** Establishing resources for the attack.
    
3. **Initial Access:** Gaining entry into the target environment.
    
4. **Execution:** Running malicious code on the target system.
    
5. **Persistence:** Maintaining access to the target system.
    
6. **Privilege Escalation:** Gaining higher-level permissions.
    
7. **Defense Evasion:** Avoiding detection and defenses.
    
8. **Credential Access:** Stealing account credentials.
    
9. **Discovery:** Identifying information about the target environment.
    
10. **Lateral Movement:** Moving through the target environment.
    
11. **Collection:** Gathering data from the target.
    
12. **Command and Control:** Communicating with compromised systems.
    
13. **Exfiltration:** Stealing data from the target.
    
14. **Impact:** Disrupting or destroying the target environment.

#### Example NotPetya Ransomware Attack

**Reconnaissance:**

- Attackers identified vulnerabilities in the Ukrainian financial sector and targeted companies using the M.E.Doc accounting software.
    

**Initial Access:**

- The attackers gained initial access by compromising the update mechanism of the M.E.Doc software, distributing the malware as a legitimate software update.
    

**Execution:**

- Once inside the network, the malware executed a payload that encrypted the victim's files and displayed a ransom note.
    

**Persistence:**

- The malware established persistence by creating scheduled tasks and modifying registry keys to ensure it would run on system reboot.
    

**Privilege Escalation:**

- NotPetya used the EternalBlue exploit and other techniques to escalate privileges and spread laterally across the network.
    

**Defense Evasion:**

- The malware used various techniques to evade detection, such as disabling security software and clearing event logs.
    

**Credential Access:**

- NotPetya harvested credentials from infected machines using tools like Mimikatz.
    

**Discovery:**

- The malware performed network discovery to identify other vulnerable systems within the network.
    

**Lateral Movement:**

- Using the harvested credentials and exploits, NotPetya moved laterally across the network, infecting other machines.
    

**Collection:**

- The malware collected sensitive data from the infected systems.
    

**Command and Control:**

- NotPetya communicated with command and control servers to receive instructions and report infection status.
    

**Exfiltration:**

- The malware exfiltrated collected data to the attacker's servers.
    

**Impact:**

- The primary impact was data encryption, rendering systems inoperable and causing significant disruption to businesses worldwide.
