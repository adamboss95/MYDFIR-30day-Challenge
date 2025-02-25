
## User Management & Security Hardening  
**Objective**: Secure user accounts and audit system permissions.  
Tasks:

- Create two users: dev1 and dev2 with home directories

```
sudo adduser dev1
```

```
sudo adduser dev2
```

to verify if users are created
```
cat /etc/passwd
```

- Force both users to reset passwords on first login.

```
sudo passwd --expire dev1
```

```
sudo passwd --expire dev2
```


- Create a group developers and add both users to it.

```
sudo addgroup developers
```

```
sudo usermod developers dev1
```

```
sudo usermod developers dev1
```

to verify this
```
cat /etc/group
```


- Restrict SSH access to members of the developers group. (dont forget to delete the lines added in the editor)

```
sudo vim /etc/ssh/sshd_config
```

add this line in the editor **AllowGroups developers** > save exit


> [!NOTE]
> Allow SSH to only members of the developers group


Restart SSH
```
systemctl restart ssh
```


- Find all files with SUID/SGID permissions and document them in suid-report.txt.

```
sudo find / -perm /6000 -type f > suid-report.txt
```


