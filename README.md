# Fiberhome HG6145F1 Custom Webui

This concerns only the devices available in Algeria, firmware version RP4423

## What's new
- New login page + small UI changes
- Enable Custom DNS
- PPPOE/Voip password retrieval

![ezgif-615983e564351ee7](https://github.com/user-attachments/assets/27a735db-aee6-4637-9ff5-0a8472fc5934)


## How to use:

1-Via the web interface
- Go to Management > Device Management > Local Upgrade
- Choose custom-webui.bin and click Upgrade
- Wait a couple of seconds, there will be a message saying Upgrade failed
- Refresh the current webpage and voilà !

2-Via telnet:
- Upload bash script to /var via tftp or use a usb stick
- Give correct permissions (`chmod +x ./custom-webui.sh`)
- Run the script

Web UI changes are not permanent and will be reset after a reboot, however, custom DNS settings are saved
