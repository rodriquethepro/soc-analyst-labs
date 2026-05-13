# Active Directory Reconnaissance Investigation

## Platform
TryHackMe

## Room
SOC Level 1 Alert Triage

## Scenario
Investigation of suspicious Active Directory reconnaissance activity on a Microsoft Exchange server.

## Alert Details

- Host: DMZ-MSEXCHANGE-2013
- OS: Windows Server 2012 R2
- User: NT AUTHORITY\SYSTEM
- Source Process: cmd.exe
- Parent Process: revshell.exe
- Grandparent Process: w3wp.exe

  ## Commands Observed

```cmd
dir
hostname
whoami /priv
net group "Domain Admins" /domain
nltest /dclist:tryhackme.thm
```
## Investigation Findings

The investigation revealed suspicious Active Directory enumeration activity originating from a reverse shell process.

The process chain indicated that cmd.exe was spawned by revshell.exe, which originated from the IIS worker process w3wp.exe.

The commands executed are commonly associated with attacker reconnaissance and privilege discovery before lateral movement.

## Analyst Assessment

- Classification: True Positive
- Severity: Critical
- Activity Type: Post-Exploitation / Active Directory Reconnaissance

  ## Recommended Actions

- Isolate affected host
- Quarantine malicious files
- Investigate IIS exploitation
- Review lateral movement activity
- Reset potentially compromised credentials

  ## Skills Practiced

- SOC Alert Triage
- Process Tree Analysis
- Threat Detection
- Active Directory Enumeration Detection
- Incident Investigation
