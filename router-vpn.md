# Router VPN (WireGuard)

This adds a lightweight VPN-server helper at `Application > VPN > Router VPN`.

## What it does

- Starts a `wg0` WireGuard interface on the router.
- Enables IPv4 forwarding.
- Adds temporary `iptables` rules so VPN clients can route traffic through the router's WAN.
- Generates a ready-to-import WireGuard client configuration.

## Requirements

The helper intentionally does not bundle large binaries. The router firmware must already provide:

- `wg`
- `ip`
- `iptables`
- kernel WireGuard support for `ip link add dev wg0 type wireguard`

If those are missing, the page reports a clear error instead of changing firewall rules.

## Setup

1. Install the custom web UI with `custom-webui.sh`.
2. Open `Application > VPN > Router VPN`.
3. Enter your public IP or DDNS hostname.
4. Keep the default UDP port `51820`, or choose another UDP port.
5. Click `Start VPN`.
6. Import the generated client config into the WireGuard app on your phone or laptop.

## Internet access notes

- If the ONT has a public WAN address, allow inbound UDP on the selected port.
- If the ONT sits behind another router, forward the selected UDP port to this ONT.
- If your ISP uses CGNAT, inbound VPN access will not work without a public IP, port-forwardable upstream router, or an external relay/VPS.

## Persistence

Rules and keys are stored under `/var/router-vpn`, so they may be reset after reboot depending on firmware behavior. Re-open the page and click `Start VPN` after reboot, or add the same helper call to your own boot persistence mechanism.

## Security

- Treat the generated client config as a secret; it contains the client private key.
- Use a random high UDP port if you do not want to expose the default WireGuard port.
- Stop the VPN from the same page when remote access is no longer needed.