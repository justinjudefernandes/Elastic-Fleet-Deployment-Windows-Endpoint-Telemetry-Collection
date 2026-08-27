# Elastic Fleet Deployment & Windows Endpoint Telemetry Collection

## 🎯 Objective:
Deploy and configure Elastic Security to centrally monitor a Windows endpoint, collect security telemetry from Sysmon and Windows Defender, and make the data available for investigation and analysis.

## 📊 Project Overview:
Provisioned a Windows 11 endpoint and an Ubuntu-based Fleet Server, then used Elastic Fleet to centrally enroll and manage the Windows Elastic Agent. Sysmon was installed and configured using Olaf Hartong's community-maintained Sysmon configuration to expand Windows endpoint visibility. Custom Windows Event Log integrations were configured through Elastic Agent to collect Sysmon and Windows Defender telemetry and forward the events to Elasticsearch, with end-to-end telemetry collection validated through Kibana Discover.

## 🧰 Tools Used:
- VMware (Virtualization)
- Windows 11 – Monitored Endpoint
- Ubuntu Server 22.04.4 – Fleet Server
- Elastic Stack (Elasticsearch, Kibana)
- Elastic Fleet & Elastic Agent
- Microsoft Sysmon v15.21
- Olaf Hartong's Sysmon Configuration
- Windows Defender
- Windows Event Viewer

## 🛠️ Capabilities Demonstrated:
- Elastic Stack architecture and Fleet Server deployment
- Centralized agent management vs. standalone deployment models
- Elastic Agent installation, enrollment, and policy management
- Windows endpoint onboarding and telemetry collection
- Sysmon deployment and advanced configuration
- Custom Windows Event Log integration design
- Security event filtering and scoping by Event ID
- Windows Defender security event collection and analysis
- Centralized log ingestion and validation using Kibana Discover
- Endpoint security monitoring and visibility engineering

## 📁 Key Deliverables:
- Provisioned a Windows 11 endpoint virtual machine for security monitoring
- Deployed and configured an Elastic Fleet Server on Ubuntu 22.04.4
- Successfully enrolled and centrally managed the Windows 11 Elastic Agent through Fleet
- Installed and configured Sysmon using Olaf Hartong's community-maintained configuration
- Verified Sysmon service operation and security event generation
- Created a dedicated Windows agent policy (`MYDFIR-Windows-policy`)
- Built a custom Windows Event Log integration for Sysmon Operational logs
- Built a targeted Windows Defender Event Log integration for security-relevant events
- Configured collection of Windows Defender Event IDs 1116, 1117, and 5001
- Verified centralized Sysmon and Windows Defender telemetry in Kibana Discover

## 🔍 Steps Performed:
### 1. Endpoint Provisioning
- Provisioned a Windows 11 virtual machine to serve as the monitored endpoint.
- Installed VMware Tools to support endpoint management and VM operations.
- Captured a VM snapshot to provide a recovery and rollback point.

### 2. Fleet Architecture Planning
- Evaluated standalone Elastic Agent deployment against Fleet Server-managed deployment.
- Selected the Fleet Server architecture to provide centralized agent enrollment, policy deployment, configuration management, and endpoint health monitoring.

### 3. Fleet Server Deployment
- Provisioned an Ubuntu Server 22.04.4 virtual machine to host the Fleet Server.
- Generated a Fleet Server policy through the Elastic Fleet interface.
- Deployed the Fleet Server using the generated enrollment command.
- Verified successful Fleet Server connectivity and registration within the Elastic dashboard.

### 4. Windows Elastic Agent Enrollment
- Generated a Windows Elastic Agent enrollment package through Fleet.
- Configured Fleet Server communication using port `8220`.
- Deployed the Elastic Agent on the Windows 11 endpoint.
- Verified successful agent enrollment and connectivity within Fleet.
- Confirmed that Windows endpoint telemetry was being received and indexed in Elasticsearch.

### 5. Sysmon Deployment & Configuration
- Reviewed Sysmon capabilities, including process creation, network connections, image loading, process access, and DNS query monitoring.
- Downloaded Sysmon v15.21 from Microsoft's official Sysinternals resource.
- Applied Olaf Hartong's community-maintained Sysmon configuration to expand detection-relevant Windows telemetry.
- Installed Sysmon using an elevated PowerShell session.
- Verified Sysmon service operation through Windows Services.
- Confirmed Sysmon event generation through Windows Event Viewer.

### 6. Elastic Agent Policy Management
- Created a dedicated Windows agent policy named `MYDFIR-Windows-policy`.
- Configured the policy to centrally manage telemetry collection for the Windows endpoint.
- Migrated the Windows 11 endpoint to the dedicated policy.

### 7. Sysmon Log Ingestion
- Created a custom Windows Event Log integration named `MYDFIR-Win-Sysmon`.
- Identified the correct Sysmon Operational channel through Windows Event Viewer.
- Configured Elastic Agent to collect events from the Sysmon Operational channel.
- Applied the integration to the Windows agent policy.
- Verified that Sysmon events were successfully ingested into Elasticsearch.

### 8. Windows Defender Log Ingestion
- Created a custom Windows Event Log integration for Windows Defender security telemetry.
- Scoped collection to selected high-value security events:
  - **1116** – Malware/threat detected
  - **1117** – Threat remediation or blocking action taken
  - **5001** – Real-time protection disabled
- Applied the integration to the Windows agent policy.
- Verified that the selected Windows Defender events were successfully collected and indexed.

### 9. Validation
- Confirmed that Sysmon telemetry was being received and indexed in Elasticsearch.
- Confirmed that the selected Windows Defender events were being collected and indexed.
- Used Kibana Discover to search and validate the collected endpoint telemetry.
- Verified the complete telemetry flow from the Windows endpoint through Elastic Agent and Fleet to Elasticsearch and Kibana.
