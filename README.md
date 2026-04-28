# Fiberhome HG6145F1 Custom Webui

This concerns only the devices available in Algeria, firmware version RP4423

WebUI changes are not permanent and will be reset after a reboot, however, modified settings are saved.  
An option to enable persistence across reboots is available.

## Screenshots
<p float="left">
  <img src="https://github.com/user-attachments/assets/76bbcfd8-a463-4f93-bc0e-2d8fdf730dbf" width="300" alt="Login page">
  <img src="https://github.com/user-attachments/assets/60ef7987-85ef-4d55-8935-0fa3200cc379" width="300" alt="home page">
</p>
<p float="left">
  <img src="https://github.com/user-attachments/assets/46cb3f0b-17f7-46bd-b23d-e83f05812c3f" width="300" alt="broadband settings">
  <img src="https://github.com/user-attachments/assets/d4f08818-bb05-43a6-b48b-5c61a43e8b45" width="300" alt="Voip settings">
</p>
<p float="left">
  <img src="https://github.com/user-attachments/assets/bf6b3f02-7b18-47af-8845-df33175d8628" width="300" alt="Application page">
  <img src="https://github.com/user-attachments/assets/0fd3198f-e695-4b3a-9c00-c7ac81eb974c" width="300" alt="Extra options">
</p>

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
- Schedule reboot option
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
