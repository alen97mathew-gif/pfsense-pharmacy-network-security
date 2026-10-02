# Testing and Validation

> **Evidence status:** This is a validation plan. No captured test results have been committed yet; unchecked items must not be treated as passed tests.

Use this checklist to demonstrate that the security controls worked without exposing sensitive information.

## A. Connectivity and DHCP

- [ ] Connect PH1/PH2 to the LAN switch.
- [ ] Confirm an address in the expected LAN/DHCP range.
- [ ] Confirm gateway is `192.168.1.1`.
- [ ] Confirm the intended DNS server is supplied.
- [ ] Confirm normal approved Internet connectivity.

Example Windows commands:

```powershell
ipconfig /all
ping 192.168.1.1
```

## B. DNS Resolver

```powershell
nslookup example.com 192.168.1.1
```

Expected result: the pfSense resolver responds successfully for an allowed domain.

## C. DNSBL

1. Select a harmless domain known to match an enabled test category/feed.
2. Query it through the pfSense resolver.
3. Confirm the configured block/sinkhole behavior.
4. Confirm the event is visible in DNSBL/pfBlockerNG logs.

Do not test by intentionally visiting active malicious infrastructure.

## D. External DNS bypass

From a test endpoint, attempt a DNS query to an external resolver only if doing so is permitted in the lab/site test plan.

Expected result when enforcement is enabled: the direct query should be blocked/redirected according to the implemented policy, while approved DNS through pfSense continues to work.

## E. Encrypted DNS / DoH

DoH uses HTTPS and requires more than simply blocking TCP/UDP 53. Validate the specific controls configured in the environment and verify that normal HTTPS applications are not unintentionally disrupted.

## F. pfBlockerNG

- [ ] Confirm feeds update successfully.
- [ ] Confirm IP/DNSBL tables populate.
- [ ] Confirm a safe known test match is logged.
- [ ] Check for false positives affecting required services.

## G. Snort

- [ ] Confirm Snort is running on LAN.
- [ ] Confirm Snort is running on WAN.
- [ ] Confirm community/FEODO rules are loaded as expected.
- [ ] Produce or identify a controlled test alert.
- [ ] Verify the alert appears on the expected interface.
- [ ] Document the SID/message and why the event was considered a test.
- [ ] Verify legitimate pharmacy connectivity after tuning.

## H. Firewall management safety

After firewall changes:

- [ ] WebGUI remains reachable from the authorized management path.
- [ ] Required outbound services still function.
- [ ] Blocked traffic is logged where expected.
- [ ] No unintended broad allow rule was introduced.

## I. Backup

- [ ] Confirm the current configuration backup exists.
- [ ] Confirm daily backup procedure/schedule.
- [ ] Store backups securely outside the public Git repository.
- [ ] Never commit an unsanitized `config.xml`.

## Suggested evidence table

| Test | Expected | Evidence |
|---|---|---|
| DHCP | Client receives valid LAN lease | Sanitized `ipconfig` screenshot |
| DNS | pfSense resolves allowed domain | `nslookup` screenshot |
| DNSBL | Safe test domain blocked | DNSBL log screenshot |
| IP reputation | Test match visible | pfBlockerNG report |
| Snort | Controlled alert generated | Sanitized Snort alert |
| Backup | Recovery copy available | Screenshot without secrets |
