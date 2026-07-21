# Pi-hole

A Docker-based Pi-hole setup for network-wide ad blocking and DNS management.

## Overview

This setup runs Pi-hole v6 in a Docker container with persistent configuration stored in `etc-pihole/`.

## Quick Start

```bash
docker compose up -d
```

## Ports

| Port | Protocol | Purpose |
|------|----------|---------|
| 53 | TCP/UDP | DNS |
| 80 | TCP | HTTP web interface |
| 443 | TCP | HTTPS web interface |

## Configuration

All Pi-hole configuration is managed via `etc-pihole/pihole.toml`. Key settings:

- **Upstream DNS**: Google (8.8.8.8, 8.8.4.4)
- **Listening mode**: ALL (required for Docker bridge networking)
- **Domain**: `lan`
- **Web interface**: `http://pi.hole/admin` or `https://pi.hole/admin`
- **DHCP**: Disabled (use your router's DHCP server)
- **TLS**: Enabled with auto-generated self-signed certificate

## Files

| Path | Description |
|------|-------------|
| `compose.yaml` | Docker Compose configuration |
| `etc-pihole/pihole.toml` | Main Pi-hole configuration |
| `etc-pihole/gravity.db` | Blocklist database |
| `etc-pihole/pihole-FTL.db` | Query log database |
| `etc-pihole/hosts/custom.list` | Custom DNS entries |
| `etc-pihole/dhcp.leases` | DHCP lease file |

## Custom DNS Entries

Add custom local DNS records to `etc-pihole/hosts/custom.list` in hosts file format:

```
192.168.1.10 myserver.lan
192.168.1.20 nas.lan
```

this is an edit