# Fiberhome HG6145F1 Custom Webui

This concerns only the devices available in Algeria, firmware version RP4423

WebUI changes are not permanent and will be reset after a reboot, however, modified settings are saved.  
An option to enable persistence across reboots is available.

## What's new
- New login page + small UI changes
- Enable Custom DNS (cloudflare, Google...)
- PPPOE/Voip password retrieval
- Enable SSID Isolation
- Enable Custom Dynamic DNS
- Enable QoS settings
- Enable parental control
- Enable DLNA/Samba/NAT/ALG
- Enable System Log view
- TR-069 patch (prevents TR-069 from auto-enabling)

![ezgif-615983e564351ee7](https://github.com/user-attachments/assets/27a735db-aee6-4637-9ff5-0a8472fc5934)

## How to use:

1-Via the web interface (easiest)
- Go to Management > Device Management > Local Upgrade
- Choose custom-webui.bin and click Update File
- Wait a couple of seconds, there will be a message saying Upgrade failed
- Refresh the current webpage and voilà !

2-Via telnet:
- Use a usb stick or upload bash script to a writable directory (such as `/var` ) via tftp 
- Give correct permissions (`chmod +x custom-webui.sh`)
- Run the script

## How does it work:

***The bin image uses a patch-based update feature (instead of a full firmware update) pushed via TR-069 / OMCI.

Patched ajax binary (/cgi-bin folder) and modified html/js/css files are embeded in a bash script >>> Extracted to a temp folder (/var/www-custom) >>> Mount-binded to /www folder (read only)


#### Patched ajax binary:
-All available AJAX endpoints have been patched to allow access.  
-Instead of asterisks (**********), encoded PPPOE/VOIP password are returned (decrypted later via _fhdecrypt_ (javascript)) 
