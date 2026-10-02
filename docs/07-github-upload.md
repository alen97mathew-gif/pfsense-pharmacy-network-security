# GitHub Upload Instructions

## Option 1 — GitHub website

1. Sign in to GitHub.
2. Create a new repository named `pfsense-pharmacy-network-security`.
3. Choose **Public** if this is intended as a portfolio repository.
4. Do **not** initialize it with another README if you plan to upload this package as-is.
5. Extract the ZIP from ChatGPT.
6. Upload the repository contents (not the outer ZIP itself). Preserve `docs/`, `configs/`, `diagrams/` and `screenshots/`; do not flatten their files into the root.
7. Commit with a message such as `Initial pfSense pharmacy security project`.
8. Review the rendered README and Mermaid diagram.

## Option 2 — Git command line

After creating an empty repository on GitHub:

```bash
git init
git add .
git commit -m "Initial pfSense pharmacy security project"
git branch -M main
git remote add origin <YOUR-GITHUB-REPOSITORY-URL>
git push -u origin main
```

## Updating this existing repository

Clone the repository before making further updates:

```bash
git clone https://github.com/alen97mathew-gif/pfsense-pharmacy-network-security.git
cd pfsense-pharmacy-network-security
# Add sanitized screenshots to the appropriate screenshots/ subfolder.
git status
git diff --check
git add screenshots/
git diff --cached
git commit -m "Add sanitized deployment evidence"
git push origin main
```

Review staged files before committing. A `.gitignore` does not protect secrets already tracked by Git or visible inside screenshots.

## Before publishing screenshots

Run through this checklist:

- No public IP addresses unless intentionally disclosed
- No customer/patient data
- No usernames/email addresses
- No passwords/tokens/API keys
- No private keys/certificates
- No real `config.xml`
- No unnecessary MAC addresses
- No identifying hostnames/site names
- Browser tabs/bookmarks are not exposing unrelated information

## Suggested GitHub metadata

**Description:**  
`pfSense pharmacy network security project featuring firewall hardening, Kea DHCP, pfBlockerNG/DNSBL, GeoIP controls, Snort IDS/IPS, monitoring and validation.`

**Topics:**  
`pfsense`, `cybersecurity`, `network-security`, `firewall`, `snort`, `ids`, `ips`, `pfblockerng`, `dns-security`, `homelab`, `blue-team`

## Final check

Open the repository in a logged-out/private browser window and inspect it as a recruiter would. The README should explain the problem, architecture, controls, testing and lessons without requiring access to private infrastructure.
