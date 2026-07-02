# Phase 3: Sysmon Endpoint Telemetry Deployment

## Overview

This phase documents the deployment and validation of Sysmon (System Monitor) across a multi-machine Active Directory homelab environment. The objective was to implement enhanced endpoint visibility through detailed system telemetry collection, enabling future detection engineering and SIEM integration. Sysmon v15.21 was deployed on both a Windows Server Domain Controller and a Windows 11 client machine using the SwiftOnSecurity configuration as a baseline for structured security logging. The environment was built within VirtualBox and includes a Kali Linux machine used for controlled reconnaissance and network testing.

## Environment

The lab consists of the following systems: Windows Server (Domain Controller), Windows 11 Client (Domain-joined workstation), and Kali Linux (used for network testing and simulated attacker activity). All systems operate within an isolated virtual network designed to simulate a small enterprise Active Directory environment.

## Sysmon Deployment

Sysmon was installed on both Windows systems to enable detailed endpoint telemetry collection. Installation was performed using the following command: Sysmon.exe -accepteula -i sysmonconfig-export.xml. The Sysmon configuration was managed using the SwiftOnSecurity Sysmon configuration file, which defines structured logging rules for common security-relevant system behaviors. Configuration updates and validation were performed using: Sysmon.exe -c sysmonconfig-export.xml.

## Telemetry Coverage

Once deployed, Sysmon provided comprehensive endpoint visibility across multiple event categories, including Event ID 1 (Process Creation), Event ID 22 (DNS Query Activity), file creation events, registry modification events, image load events, and network connection activity (dependent on configuration rules). This telemetry enables detailed visibility into process execution, system modifications, and network activity across both virtual machines.

## Validation and Testing

Sysmon logging was validated using Windows Event Viewer at: Applications and Services Logs → Microsoft → Windows → Sysmon → Operational. Event filtering confirmed that Sysmon was actively generating telemetry on both systems. Controlled testing was performed using standard administrative and network tools, including PowerShell Test-NetConnection, Netcat (nc) connection attempts, Nmap TCP scanning and service enumeration, and SMB enumeration using smbclient. These activities successfully generated corresponding Sysmon events, confirming that endpoint telemetry collection was functioning as expected.

## Key Observations

During deployment and validation, it was observed that Sysmon telemetry output is highly dependent on XML configuration structure and rule definitions. Small configuration changes can significantly impact which events are captured or excluded. Key lessons from this phase include: Sysmon configurations must be validated after every change, using a known-good baseline configuration improves stability and predictability, event visibility is controlled explicitly through XML inclusion rules, and Event Viewer filtering is essential for confirming expected telemetry output.

## Outcome

Sysmon was successfully deployed and validated across both virtual machines within the Active Directory lab environment. The system now provides structured endpoint telemetry suitable for security monitoring, detection engineering, behavioral analysis, and future SIEM integration. This deployment forms a foundational layer for the next phase of the project, which focuses on centralized log ingestion, SIEM correlation, and security event analysis using Splunk.
