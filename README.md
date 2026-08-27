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

📌 Refer to the below screenshots: (left to right)
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/e289227d-63a1-4935-87ec-13d61c7b8b00" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/d32f0f39-90c8-470e-a416-b0b12a7653f1" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/7ca30d3d-c8be-44fc-a0a9-0bfd10008578" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/037f8ece-252f-4866-a701-d83406611fca" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/893a2743-1790-474d-9c78-c98f3df8657e" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/8b49e508-d5d0-471d-9711-39e7ca1d8046" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/b53d5122-b002-47f0-8dec-f4e49efbc021" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/bd86639b-6585-42bd-b491-1ec453b66c57" />

### 4. Windows Elastic Agent Enrollment
- Generated a Windows Elastic Agent enrollment package through Fleet.
- Configured Fleet Server communication using port `8220`.
- Deployed the Elastic Agent on the Windows 11 endpoint.
- Verified successful agent enrollment and connectivity within Fleet.
- Confirmed that Windows endpoint telemetry was being received and indexed in Elasticsearch.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/be0030dd-b4db-4de5-9b07-9ae2b59da3a7" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/01813f2c-8ccc-4dca-b30c-967d7973439e" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f4e8edc9-88ab-4d80-989e-0486412dea2c" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/bd3fa237-a125-440e-8f89-758cd8569871" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/eaa623cb-9733-4114-9378-7ea6f10fd36f" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/126783c5-9766-4dd3-80c3-e26d229ed3be" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/f3fa7085-7d85-4be3-b314-729dbbeed29b" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/7b93586d-0890-47e6-978e-0a12873a5ea5" />
<img width="785" height="230" alt="image" src="https://github.com/user-attachments/assets/6d99fb17-1fd2-4702-8884-68946f5b1d58" />

### 5. Sysmon Deployment & Configuration
- Reviewed Sysmon capabilities, including process creation, network connections, image loading, process access, and DNS query monitoring.
- Downloaded Sysmon v15.21 from Microsoft's official Sysinternals resource.
- Applied Olaf Hartong's community-maintained Sysmon configuration to expand detection-relevant Windows telemetry.
- Installed Sysmon using an elevated PowerShell session.
- Verified Sysmon service operation through Windows Services.
- Confirmed Sysmon event generation through Windows Event Viewer.

📌 Refer to the below screenshots: (left to right)

<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/abc45a6f-f308-4b63-9036-2e90fa40a4d1" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/df7310c6-916d-4b09-ab4f-c2f8f1e15c93" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/b1a6978f-aced-42b0-8f62-44b152f44bcb" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/23c6f6a5-520f-489b-9d8f-4fe9dde9f6f5" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/4bff148e-b358-47f2-93f8-f3ba050954d2" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/9daacf06-425e-403c-8aaa-fbc7989d3ff3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/22302ca4-ae05-4dba-946a-97742cb886b6" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/13d01601-8ddf-4b1e-9193-2e72e1635463" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/78a7b1d4-95f7-45de-b5ba-1c0cac70630e" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/47ee04ae-2f8c-4476-8bf7-fe30bdcc1dd3" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/80bdedcc-530c-4dac-8e70-247b8e0b4b4a" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/efb2fa0d-327f-44a0-9e55-56085d045063" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/d45f43be-6901-41a4-addc-166e2a181b35" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/77882ede-aba7-4dd1-b73a-35206c11a9a1" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/013f0804-9231-423c-9749-09fe3c6f6ce6" />
<img width="390" height="230" alt="image" src="https://github.com/user-attachments/assets/75d4a90d-65b1-4ede-9c61-845ea12fe700" />

### 6. Elastic Agent Policy Management
- Created a dedicated Windows agent policy named `MYDFIR-Windows-policy`.
- Configured the policy to centrally manage telemetry collection for the Windows endpoint.
- Migrated the Windows 11 endpoint to the dedicated policy.

📌 Refer to the below screenshots: (left to right)


### 7. Sysmon Log Ingestion
- Created a custom Windows Event Log integration named `MYDFIR-Win-Sysmon`.
- Identified the correct Sysmon Operational channel through Windows Event Viewer.
- Configured Elastic Agent to collect events from the Sysmon Operational channel.
- Applied the integration to the Windows agent policy.
- Verified that Sysmon events were successfully ingested into Elasticsearch.

📌 Refer to the below screenshots: (left to right)


### 8. Windows Defender Log Ingestion
- Created a custom Windows Event Log integration for Windows Defender security telemetry.
- Scoped collection to selected high-value security events:
  - **1116** – Malware/threat detected
  - **1117** – Threat remediation or blocking action taken
  - **5001** – Real-time protection disabled
- Applied the integration to the Windows agent policy.
- Verified that the selected Windows Defender events were successfully collected and indexed.

📌 Refer to the below screenshots: (left to right)


### 9. Validation
- Confirmed that Sysmon telemetry was being received and indexed in Elasticsearch.
- Confirmed that the selected Windows Defender events were being collected and indexed.
- Used Kibana Discover to search and validate the collected endpoint telemetry.
- Verified the complete telemetry flow from the Windows endpoint through Elastic Agent and Fleet to Elasticsearch and Kibana.

📌 Refer to the below screenshots: (left to right)


