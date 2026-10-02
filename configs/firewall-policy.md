# Sanitized Firewall Policy

This is a **policy representation**, not an export from the live firewall.

| Interface | Source | Destination | Service | Action | Purpose |
|---|---|---|---|---|---|
| LAN | LAN net | pfSense LAN address | DNS | Pass | Approved DNS path |
| LAN | LAN net | External DNS resolvers | DNS | Block / policy-enforce | Reduce DNS bypass |
| LAN | LAN net | Required Internet destinations | Required services | Pass | Business connectivity |
| LAN | LAN net | Known blocked IP reputation aliases | Any | Block | Reputation control |
| WAN | Internet | LAN | Unsolicited inbound | Block by default | Perimeter protection |

## Notes

- pfSense is stateful; return traffic for permitted states is handled automatically.
- Actual rule order matters.
- Anti-lockout/management access must be preserved until an equivalent explicit rule is verified.
- DoH cannot be reliably controlled by treating all TCP/443 traffic as DNS.
- GeoIP and reputation feeds can generate false positives and require monitoring.
