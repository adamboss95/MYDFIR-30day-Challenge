# Day 05 Setting Up a Windows Server in the Cloud

## 1. Deploying a Windows Server on Vultr

1. **Log in to Vultr**
    
    - Visit [**Vultr**](https://www.vultr.com/) and log in to your account.
        
2. **Deploy a New Server**
    
    - Click Deploy → Deploy New Server.
        
3. **Choose Server Type**
    
    - Select *Cloud Compute (Shared CPU)* (sufficient for this use case).
        
4. **Select a Location**
    
    - Choose a data center location (e.g., *Singapore*).
        
5. **Select an Operating System**
    
    - Choose *Windows Standard 2022 (latest version).*
        
6. **Choose a Plan**
    
    - Select the cheapest option: *$24/month* (1 vCPU, 2GB RAM).
        
7. **Disable Additional Features**
    
    - *Auto backups* → Not required
        
    - *IPv6* → Not required
        
    - *Virtual Private Cloud (VPC)* → Not selected (for security reasons)
        
8. **Set Hostname
        
    - Example: `MyDFIR-Win-wahab`
        
9. **Deploy the Server**
    
    - Click *Deploy Now* and wait for the instance to start.

## 2. Accessing the Windows Server

**Check Server Status**

Wait until the server status changes to Running.

**Open the Console**

Click View Console.
 
If the server is still deploying, wait a few minutes.

**Log In to Windows Server**

Click the arrow button → Show Extra Keys → Send Ctrl+Alt+Del.

Copy and paste the password provided in Vultr.

Sign in to the Windows Server.

## 3. Enabling Remote Desktop Protocol (RDP)

1. **Find the Public IP Address**
    
    - Copy the public IP address from Vultr.
        
2. **Use Remote Desktop to Connect**
    
    - Open Remote Desktop (RDP) on your local machine.
        
    - Paste the copied IP address and click Connect.
        
    - Enter the password and log in.
        
3. **Verify RDP Connectivity**
    
    - Ensure successful login via RDP.
        
4. **Monitor for Unauthorized Login Attempts**
    
    - Once RDP is exposed, expect to see unsuccessful login attempts from attackers.
        
    - These will generate logs, which will be analyzed in later videos.


[Day 06 Understanding Fleet Server and Elastic Agent](Day%2006%20Understanding%20Fleet%20Server%20and%20Elastic%20Agent)