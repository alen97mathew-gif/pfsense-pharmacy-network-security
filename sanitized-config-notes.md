# Sanitized Configuration Notes

## LAN

```text
Interface: eth1
Network:   192.168.1.0/24
Gateway:   192.168.1.1
```

## WAN

```text
Interface: eth0
Addressing: REDACTED / ISP-provided
```

## Kea DHCP

```text
Pool start: 192.168.1.100
Pool end:   192.168.1.199
Gateway:    192.168.1.1
DNS:        pfSense / configured resolver path
```

## Example endpoints

```text
PH1: 192.168.1.100
PH2: 192.168.1.101
```

## pfBlockerNG-devel

```text
IPv4/IP reputation: Enabled/configured
GeoIP controls:     Enabled/configured as required
DNSBL:              Enabled
DNSBL feeds:        Shallalist / UT1-based categories used in testing
```

## Snort

```text
Interfaces: LAN and WAN
Rules:      Snort GPLv2 Community
            FEODO Tracker Botnet C2
```

## Intentionally omitted

The following must never be copied from a real deployment into this repository:

- Passwords and password hashes
- API tokens
- Certificates/private keys
- Public WAN address
- Customer/patient information
- Full pfSense configuration export
- Unique identifiers that expose the organization
