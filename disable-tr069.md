# How to prevent TR-069 from auto-enabling

With firmware version 4423, the TR-069 protocol is automatically re-enabled after every reboot.

The provided solution prevents this behavior, ensuring that TR-069 protocol remains disabled if you choose to.

_*It may work for other firmware versions (configuration file method; not tested)_

## Method 1: Use custom WebUI (easiest)
- Login to the web interface
- Go to WebUI Options > Disable TR069 and click 'Apply Patch'

## Method 2: edit configuration file
Add the following lines to your configuration file, encrypt it and upload it via the web interface
```
config interface 'InternetGatewayDevice__X_FH_FiLink__'
        option X_FH_link_enable '0'
```

Use [this tool](https://github.com/numberonedz/fiberhome-config-utility) for configuration file decryption/encryption.
