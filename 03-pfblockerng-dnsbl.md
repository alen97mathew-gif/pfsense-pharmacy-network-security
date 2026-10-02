# pfBlockerNG-devel and DNSBL

## Purpose

pfBlockerNG-devel extended the firewall with reputation and domain-based filtering.

## Controls used

- IPv4/IP reputation blocking
- GeoIP controls
- DNSBL domain filtering
- DNS Resolver integration
- Shallalist / UT1-based DNSBL categories used during project testing

## DNSBL flow

```text
LAN Client
   |
   | DNS request
   v
pfSense DNS Resolver
   |
   +--> Allowed domain -> normal resolution
   |
   +--> DNSBL match -> blocked/sinkholed according to configuration
```

## Validation approach

Use a **safe test domain/category** that is expected to be blocked by an enabled feed. Do not browse malicious domains merely to prove the filter works.

Example diagnostic command:

```bash
nslookup example.test 192.168.1.1
```

Replace `example.test` with a harmless domain known to match the category/feed you are validating.

Then review the DNSBL/pfBlockerNG logs to confirm that the request matched the intended policy.

## GeoIP caution

GeoIP is a coarse control and is not an identity or trust mechanism. Allow/deny decisions should be based on business requirements and tested for third-party/CDN dependencies.
