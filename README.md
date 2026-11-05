# 🛡️ Automated Security Monitoring & Incident Response Platform

**An Integrated SIEM, SOAR, Threat Intelligence & Automated Incident Response System**

![Project Status](https://img.shields.io/badge/Status-In%20Development-orange)
![SIEM](https://img.shields.io/badge/SIEM-Wazuh-blue)
![SOAR](https://img.shields.io/badge/SOAR-Shuffle-purple)
![Incident Management](https://img.shields.io/badge/Incident%20Management-TheHive-red)
![Platform](https://img.shields.io/badge/Endpoint-Windows%2010-0078D6)

## 📌 Overview

This project focuses on developing an integrated **Security Operations Center (SOC) automation environment** by combining Security Information and Event Management (SIEM), Security Orchestration, Automation and Response (SOAR), threat intelligence, and incident management technologies.

The platform integrates **Wazuh, Shuffle, TheHive, and external Open Source Intelligence (OSINT) sources** to establish an automated security monitoring and incident response workflow.

The system monitors endpoint activities, detects suspicious events, forwards security alerts for automated processing, enriches Indicators of Compromise (IOCs) with threat intelligence, and creates incident cases for investigation.

It also incorporates automated response capabilities to execute predefined actions on monitored endpoints, reducing manual intervention during security incident handling.

The ultimate goal is to demonstrate how multiple open-source cybersecurity technologies can work together to create a centralised and automated SOC environment.

## 🏗️ System Architecture

The following diagram illustrates the proposed architecture and communication flow between the integrated security components.

![System Architecture](docs/topology.png)

### Architecture Components

| Component | Technology | Responsibility |
|---|---|---|
| Endpoint | Windows 10 | Generates system and security events |
| Endpoint Agent | Wazuh Agent | Collects and forwards endpoint events |
| SIEM | Wazuh Manager | Analyses events and generates security alerts |
| SOAR | Shuffle | Orchestrates automated security workflows |
| Threat Intelligence | OSINT | Enriches IOCs with external intelligence |
| Incident Management | TheHive | Creates and manages security incident cases |
| Notification | Email | Delivers security alerts to SOC analysts |
| Security Analyst | SOC Analyst | Reviews incidents and oversees response actions |

## 🔄 How It Works

The platform follows an automated security monitoring and incident response workflow.

### 1. Endpoint Event Collection

**Technology: Wazuh Agent | Windows 10**

- A Wazuh Agent is deployed on the Windows 10 endpoint.
- The agent monitors system activities and collects security-related events.
- Collected events are forwarded to the Wazuh Manager for analysis.

### 2. Security Event Analysis

**Technology: Wazuh Manager**

- The Wazuh Manager receives events from monitored endpoints.
- Its detection engine evaluates events against configured security rules.
- Suspicious activities trigger security alerts.
- Relevant alerts are forwarded to Shuffle for automated processing.

### 3. Security Alert Orchestration

**Technology: Shuffle SOAR**

- Shuffle receives security alerts from Wazuh.
- The workflow extracts relevant information from incoming alerts.
- Alert information is processed according to predefined automation rules.
- The workflow determines which integrations and response actions should be triggered.

### 4. Threat Intelligence Enrichment

**Technology: Shuffle + OSINT**

- Shuffle extracts available Indicators of Compromise (IOCs) from security alerts.
- Relevant indicators, such as IP addresses, domains, and file hashes, are submitted to external OSINT services.
- Threat intelligence information is retrieved to provide additional context.
- Enrichment results help analysts understand the potential risk associated with suspicious indicators.

### 5. Incident Case Creation

**Technology: Shuffle + TheHive**

- Shuffle forwards relevant security alerts and enrichment information to TheHive.
- TheHive automatically creates an incident case.
- Incident information is organised for investigation and tracking.
- SOC analysts can review the case, investigate findings, and manage remediation activities.

### 6. Email Notification

**Technology: Shuffle + Email**

- Shuffle triggers email notifications based on configured alert conditions.
- The notification contains relevant security alert information.
- SOC analysts receive notifications to review and investigate potential incidents.

### 7. Automated Incident Response

**Technology: Wazuh Active Response**

- Based on predefined conditions, Shuffle can initiate an approved response workflow.
- Wazuh Active Response executes configured actions on the monitored Windows endpoint.
- Response actions may include blocking malicious IP addresses or other predefined remediation activities.
- The objective is to reduce the time between threat detection and response.

**Note:** Automated response actions will be implemented with appropriate validation and safeguards to minimise false positives and unintended system disruption.

## ⚙️ Technology Stack

| Technology | Category | Usage |
|---|---|---|
| [Wazuh](https://wazuh.com/) | SIEM / XDR | Endpoint monitoring, security event analysis and active response |
| [Shuffle](https://shuffler.io/) | SOAR | Security workflow automation and tool integration |
| [TheHive](https://thehive-project.org/) | Incident Management | Security incident creation, investigation and case management |
| [OSINT](https://www.virustotal.com/) | Threat Intelligence | IOC reputation analysis and threat enrichment |
| Windows 10 | Operating System | Monitored endpoint |
| Email | Notification | Security alert delivery |

## ✨ Key Features

- **Centralised Security Monitoring** – Collect and analyse endpoint security events through Wazuh.
- **Automated Alert Processing** – Forward and process security alerts using Shuffle SOAR.
- **IOC Threat Intelligence Enrichment** – Enrich suspicious indicators using external OSINT services.
- **Automated Incident Management** – Create and organise incident cases in TheHive.
- **SOC Email Notifications** – Notify analysts when configured security events occur.
- **Automated Endpoint Response** – Execute predefined remediation actions through Wazuh Active Response.
- **Security Tool Integration** – Connect multiple open-source security solutions into a unified workflow.
- **Reduced Manual Intervention** – Automate repetitive SOC tasks and improve incident handling efficiency.

## 🎯 Project Objectives

1. **Centralised Monitoring:** Establish an endpoint security monitoring environment using Wazuh to collect and analyse security events.
2. **Workflow Automation:** Integrate Shuffle SOAR to automate security alert processing and incident response workflows.
3. **Threat Intelligence:** Implement IOC enrichment using external OSINT sources to provide additional threat context.
4. **Incident Management:** Integrate TheHive to automate incident creation and support incident investigation.
5. **Security Notifications:** Implement automated email notifications to improve SOC analyst awareness.
6. **Automated Response:** Configure predefined endpoint response actions to handle selected security threats.

## 🧪 Planned Testing Scenarios

The following scenarios will be used to evaluate the system during implementation.

| Test Scenario | Expected Result |
|---|---|
| Multiple failed login attempts | Wazuh detects suspicious authentication activity |
| Suspicious PowerShell execution | Wazuh generates a security alert |
| Suspicious IP address detected | Shuffle extracts and enriches the IOC |
| Malicious indicator identified | Threat intelligence results are included in the workflow |
| Security alert received | TheHive automatically creates an incident case |
| High-priority alert detected | SOC analyst receives an email notification |
| Approved response condition triggered | Wazuh executes the configured endpoint response |

## 🚀 Implementation Roadmap

The project will be developed incrementally to ensure that each component functions correctly before integrating the complete workflow.

- [ ] **Phase 1 – Environment Setup**
  - [ ] Prepare Windows 10 endpoint.
  - [ ] Deploy Wazuh Manager.
  - [ ] Install and configure Wazuh Agent.
  - [ ] Verify endpoint event collection.

- [ ] **Phase 2 – SOAR Integration**
  - [ ] Deploy Shuffle SOAR.
  - [ ] Configure Wazuh alert forwarding.
  - [ ] Establish communication between Wazuh and Shuffle.
  - [ ] Build initial automation workflows.

- [ ] **Phase 3 – Threat Intelligence Integration**
  - [ ] Identify suitable OSINT services.
  - [ ] Configure API integrations.
  - [ ] Implement IOC extraction.
  - [ ] Implement automated IOC enrichment.

- [ ] **Phase 4 – Incident Management**
  - [ ] Deploy TheHive.
  - [ ] Integrate Shuffle with TheHive.
  - [ ] Configure automated incident case creation.
  - [ ] Verify incident information and enrichment results.

- [ ] **Phase 5 – Notification & Response**
  - [ ] Configure email notification workflows.
  - [ ] Integrate Wazuh Active Response.
  - [ ] Implement predefined response conditions.
  - [ ] Validate response actions on the endpoint.

- [ ] **Phase 6 – Testing & Evaluation**
  - [ ] Execute security testing scenarios.
  - [ ] Verify end-to-end automation.
  - [ ] Evaluate alert processing and response accuracy.
  - [ ] Document findings and implementation results.

## 📁 Repository Structure

```text
Automated-Security-Monitoring/
│
├── README.md
│
├── docs/
│   ├── topology.png
│   ├── architecture.md
│   └── screenshots/
│
├── wazuh/
│   ├── configuration/
│   ├── rules/
│   └── active-response/
│
├── shuffle/
│   └── workflows/
│
├── thehive/
│   └── configuration/
│
├── scripts/
│   └── testing/
│
└── reports/
    └── test-results.md
```

## 🔐 Security Considerations

Security and reliability are important considerations throughout the development of this platform.

- **Credential Protection:** API keys, passwords, and authentication tokens must be stored securely and excluded from version control.
- **Access Control:** Restrict access to security management interfaces and administrative functions.
- **Response Validation:** Validate alerts and response conditions before executing potentially disruptive actions.
- **Auditability:** Maintain records of automated workflows and endpoint response activities.
- **Endpoint Protection:** Conduct testing only on authorised systems and isolated laboratory environments.
- **False Positive Management:** Apply appropriate detection thresholds and validation mechanisms to minimise unnecessary response actions.

## 📊 Expected Outcome

Upon completion, the project is expected to demonstrate a functional automated SOC environment capable of:

- Monitoring endpoint activities and detecting suspicious behaviour.
- Processing and orchestrating security alerts automatically.
- Enriching suspicious indicators using external threat intelligence.
- Creating and managing security incident cases.
- Delivering automated notifications to SOC analysts.
- Executing predefined endpoint response actions.

By integrating SIEM, SOAR, threat intelligence, and incident management technologies, this project demonstrates a practical approach to improving security operations through automation.

## ⚠️ Disclaimer

This project is developed for educational, research, and cybersecurity laboratory purposes.

All security testing, monitoring, and automated response activities must be conducted on systems for which proper authorisation has been obtained.

---

**Project Status:** In Development

**Domain:** Cybersecurity | Security Operations | SIEM | SOAR | Incident Response

**Core Technologies:** Wazuh · Shuffle · TheHive · OSINT
