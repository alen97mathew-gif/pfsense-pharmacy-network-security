# Snort IDS/IPS

## Deployment

Snort was configured on both **LAN** and **WAN** interfaces to provide network threat visibility.

## Rule sources

The project used:

- Snort GPLv2 Community rules
- FEODO Tracker Botnet C2 indicators/rules

## Operational workflow

1. Update enabled rule sources.
2. Confirm the LAN/WAN Snort instances are running.
3. Generate controlled, non-destructive test traffic or validate against known safe rule triggers.
4. Review alert timestamp, interface, source/destination, protocol and SID/message.
5. Determine whether the event is expected, suspicious or a false positive.
6. Tune rules/suppressions only after understanding why the alert fired.

## IDS/IPS principle

An alert is evidence to investigate, not proof that a host is compromised. Blocking mode can affect legitimate traffic, so rule categories should be enabled and tuned incrementally.

## Evidence to capture for the portfolio

Good sanitized screenshots include:

- Snort interface overview showing LAN/WAN
- Enabled rule source/category screen
- Alert list with public IPs/host-identifying values blurred
- A controlled test alert and a short explanation of why it triggered
