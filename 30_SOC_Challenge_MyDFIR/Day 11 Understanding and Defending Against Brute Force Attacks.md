# Day 11: Understanding and Defending Against Brute Force Attacks

## 1. Introduction

**Goal**: Learn about Brute Force attacks, common tools used, and protection methods.

## 2. What is a Brute Force Attack?

**Definition**: An attacker tries every password combination to compromise 
an account.

**Example**: Trying every combination on a luggage keypad lock.

**Prevalence**: Common due to ease of use and accessibility.

## 3. Common Types of Brute Force Attacks

**Simple Brute Force Attack**:

- Tries every combination starting from 0000.
- Automated attempts to gain unauthorized access.

**Dictionary Attack**:

- Uses a word list containing common words, phrases, and passwords from credential dumps.

- Higher success rate due to repeated passwords.

**Credential Stuffing**:

- Uses credential dumps to try every username and password combination.
- Commonly seen in honeypots.

## 4. Protecting Against Brute Force Attacks

**Long Passwords/Passphrases**:

 - Use 15+ character passwords or passphrases.
 - Include uppercase letters, numbers, and special characters.
 - Use a password manager to generate and store passwords.

**Multifactor Authentication (MFA)**:

- Adds an additional layer of security.
- Prompts for an additional authentication method (SMS, email, authenticator).
- Recommended to use an authenticator over SMS or email.

**Vigilance**: >> the action or state of keeping careful watch for possible danger or difficulties.

- Adopt a mindset of questioning and high alert.
- Verify the source and purpose of emails asking for login.
- Sign up for alerts on haveibeenpwned.com to check if your email was compromised.
## 5. Additional Protection Measures

**Check Attack Surface**:

- Identify publicly available assets and services (e.g., SSH, RDP).
- Disable unnecessary services or place them behind a firewall.

## 6. Common Tools for Brute Force Attacks

- **Hydra**
- **Hashcat**
- **John the Ripper**


**Note**: Use these tools ethically on machines you own or have permission to test.

[Day 12 Setting Up an SSH Server and Reviewing Authentication Logs](Day%2012%20Setting%20Up%20an%20SSH%20Server%20and%20Reviewing%20Authentication%20Logs.md)
