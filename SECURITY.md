System/Rootkit audit
-----------------------

```
rkhunter -c  --report-warnings-only
```

Rootkit audit
-----------------------

```
chkrootkit
```

History search between two command
-----------------------

```
fc -lr ls ps
```

Log audit
-----------------------

```
CentOS: /var/log/secure
Debian/Ubuntu: /var/log/auth.log
```

SSH - /etc/ssh/sshd_config
-----------------------

```
PasswordAuthentication no
PermitRootLogin no
```

Password aging -  /etc/shadow 
-----------------------

```
chage -M 60 -m 7 -W 7 userName
```

Password aging -  force user to change on first login
-----------------------

```
chage -d 0 tom
```

Lock/unlock a user account
-----------------------

```
passwd -l vivek
passwd -u vivek
```

Locking User Accounts After Login Failures - failed attempts /var/log/faillog
-----------------------

```
faillog
```

To unlock an account after login failures, run:
-----------------------

```
faillog -r -u userName
```

Find Listening Network open Ports and associated programs:
-----------------------

```
netstat -tulpn
nmap -sT -O localhost
```

Locate world-writable files
-----------------------

```
find /dir -xdev -type d \( -perm -0002 -a ! -perm -1000 \) -print
```

Locate noowner files
```
find /dir -xdev \( -nouser -o -nogroup \) -print
```
