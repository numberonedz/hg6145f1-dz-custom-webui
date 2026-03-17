# How to enable Telnet

Login to the web interface (admin access is mandatory) and go to Security > ACL Settings

<img width="589" height="413" src="https://github.com/user-attachments/assets/42f073f4-0669-4671-b79c-cf49cdde1b0a" />


## Telnet Credentials
Connect to 192.168.1.1 with gpon/Fh@XXXXXX (was gpon/gpon with older firmware versions)

XXXXXX: last 6 characters of the MAC address

```
------acl IP:192.168.1.3 --------
Login: gpon
Password: Fh@XXXXXX

User> enable
Password: Fh@XXXXXX

Config#
```
