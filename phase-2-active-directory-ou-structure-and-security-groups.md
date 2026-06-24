# Phase 2: Active Directory OU Structure and Security Groups

## Overview

In this phase of my cybersecurity homelab, I designed and implemented a structured Active Directory environment within my Windows Server 2022 domain. The primary objective was to organize domain resources using Organizational Units (OUs), create realistic enterprise user and computer objects, establish security groups for future access control, and prepare the environment for Group Policy deployment, security monitoring, and attack simulation activities.

This phase focused on building the administrative foundation of the domain and learning how enterprise Active Directory environments are organized and managed.

---

## Objectives

* Create a structured Organizational Unit (OU) hierarchy.
* Separate users, computers, groups, and lab resources into logical administrative containers.
* Create realistic enterprise user accounts.
* Create security groups to support future access control implementation.
* Build a sandbox environment for testing and security simulations.
* Troubleshoot common Active Directory administrative issues.

---

## Lab Environment

### Infrastructure

* Domain: `cyberlab.local`
* Domain Controller: Windows Server 2022
* Workstation: Windows 11
* Attacker VM: Kali Linux

### Tools Used

* Active Directory Users and Computers (ADUC)
* Windows PowerShell
* Active Directory Domain Services (AD DS)

---

## Organizational Unit Structure

A dedicated top-level Organizational Unit named **CYBERLAB** was created beneath the domain root to separate custom lab resources from default Active Directory objects.

### Final OU Structure

```text
cyberlab.local
│
├── CYBERLAB
│   ├── Users
│   │   ├── SOC_Analysts
│   │   ├── Helpdesk
│   │   ├── IT_Admins
│   │   ├── Service_Accounts
│   │   └── Standard_Users
│   │
│   ├── Computers
│   │   ├── Workstations
│   │   ├── Servers
│   │   └── SOC_Tools
│   │
│   ├── Groups
│   │   ├── Security_Groups
│   │   ├── Access_Control
│   │   ├── Admin_Groups
│   │   └── ReadOnly_Groups
│   │
│   └── Sandbox
│       ├── Test_Users
│       ├── Test_Computers
│       ├── Broken_GPO_Lab
│       └── Misconfig_Lab
│
├── Builtin
├── Computers
├── Domain Controllers
├── ForeignSecurityPrincipals
├── Managed Service Accounts
└── Users
```

---

## User Accounts Created

To simulate a realistic enterprise environment, several user accounts were created to represent common organizational roles.

### SOC Analysts

* analyst1
* analyst2

### Help Desk

* helpdesk1
* helpdesk2

### IT Administration

* itadmin1

### Service Accounts

* svc-siem
* svc-monitoring

### Sandbox Accounts

* phishing-test-user

### Purpose

These accounts will be used in future exercises involving:

* Authentication monitoring
* Account lockout investigations
* Password policy testing
* Privilege escalation scenarios
* Incident response simulations

---

## Security Groups Created

Security groups were created to establish the foundation for future Role-Based Access Control (RBAC) implementation and permission management.

### SOC Groups

* SOC_ReadOnly
* SOC_Tier1
* SOC_Tier2
* SOC_Manager

### Administrative Groups

* Helpdesk_Tier1
* Endpoint_Admins
* Domain_Admins_Lab

### Monitoring and Logging Groups

* SIEM_ReadAccess
* Log_Collectors

### Purpose

These groups were created to support:

* Future permission assignment
* Role-based administration
* Group Policy targeting
* Least privilege access models
* Enterprise-style access management

At this stage, permissions have not yet been assigned through these groups. The groups serve as the foundation for future access control implementation.

---

## Computer Objects Created

### Workstations

* WIN10-USER01
* WIN10-USER02

### Servers

* FILESERVER01
* APPSERVER02

### SOC Infrastructure

* SIEM-SERVER
* LOG-SERVER
* FORENSICS-BOX

### Sandbox Systems

* ATTACKER-VM

### Purpose

These computer objects simulate a small enterprise network and will later be used for:

* Event generation
* Security monitoring
* Log collection
* Detection engineering exercises
* Incident response simulations

---

## Sandbox Environment

A dedicated Sandbox OU was created to provide a safe environment for testing security controls and troubleshooting configurations.

### Test_Users

Used for:

* Password testing
* Authentication testing
* Account lockout simulations

### Test_Computers

Used for:

* Attack simulations
* Event generation
* Security testing

### Broken_GPO_Lab

Reserved for:

* Group Policy troubleshooting
* Policy conflict testing
* Administrative recovery exercises

### Misconfig_Lab

Reserved for:

* Permission misconfigurations
* Excessive privilege testing
* Security auditing exercises

---

## Challenges Encountered

### Users Container vs Organizational Units

#### Issue

Initially attempted to create Organizational Units within the default Active Directory Users container.

#### Cause

The default Users object visually resembles an Organizational Unit but is actually a legacy Active Directory container.

#### Resolution

After investigating the issue, I learned the distinction between:

* Containers (CN=Users)
* Organizational Units (OU)

A dedicated CYBERLAB Organizational Unit was created beneath the domain root and used as the primary administrative structure for the lab.

#### Lesson Learned

Not every folder-like object displayed in Active Directory Users and Computers is an Organizational Unit.

---

### Domain Administrator Verification

#### Issue

Encountered permission-related errors while attempting to manage Active Directory objects.

#### Investigation

Verified administrative privileges using:

```powershell
whoami
whoami /groups
```

Confirmed membership within the Domain Admins group.

#### Resolution

Determined that permissions were functioning correctly and that the issue stemmed from Active Directory object placement rather than insufficient privileges.

#### Lesson Learned

Always verify group membership and effective permissions before troubleshooting administrative access issues.

---

### Locating the CYBERLAB OU

#### Issue

The CYBERLAB Organizational Unit appeared to be missing from Active Directory Users and Computers.

#### Investigation

Queried Active Directory directly using:

```powershell
Get-ADOrganizationalUnit -Filter *
```

#### Resolution

Verified that the CYBERLAB OU existed and refreshed the ADUC console. The Organizational Unit then appeared correctly beneath the domain root.

#### Lesson Learned

PowerShell can provide a more reliable view of Active Directory objects than relying solely on graphical management tools.

---

## Key Concepts Learned

### Organizational Units vs Containers

* Containers are legacy Active Directory objects.
* Organizational Units are designed for administration, delegation, and Group Policy application.

### Security Groups

Security groups provide a scalable method for organizing users and preparing for future access control implementation.

### Active Directory Troubleshooting

PowerShell can be used to validate Active Directory objects and administrative privileges when graphical tools provide unclear results.

### Enterprise Organizational Design

A structured OU hierarchy simplifies:

* User management
* Computer administration
* Group Policy deployment
* Security monitoring
* Incident response activities

---

## Outcome

Successfully designed and implemented a structured Active Directory environment that mirrors many organizational practices found in enterprise environments.

The environment now includes:

* Logical Organizational Unit segmentation
* Enterprise-style user organization
* Security group foundations for future access control
* Dedicated workstation, server, and SOC infrastructure objects
* Sandbox environments for testing and troubleshooting
* Infrastructure prepared for Group Policy deployment and security monitoring

---

## Next Steps

* Configure Group Policy Objects (GPOs)
* Implement password and account lockout policies
* Enable advanced Windows auditing
* Configure Windows Event Logging
* Deploy Sysmon
* Install and configure Wazuh
* Generate and investigate security events
* Begin implementing access controls using security groups
* Develop SOC-style detection and response scenarios
