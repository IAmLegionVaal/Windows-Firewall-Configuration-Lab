# Windows Firewall Configuration Lab

![Status](https://img.shields.io/badge/Project-Completed-success)
![Windows](https://img.shields.io/badge/Platform-Windows-0078D4)
![Firewall](https://img.shields.io/badge/Focus-Windows%20Firewall-2F6FED)

A completed Windows security lab in which I created, tested and audited inbound and outbound Windows Defender Firewall rules across different network profiles.

> **Status:** Completed and validated. This repository documents work already performed in a private lab. Real device names, addresses, applications and environment-specific values have been generalized.

## Objectives completed

- Reviewed Domain, Private and Public firewall profiles
- Created inbound port and application rules
- Created outbound control rules
- Scoped rules by profile, protocol and remote address
- Enabled firewall logging
- Tested allowed and blocked traffic
- Reviewed active policy and rule precedence
- Documented troubleshooting and security findings

## Implementation summary

1. Reviewed the active network profile on the Windows endpoint.
2. Confirmed that Windows Defender Firewall was enabled.
3. Created narrowly scoped inbound rules for selected services.
4. Created outbound test rules for controlled validation.
5. Applied profile, address and protocol restrictions.
6. Enabled logging for dropped packets and successful connections where required.
7. Tested connectivity before and after each rule change.
8. Reviewed effective rules through PowerShell and the firewall console.
9. Removed or disabled temporary test rules after validation.

## Validation commands

```powershell
Get-NetFirewallProfile
Get-NetFirewallRule -Enabled True
Get-NetFirewallPortFilter
Get-NetFirewallAddressFilter
Test-NetConnection <target> -Port <port>
```

```cmd
netsh advfirewall show allprofiles
```

## Outcome

The endpoint enforced the intended inbound and outbound controls according to network profile and rule scope. Approved connections succeeded, blocked traffic failed as expected, and firewall logs provided evidence of the enforcement result.

## Findings

- A rule assigned to the wrong network profile had no effect even when its port and protocol were correct.
- Broad allow rules were easier to create but weakened the value of the firewall; limiting addresses, applications and profiles produced a safer result.
- Rule names and descriptions mattered during troubleshooting because Windows systems could contain many similar built-in rules.
- Port availability testing helped confirm the result, but firewall logging provided stronger evidence when traffic was dropped.
- Local rules and centrally applied policy could interact, so reviewing the effective rule set was more reliable than checking only one console entry.
- Disabling the firewall hid the root cause and was not an acceptable troubleshooting solution compared with creating a targeted temporary rule.

## Skills demonstrated

- Windows Defender Firewall administration
- Inbound and outbound rule design
- Network profile management
- Port, protocol and address scoping
- Firewall logging
- Connectivity testing
- Security troubleshooting
- Technical documentation

## Security notes

- No real production addresses or application paths are included.
- Temporary test rules were controlled and removed after validation.
- The lab was completed in a non-production environment.

## Author

**Dewald Pretorius** — L2 IT Support Engineer
