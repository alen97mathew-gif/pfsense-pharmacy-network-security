# Monitoring and Backups

## Dashboard

The project dashboard was organized to make day-to-day health and security checks quick. Useful widgets included:

- System information/status
- Interface/traffic status
- pfBlockerNG / DNSBL visibility
- Snort alerts/status

## Routine checks

A practical review cycle includes:

1. Confirm WAN/LAN interface health.
2. Review unexpected firewall blocks.
3. Review pfBlockerNG and DNSBL events.
4. Review high-value Snort alerts and investigate context.
5. Check feed/rule update status.
6. Confirm backup success.

## Backups

Configuration backups were maintained daily. Backups from a real firewall must be treated as sensitive because they can contain credentials, hashes, certificates, VPN material, hostnames and other operational information.

**Repository rule:** never commit the live pfSense `config.xml`. Document the process instead.
