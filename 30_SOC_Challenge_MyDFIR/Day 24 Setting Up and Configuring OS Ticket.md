# Day 24: Setting Up and Configuring OS Ticket

## 1. Introduction

**Goal**: Successfully set up and configure OS Ticket, a ticketing system for the challenge.

## 2. Deploying the Server

**Steps**:

1. **Log in to Vulture**:

    - Click on `Deploy` and select "Deploy New Server".
    - Choose `Cloud Compute` with a shared CPU.
    - Select `Singapore` as the location.
    - Choose `Windows Standard 2022` as the operating system.
    - Select `Cloud Regular Compute` plan with 55 GB, 1 CPU, and 2 GB of memory.
    - Disable `auto backup` and `IPv6`.
    - Enable `Virtual Private Cloud`.
    - Set the host name to `MyDFIR-OSticket`.
    - Click `Deploy Now`.

2. **Access the Server**:
    
    - After setup, select "View Console".
    - RDP into the machine using the provided username and password using `xfreerdp`.

```
 xfreerdp /v:<MyDFIR-OSticket-IP> /u:Administrator
```

## 3. Setting Up the Firewall

**Steps**:

1. **Add a Firewall**:

    - Go to `Settings` and click on `Firewall`.
    - Use the `SOC Simulation` firewall.
    - This firewall will restrict access to the web server hosting the ticketing system.

## 4. Installing XAMPP

**Steps**:

1. **Download XAMPP**:
    
    - Search for `XAMPP` and go to the Apache Friends website.
    - Download version 8.2.2 (or the latest available version).

2. **Install XAMPP**:
    
    - Open the installer and follow the setup wizard.
    - Note the installation directory (default is `C:\xampp`).
    - Complete the installation and open the XAMPP control panel.

## 5. Configuring XAMPP

**Steps**:

1. **Edit Properties Configuration File**:
    
    - Go to `C:\xampp` and find the `properties` configuration file.
    - Change the  `apache_domainname` to your `MyDFIR-OSticket` public IP address.
    - Save the changes.

2. **Create Firewall Rules**:
    
    - Open `Windows Defender Firewall with Advanced Security`.
    - Create new inbound rules for ports `80` and `443`.
    - Allow TCP connections on these ports.

## 6. Starting XAMPP Services

**Steps**:

1. **Start Apache and MySQL Services**:
    
    - Open the `XAMPP control panel`.
    - Start the Apache and MySQL services.

2. **Access PHP MyAdmin**:
    
    - Click on `Admin` under the Apache service.
    - Select `phpMyAdmin` at the top. or search this URL [localhost / 127.0.0.1 | phpMyAdmin 5.2.1](http://localhost/phpmyadmin/)
    - 
## 7. Configuring PHP MyAdmin

**Steps**:

1. **Authorize Public IP Address**:
    
    - Go to PHP MyAdmin and select `User Accounts`.
    - Modify the `root` account which have hostname `localhost` & in `login information` change the hostname to `MyDFIR-OSticket` public IP address.
    - Set the password to `Winter2024!`.

	- Modify the `pma` account which have hostname `localhost` & in `login information` change the hostname to `MyDFIR-OSticket` public IP  address.
	- Set the password to `Winter2024!`.

2. **Edit PHP Admin Configuration File**:
    
    - Go to the `phpMyAdmin` directory and find `config.inc.php`.
    - Make a backup of the file.
    - Scroll down to where the `/* Bind to the localhost ipv4 address and tcp */` is and change the server host to your `MyDFIR-OSticket` public IP address and password to new password `Winter2024!`
    
    - Change the `pma`  user password to new password `Winter2024!` under `/* User for advanced features */` and password to new password `Winter2024!`.

## 8. Installing OS Ticket

**Steps**:

1. **Download OS Ticket**:
    
    - Go to the [Download – osTicket | Support Ticketing System](https://osticket.com/download/)) and download the `self-hosted` version.
    - Extract the downloaded `osTicket` files . and then extract again the sub folder `osTicket-v1.18.2`

2. **Prepare XAMPP for OS Ticket**:
    
    - Create a new directory called `osticket` under the `htdocs` directory in `XAMPP`.
    - Copy the extracted `osTicket-v1.18.2` files into the `osticket` directory.

3. **Access OS Ticket Setup Page**:
    
    - Open a browser and navigate to `http://<MyDFIR-OSticketpublic_ip>/osticket/upload`.
    - Follow the setup instructions.

4. **Rename Configuration File**:

    - Navigate to `C:\xampp\htdocs\osticket\upload\include`
    - Rename `ost-sampleconfig.php` to `ost-config.php` in the `include` directory.
    - Continue with the setup.

## 9. Setting Up OS Ticket

**Steps**:

1. **Basic Installation**:
    
    - Enter the help desk name, admin username, and password.
    - Create a new database in PHP MyAdmin named `MyDFIR-db`.

2. **Database Configuration**:
    
    - Use the root username and the public IP address for the MySQL host.
    - Enter the password `Winter2024!`.

3. **Complete Installation**:
    
    - Ensure the database is created and privileges are set.
    - Rerun the OS Ticket configuration and complete the setup.

## 10. Finalizing OS Ticket Setup

**Steps**:

1. **Configure File Permissions**:

    - Navigate to `C:\xampp\htdocs\osticket\upload\include`
    - Open PowerShell with admin privileges.
    - Navigate to the `include` directory where `ost-config.php` is located.
    - Change the file permissions using the provided commands.

```
icacls ./ost-config.php /reset
```

2. **Access OS Ticket URLs**:
    
    - Copy the OS Ticket URL and staff control panel URL.
    - Save these URLs for future access.

|**Your osTicket URL:**  <br>[http://MyDFIR-OSticket-IP/osticket/upload/](http://45.76.156.191/osticket/upload/)|

**Your Staff Control Panel:**  <br>[http://MyDFIR-OSticket-IP/osticket/upload/scp](http://45.76.156.191/osticket/upload/scp/admin.php)|

3. **Log in to OS Ticket**:
    
    - Use the staff control panel URL to log in as an agent.
    - Enter the username and password created during setup.

> [!NOTE]
> Your osTicket URL doesnt let you login for some reason, so make sure to use the staff control panel URL to login

## 11. Exploring OS Ticket

**Steps**:

1. **Admin Panel**:
    
    - Access the admin panel to configure settings.
    - Change the name and title if desired.
    - Create new agent accounts for additional users.

2. **Managing Tickets**:
    
    - Use the admin panel to manage and track tickets.
    - Assign and transfer tickets as needed.


[Day 25 Integrating OS Ticket into Your Tech Stack](Day%2025%20Integrating%20OS%20Ticket%20into%20Your%20Tech%20Stack.md)