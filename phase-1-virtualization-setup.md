# Phase 1: Virtualization Setup (CyberLab Homelab)

**Project:** CyberLab  
**Author:** Dorian Arcia
**Tools:** VirtualBox, Windows Server 2022, Windows 11, Kali Linux  
**Status:** Complete

## Overview
This phase focused on building the virtual environment using Oracle VirtualBox and preparing the base infrastructure for a cybersecurity lab.

## Tools Used
- Oracle VirtualBox
- Windows Server 2022 Evaluation
- Windows 11 ISO
- Kali Linux ISO

## Virtual Machines Created
- CYBER-SERVER (Windows Server 2022)
- WIN11-LAB (Windows 11 Pro)
- KALI-LAB (Kali Linux XFCE)

## Key Configurations

### Virtual Network
- Type: Internal Network
- Name: CyberLab

### IP Addressing Scheme
- CYBER-SERVER: 192.168.50.10
- WIN11-LAB: 192.168.50.20
- KALI-LAB: 192.168.50.30

### VM Settings
- All machines configured with static IP addresses
- Adapter type: Intel PRO/1000 MT Desktop
- Promiscuous mode: Deny
- Cable connected enabled

## Issues Resolved
- Incorrect ISO selection during Windows Server setup
- VirtualBox boot order and ISO attachment issues
- Kali VM initially attached to NAT instead of Internal Network
- Firewall configuration blocking ICMP traffic between hosts

## Final Result
All three VMs successfully communicate via ICMP (ping) within the CyberLab internal network.

## Status
Phase 1 complete — stable multi-VM network established.
