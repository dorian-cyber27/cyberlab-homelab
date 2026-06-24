# CyberLab Troubleshooting Log

## Issue 1: Windows Server Reinstallation Loop

### Problem

CYBER-SERVER repeatedly booted into the Windows Server installation process after installation appeared complete.

### Root Cause

The Windows Server ISO remained attached to the virtual optical drive, causing the VM to boot from installation media instead of the virtual hard disk.

### Resolution

Removed the ISO from the virtual optical drive and rebooted the VM.

### Outcome

Windows Server booted normally to the login screen.

---

## Issue 2: Windows 11 and Windows Server Unable to Communicate

### Problem

WIN11-LAB and CYBER-SERVER could not ping each other despite static IP configuration.

### Symptoms

* 100% packet loss
* No successful ICMP communication
* Network adapters appeared connected

### Investigation

* Verified IP addressing
* Verified subnet masks
* Verified Internal Network settings
* Verified routing tables
* Checked ARP entries
* Reviewed Windows Firewall settings

### Root Cause

Windows Firewall was blocking inbound ICMP traffic.

### Resolution

Adjusted firewall rules to allow ICMP communication.

### Outcome

Both systems successfully exchanged ping traffic.

---

## Issue 3: Kali Linux Unable to Reach Other Hosts

### Problem

KALI-LAB could not communicate with either Windows system.

### Symptoms

* Destination Host Unreachable
* ARP entries showed "<incomplete>"
* Route table appeared correct

### Investigation

* Verified static IP configuration
* Verified routing table
* Reviewed ARP table
* Compared VirtualBox adapter settings with working VMs

### Root Cause

KALI-LAB was attached to a NAT network instead of the CyberLab Internal Network.

### Resolution

Changed Adapter 1 from NAT to Internal Network and assigned the network name CyberLab.

### Outcome

KALI-LAB successfully communicated with CYBER-SERVER and WIN11-LAB.

---

## Lessons Learned

* ARP tables are useful for identifying Layer 2 connectivity problems.
* VirtualBox network modes significantly affect VM communication.
* Successful IP configuration does not guarantee network connectivity.
* Firewall rules should be verified early during troubleshooting.
* Methodical troubleshooting is more effective than randomly changing settings.

* ## Skills Practiced

- Network troubleshooting
- TCP/IP configuration
- ARP analysis
- Windows Firewall management
- VirtualBox networking
- Root cause analysis
- Technical documentation
  }
