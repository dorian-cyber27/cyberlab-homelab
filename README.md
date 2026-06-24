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

### Phase 1: Virtualization Setup
- [x] Virtual machines created in VirtualBox
- [x] Operating systems installed (Windows Server, Windows 11, Kali Linux)
- [x] Static IP addressing configured
- [x] Internal networking established (CyberLab)
- [x] Full connectivity verified (ICMP/ping between all systems)

### Phase 2: Active Directory Setup (In Progress)
- [ ] Install Active Directory Domain Services
- [ ] Configure DNS
- [ ] Promote CYBER-SERVER to Domain Controller
- [ ] Create domain: cyberlab.local
- [ ] Join WIN11-LAB to domain

### Phase 3: Security Testing (Planned)
- [ ] Network enumeration with Kali Linux
- [ ] Service scanning and analysis
- [ ] Active Directory attack/defense simulations

---

## Key Skills Demonstrated
- Virtualization (VirtualBox)
- Network configuration (static IPs, internal networking)
- Windows Server fundamentals
- Linux system usage (Kali Linux)
- Basic troubleshooting of network connectivity
- Cybersecurity lab design

---

## Goal
To build a realistic Active Directory environment for learning enterprise IT administration, blue team operations, and security testing workflows.

---

## Status
Active development — Phase 2 in progress
