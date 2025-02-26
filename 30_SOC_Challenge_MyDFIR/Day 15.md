#### **Introduction to RDP Abuse**

- **RDP (Remote Desktop Protocol)**: Widely abused protocol; crucial in 90% of ransomware breaches in 2023 (source: Sophos).
    
- **RDP Use Case**: Enables remote connection to endpoints, facilitating remote work and troubleshooting.
    

#### **Understanding RDP**

- **Official Definition**: Communication protocol between terminal server and client.
    
- **Default Port**: TCP 3389.
    
- **User Benefits**: Remote access saves commute time, enhances accessibility and convenience.
    

#### **Risks and Abuse of RDP**

- **Common Attack Vector**: Exposed RDP services on servers allow unauthorized access.
    
- **Methods of Abuse**:
    
    - **Brute Force**: Attackers attempt multiple logins.
        
    - **Phishing**: Valid credentials obtained through phishing are used.
        
- **Credential Dumping**: Attackers gather credentials to move laterally within the network.
    

#### **Finding Exposed RDP Servers**

- **Tools**: Shodan and Censys can be used to find exposed RDP services.
    
- **Shodan**:
    
    - **Search Query**: `port:3389`.
        
    - **Details**: Provides insights into open RDP ports and associated machine names.
        
- **Censys**:
    
    - **Search Query**: `3389`.
        
    - **Filtering**: Allows filtering results to focus on RDP services.
        

#### **Protecting Against RDP Abuse**

1. **Disable Unused Services**:
    
    - Often, developers forget to disable RDP after development.
        
    - Regularly check for exposed services using tools like Shodan and Censys.
        
2. **Use Multi-Factor Authentication (MFA)**:
    
    - Adds an extra security layer; essential for account protection.
        
    - MFA is not foolproof but significantly enhances security.
        
3. **Restrict Access**:
    
    - Implement firewall rules to limit RDP access to specific IP ranges.
        
    - Use VPNs to secure RDP access.
        
4. **Strengthen Passwords**:
    
    - Use complex passwords (15+ characters, mixed case, numbers, special characters).
        
    - Consider using privileged access management (PAM) tools for one-time passwords.
        
5. **Avoid Default Accounts**:
    
    - Disable default local accounts.
        
    - Create new, uniquely named administrator accounts to thwart credential stuffing attacks.
        

#### **Monitoring and Detection**

- **Regular Log Review**:
    
    - Check authentication logs for unauthorized access.
        
    - Look for login attempts from unusual locations (e.g., countries where the organization doesn't do business).