# Deployment Screenshots

No deployment screenshots are included yet. These folders are reserved for genuine sanitized evidence; the architecture diagram is illustrative rather than a captured firewall screen.

| Folder | Suggested evidence |
|---|---|
| [dashboard](dashboard/) | System health and LAN/WAN status |
| [firewall-rules](firewall-rules/) | Ordered LAN policy and DNS controls |
| [pfblockerng](pfblockerng/) | Feed status, DNSBL test match and reports |
| [snort](snort/) | LAN/WAN instances and controlled test alert |

Before uploading, redact public IPs, identifying hostnames, usernames, email addresses, unnecessary MAC addresses, credentials, tokens, keys, certificates, and customer/patient data. Inspect browser tabs and bookmarks too. Use opaque redaction and export a flattened image.

For each image, record the control tested, date, expected behavior, observed result, and relevant sanitized SID/log context. Link evidence from the [validation checklist](../docs/05-testing-validation.md). Never commit raw firewall exports or backups.
