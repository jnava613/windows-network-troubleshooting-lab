# Windows Network Troubleshooting — Home Lab 01

**Author:** Jose Nava  
**Completed:** November 9, 2026  
**Environment:** Windows laptop (16 GB RAM), Wi-Fi  
**Cost:** $0 — built-in Windows tools

## Overview

I performed a seven-step, non-destructive Windows network-health assessment designed to practice a Tier 1 help desk diagnostic workflow. This is an independent training project, **not a real outage repair or production service desk ticket**.

## Evidence-based results

| # | Command / task | Result | Evidence |
|---|---|---|---|
| 1 | `ipconfig` | Wi-Fi IPv4, subnet mask (`/22`) and gateway displayed | [Screenshot 01](screenshots/01_wifi_configuration_redacted.png) |
| 2 | `ipconfig /all` | DHCP enabled; DNS server addresses listed | Participant-reported; no screenshot |
| 3 | `ping 127.0.0.1` | 4/4 replies, 0% loss | Participant-reported; no screenshot |
| 4 | `ping <default-gateway>` | 4/4 replies, 0% loss; average 3 ms | [Screenshot 02](screenshots/02_gateway_ping.png) |
| 5 | `ping 1.1.1.1` | 4/4 replies, 0% loss; average 8 ms | [Screenshot 03](screenshots/03_external_ping.png) |
| 6 | `nslookup example.com` | DNS returned both IPv4 and IPv6 records | [Screenshot 04](screenshots/04_dns_lookup.png) |
| 7 | `Test-NetConnection example.com -Port 443` | `TcpTestSucceeded: True` | [Screenshot 05](screenshots/05_tcp_port_443_redacted.png) |

## Evidence gallery

### 1 — Wi-Fi IP configuration
![Wi-Fi configuration, with private IP details hidden](screenshots/01_wifi_configuration_redacted.png)

### 2 — Default gateway responds
![Gateway ping, 4 packets received and 0 percent loss](screenshots/02_gateway_ping.png)

### 3 — External internet IP responds
![Ping to 1.1.1.1, 4 packets received and 0 percent loss](screenshots/03_external_ping.png)

### 4 — DNS resolution works
![nslookup example.com returns IPv4 and IPv6 records](screenshots/04_dns_lookup.png)

### 5 — TCP port 443 reachable
![PowerShell test shows TcpTestSucceeded True](screenshots/05_tcp_port_443_redacted.png)

## Simulated support ticket

**Request:** Verify a Windows device's basic network configuration and reachability.  
**Actions:** Reviewed IPv4, DHCP and DNS configuration; tested local loopback, default gateway, public IP, hostname resolution, and remote TCP port 443.  
**Outcome:** All checks passed; no fault identified in the tested functions. No configuration changes or repairs were performed.

## What the results mean

- A configured IP address and gateway do **not** themselves prove connectivity.
- An ICMP gateway reply supports local network reachability at the time of the test.
- Public IP ping shows external ICMP reachability without requiring DNS.
- Successful `nslookup` establishes name resolution for the tested hostname.
- `TcpTestSucceeded: True` establishes remote TCP port reachability, **not** a complete HTTPS page load or TLS certificate verification.

## Privacy and evidence notes

Screenshots originate from actual Windows commands run by the participant. For public use, account prompts were cropped and the laptop's private IP address, configured gateway, and PowerShell source IP were obscured. No response counts, DNS records, timings, or test status values were changed. The DHCP and loopback outcomes remain participant-reported without screenshots.

## Skills applied

Windows Command Prompt · PowerShell · TCP/IP · IPv4 · DHCP configuration review · DNS · ICMP · `ping` · `nslookup` · `Test-NetConnection` · technical documentation · Tier 1 troubleshooting

## Resume bullet

> Completed a documented Windows network-health lab using `ipconfig`, `ping`, `nslookup`, and `Test-NetConnection` to verify IPv4/DHCP configuration, gateway and external reachability, DNS name resolution, and TCP port 443 connectivity.
