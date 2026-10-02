# Firewall Configuration

This document records policy intent rather than exporting a live pfSense configuration.

## Baseline behavior

pfSense provides stateful inspection and NAT at the perimeter. The final ruleset retained the platform's management/anti-lockout protection and a LAN policy that allowed required outbound connectivity.

## DNS policy

LAN clients were intended to use the pfSense DNS Resolver rather than arbitrary external resolvers.

Representative policy intent:

1. Permit LAN clients to query the firewall's DNS service.
2. Prevent direct client DNS queries to external resolvers where the environment requires enforced DNS filtering.
3. Test encrypted DNS / DoH bypass controls separately because HTTPS-based DNS cannot be safely identified by port number alone.
4. Log blocks during rollout so legitimate application failures can be investigated.

## IPv6

IPv6 rules should match the actual ISP/site design. Do not copy an IPv6 allow/block rule blindly into another deployment. The original project documentation retained/reviewed the applicable default IPv6 behavior rather than presenting an untested universal rule.

## Administrative safety

Before changing LAN management rules:

- Maintain a local recovery path.
- Export a sanitized/offline backup for recovery.
- Change one control at a time.
- Confirm WebGUI/SSH access after each relevant policy change.
- Avoid deleting anti-lockout protection until an equivalent management rule is confirmed.

See `configs/firewall-policy.md` for a sanitized policy matrix.
