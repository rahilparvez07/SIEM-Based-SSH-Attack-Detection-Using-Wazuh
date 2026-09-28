# Wazuh SIEM: SSH Security Monitoring & Attack Detection

## Overview

This project demonstrates a SOC/SIEM lab built using Wazuh to
monitor and investigate SSH authentication activity.

The lab simulates SSH password-guessing activity from Kali Linux
against an Ubuntu Server and uses Wazuh to collect, analyze and
display the resulting security events.

## Architecture

Kali Linux
    |
    | SSH / Hydra
    ↓
Ubuntu Server
    |
    | /var/log/auth.log
    ↓
Wazuh Manager
    |
    ↓
Wazuh Indexer
    |
    ↓
Wazuh Dashboard

## Technologies

- Wazuh
- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Ubuntu Server
- Kali Linux
- OpenSSH
- Hydra

## Objectives

- Deploy a SIEM lab using Wazuh
- Monitor SSH authentication activity
- Simulate SSH password-guessing attacks
- Detect failed SSH authentication
- Investigate successful SSH authentication
- Analyze security alerts using the Wazuh Dashboard

## Attack Simulation

A controlled SSH password-guessing simulation was performed
from Kali Linux using Hydra.

Example:

    hydra -l wazuhadmin -P passwords.txt ssh://<UBUNTU-IP>

## Wazuh Detection

### Failed SSH Authentication

Wazuh detected the failed SSH authentication attempts.

**Rule ID:** 5760

**Severity:** Level 5

**Description:** sshd: authentication failed

**MITRE ATT&CK:**

- T1110.001 - Password Guessing
- T1021.004 - SSH

### Successful SSH Authentication

Wazuh also detected the subsequent successful authentication.

**Rule ID:** 5715

**Description:** sshd: authentication success

## Evidence

### Hydra Attack Simulation

![Hydra attack](screenshots/01-hydra-attack.png)

### Wazuh Dashboard

![Wazuh Dashboard](screenshots/02-wazuh-dashboard.png)

### Wazuh Alert Details

![Wazuh Alert](screenshots/03-wazuh-alert-details.png)

### Ubuntu SSH Logs

![SSH logs](screenshots/04-ubuntu-auth-log.png)

### Successful SSH Authentication

![Successful SSH login](screenshots/05-successful-ssh-login.png)

## Key Learning

This project demonstrates the SOC workflow:

Attack Simulation
→ Log Generation
→ Log Collection
→ SIEM Detection
→ Alert Investigation

## Future Work

- SSH brute-force correlation
- Auditd monitoring
- File Integrity Monitoring
- Privilege escalation detection
- Active Response
- Incident investigation
