# Incident Report - SSH Brute-Force Attack

## Incident Details

| Field | Details |
|---|---|
| **Incident ID** | `SOC-LAB-001` |
| **What** | SSH brute-force / password-guessing activity |
| **Who** | Kali attacker `10.10.10.20` targeting `socadmin` |
| **Where** | Isolated SOC-LAB network; Ubuntu Server `10.10.10.10` |
| **When** | `2026-09-21 01:04:55` - `2026-09-21 01:05:36` |
| **Why** | Simulated unauthorized SSH access attempts against the `socadmin` account |
| **Detection** | Splunk Enterprise |
| **Severity** | Medium |
| **Status** | Contained |

## Incident Summary

A controlled SSH brute-force attack was simulated from Kali Linux against the `socadmin` account on the Ubuntu Server.

Splunk identified **13 matching failed-password events** from `10.10.10.20`, followed by **1 successful authentication**. The activity was investigated by correlating the source IP, username, timestamps, service, and authentication results.

The observed behavior was mapped to:

- **T1110.001 - Password Guessing**
- **T1021.004 - SSH**

## Response

The identified source IP was blocked using UFW, and the `socadmin` password was reset to a new strong password.

## Validation

Post-containment testing confirmed that:

- The Ubuntu Server remained reachable via ICMP.
- SSH access from `10.10.10.20` was blocked.
- The containment measures were effective.

## Final Outcome

The simulated incident was successfully detected, investigated, contained, and validated within the isolated SOC lab environment.

**Final Status: Contained**
