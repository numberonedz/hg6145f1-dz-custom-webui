# How to enable Custom DNS

Firmware version RP4423 doesn't allow users to use custom DNS (Cloudflare, Google...). Fortunately, there is a workaround :)

## Method 1: Use custom WebUI (easiest)
- Go to Network > BroadBand Settings > Internet Settings
- Change Dns Override option to Enable
- Enter primary/secondary DNS server and click Apply

<img width="444" height="537" alt="Capture" src="https://github.com/user-attachments/assets/51e39b0d-b002-48df-a3d1-c32706586160" />


## Method 2: edit configuration file
- Download and decrypt your configuration file
- Open 'usrconfig_conf' with a text editor and locate this section
```
config interface 'InternetGatewayDevice__WANDevice__1__WANConnectionDevice__1__WANPPPConnection__1__'
```
- Add the following lines to that section (replace IP1/IP2 of the DNS servers you want to configure)
```
	option DNSOverrideAllowed '1'
	option DNSServers 'IP1,IP2'
```
- Save, encrypt and upload your configuration file

NB: Use [this tool](https://github.com/numberonedz/fiberhome-config-utility) for configuration file decryption/encryption.
