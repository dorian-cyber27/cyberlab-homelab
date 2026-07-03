# CyberLab Homelab Project

## Overview
CyberLab is a virtual cybersecurity lab built using VirtualBox to simulate a small enterprise network environment. It is designed for hands-on learning in system administration, Active Directory, networking, and security testing.

This project is being built in structured phases to mirror real-world IT infrastructure deployment.

---

## Architecture

The lab consists of three virtual machines:

- **CYBER-SERVER (Windows Server 2022)** → Domain Controller (planned)
- **WIN11-LAB (Windows 11 Pro)** → Client workstation
- **KALI-LAB (Kali Linux XFCE)** → Security testing / attack simulation

---

## Network Design

All machines are connected through a VirtualBox Internal Network:

- **Network Name:** CyberLab  
- **Subnet:** 192.168.50.0/24  

### IP Addressing Scheme

| Machine        | IP Address       | Role |
|----------------|-----------------|------|
| CYBER-SERVER   | 192.168.50.10   | Server / Domain Controller (planned) |
| WIN11-LAB      | 192.168.50.20   | Windows Workstation |
| KALI-LAB       | 192.168.50.30   | Security Testing Machine |

---

## Current Progress

### Phase 1: Virtualization Setup ✅

- [x] Virtual machines created in VirtualBox
- [x] Windows Server 2022 installed
- [x] Windows 11 installed
- [x] Kali Linux installed
- [x] Static IP addressing configured
- [x] Internal networking established (CyberLab)
- [x] Full connectivity verified (ICMP/ping between all systems)

---

### Phase 2: Active Directory Deployment ✅

- [x] Active Directory Domain Services installed
- [x] DNS configured
- [x] Windows Server promoted to Domain Controller
- [x] Domain created (`cyberlab.local`)
- [x] Windows 11 workstation joined to domain
- [x] Active Directory Users and Computers configured
- [x] Domain authentication validated
- [x] Group Policy environment initialized

---

### Phase 3: Sysmon Endpoint Telemetry ✅

- [x] Sysmon v15.21 deployed
- [x] SwiftOnSecurity Sysmon configuration applied
- [x] Configuration validated
- [x] Endpoint telemetry collection verified
- [x] Process Creation (Event ID 1) validated
- [x] File Create (Event ID 11) validated
- [x] Registry events (Event ID 13) validated
- [x] DNS Query events (Event ID 22) validated
- [x] Additional Sysmon operational events validated
- [x] NetworkConnect (Event ID 3) extensively investigated and documented as a current lab limitation

---

### Phase 4: Splunk SIEM Integration ✅

- [x] Splunk Enterprise installed
- [x] Splunk configured on Windows Server 2022
- [x] Sysmon telemetry ingested into Splunk
- [x] Windows Event Log collection configured
- [x] XML event parsing validated
- [x] SPL searches executed successfully
- [x] Endpoint telemetry validated through Splunk
- [x] Ingestion and parsing issues investigated and resolved
- [x] SIEM pipeline documented

---

### Phase 5: Detection Engineering (Next)

- [ ] Build SPL threat hunting queries
- [ ] Detect suspicious PowerShell activity
- [ ] Detect LOLBins (Living-Off-the-Land Binaries)
- [ ] Detect persistence techniques
- [ ] Build Sysmon-based detections
- [ ] Create saved searches and alerts
- [ ] Build SOC dashboards

---

### Phase 6: Offensive Security Validation (Planned)

- [ ] Network enumeration from Kali Linux
- [ ] Service enumeration
- [ ] Nmap scanning validation
- [ ] Simulated attack scenarios
- [ ] Validate SIEM detections
- [ ] Blue Team investigation workflow

---

## Key Skills Demonstrated

### Infrastructure & Systems

- Virtualization (Oracle VirtualBox)
- Windows Server 2022 administration
- Windows 11 administration
- Linux administration (Kali Linux)
- Static IP addressing and network configuration
- Internal virtual network design and implementation
- Network connectivity troubleshooting

### Identity & Access Management

- Active Directory Domain Services (AD DS)
- Domain Controller deployment
- DNS configuration and management
- Domain administration
- Windows domain authentication
- Group Policy fundamentals

### Endpoint Security

- Sysmon deployment and configuration
- Endpoint telemetry collection
- Windows Event Log analysis
- Sysmon event validation
- Endpoint monitoring
- Security telemetry troubleshooting

### SIEM & Log Analysis

- Splunk Enterprise deployment
- SIEM configuration
- Windows Event Log ingestion
- XML event parsing
- Search Processing Language (SPL)
- Security log analysis
- Log pipeline troubleshooting

### Cybersecurity Operations

- Threat telemetry validation
- Root cause analysis
- Security monitoring
- Detection engineering fundamentals
- Security documentation
- Homelab architecture and design

---

## Goal

To build a realistic enterprise cybersecurity homelab that simulates a Windows Active Directory environment with centralized logging, endpoint telemetry, SIEM monitoring, and defensive security operations. The project is designed to develop practical skills in systems administration, blue team operations, detection engineering, threat hunting, and incident investigation while documenting each phase as a professional portfolio.

---

## Status

🟢 Active Development

**Current Phase:** Phase 5 – Detection Engineering

**Completed:**
- ✅ Phase 1 – Virtualization & Network Infrastructure
- ✅ Phase 2 – Active Directory Deployment
- ✅ Phase 3 – Sysmon Endpoint Telemetry
- ✅ Phase 4 – Splunk SIEM Integration

**Next Milestone:**
Build and validate detection rules, threat hunting queries, alerts, and SOC-style dashboards using Splunk and Sysmon telemetry.

## Network Diagram

Below is the current CyberLab architecture showing all virtual machines and their internal network configuration.

![CyberLab Network Diagram](diagrams/cyberlab-network-diagram.png)
