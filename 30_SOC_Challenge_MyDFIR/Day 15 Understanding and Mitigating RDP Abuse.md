# Day 15: Understanding and Mitigating RDP Abuse

## 1. Introduction

**Goal**: Understand RDP (Remote Desktop Protocol), its use, how attackers abuse it, and how to protect your systems.

## 2. Understanding RDP

**Definition**:

- **RDP (Remote Desktop Protocol)**: A protocol developed by Microsoft for communication between terminal server and terminal server client.
    
- **Default Port**: TCP 3389.
    

**Usage**:

- Enables authorized users to connect remotely to another machine.
    
- Facilitates remote work and troubleshooting, saving commute time and enhancing convenience.
    

## 3. Risks and Abuse of RDP

**Common Attack Vectors**:

- **Exposed RDP Services**: Attackers gain initial access through exposed RDP services on servers.
    
- **Brute Force Attacks**: Attackers attempt multiple login attempts to gain access.
    
- **Credential Theft**: Using stolen credentials obtained through phishing.
    

**Steps of Abuse**:

1. Attackers connect to the exposed RDP service.
    
2. Use brute force or stolen credentials to authenticate.
    
3. Perform credential dumping to gather more valid credentials.
    
4. Move laterally within the network using RDP.
    
5. Achieve objectives such as data exfiltration or deploying ransomware.
    

## 4. Finding Exposed RDP Servers

**Tools**:

- **Shodan**:
    
    - **Search Query**: `port:3389`
        
    - Provides insights into open RDP ports and associated machine names.
        
- **Censys**:
    
    - **Search Query**: `3389`
        
    - Allows filtering results to focus on RDP services.
        

## 5. Protecting Against RDP Abuse

### 1. Disable Unused Services

- Regularly check for exposed services using tools like Shodan and Censys.
    
- Disable RDP on development servers after use.
    

### 2. Use Multi-Factor Authentication (MFA)

- Adds an extra security layer to account logins.
    
- Essential for protecting accounts against unauthorized access.
    

### 3. Restrict Access

- Implement firewall rules to limit RDP access to specific IP ranges.
    
- Use VPNs to secure RDP access, allowing only authorized users to connect.
    

### 4. Strengthen Passwords

- Use complex passwords with at least 15 characters, mixed case, numbers, and special characters.
    
- Consider using privileged access management (PAM) tools for one-time passwords.
    

### 5. Avoid Default Accounts

- Disable default local accounts.
    
- Create uniquely named administrator accounts to thwart credential stuffing attacks.
    

## 6. Monitoring and Detection

**Regular Log Review**:

- Check authentication logs for unauthorized access.
    
- Investigate login attempts from unusual locations (e.g., countries where the organization doesn't operate).
