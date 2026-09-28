# SSH Brute-Force Detection

## Objective

To simulate SSH password-guessing activity from Kali Linux
against an Ubuntu Server and detect the resulting authentication
events using Wazuh.

## Lab Environment

- Kali Linux - Attack simulation
- Ubuntu Server - SSH target
- Wazuh Manager
- Wazuh Indexer
- Wazuh Dashboard
- Hydra
- OpenSSH

## Attack Simulation

Hydra was used from Kali Linux to perform controlled SSH
authentication attempts against the Ubuntu Server.

Example:

    hydra -l wazuhadmin -P passwords.txt ssh://192.168.8.136

## Log Source

Ubuntu SSH authentication logs:

    /var/log/auth.log

## Wazuh Detection

Wazuh detected failed SSH authentication attempts.

Rule:

    5760

Description:

    sshd: authentication failed

Severity:

    Level 5

MITRE ATT&CK:

    T1110.001 - Password Guessing
    T1021.004 - SSH

## Successful Authentication

The correct password was eventually accepted during the lab
simulation.

Wazuh detected the successful SSH authentication with:

    Rule ID: 5715

    Description: sshd: authentication success

## Investigation

The Wazuh Dashboard was used to investigate:

- Source IP
- Target username
- Authentication result
- Timestamp
- Rule ID
- Severity
- MITRE ATT&CK mapping

## Result

The lab successfully demonstrated the following detection flow:

Kali
↓
Hydra
↓
SSH authentication attempts
↓
Ubuntu /var/log/auth.log
↓
Wazuh
↓
Security alerts
↓
Wazuh Dashboard
