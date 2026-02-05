# 445CyberCo Secure Cloud Infrastructure Design

This project outlines a comprehensive security transformation for **445CyberCo**, moving from a vulnerable, flat network to a modern **Zero-Trust Architecture** based on the Microsoft cloud ecosystem. The design integrates automated threat modeling, chaos engineering for resiliency, and a structured incident response plan.

---

## ## Project Overview

The objective was to identify critical security gaps in 445CyberCo’s legacy systems and design a scalable, secure architecture. We defined 24 specific security requirements to ensure holistic protection.

### ### Key Objectives
* **Zero-Trust Implementation:** Establish identity-driven security using **Microsoft Entra ID** to ensure all users and devices are authenticated and authorized.
* **Data Centricity:** Protect sensitive PII, HR, and revenue data at rest and in transit via **Microsoft Purview**.
* **Asset Modernization:** Transition from high-risk **BYOD** to a **COPE** (Corporate Owned Personally Enabled) policy with **NAC** (Network Access Control).
* **Resiliency:** Validate system durability against failures using the **Chaos Toolkit**.

---

## ## Risk Assessment & Mitigation

We identified five high-priority risks using an open-source risk assessment matrix.

[Image of a risk assessment heatmap showing impact vs probability]

| Risk | Description | Mitigation Strategy |
| :--- | :--- | :--- |
| **BYOD Vulnerabilities** | Laptops with unpatched OS and no anti-virus increase the attack surface. | Implement COPE policy, RBAC, NAC, and BitLocker FDE. |
| **Flat Network** | Lack of segmentation allows rapid spread of lateral movement attacks. | Implement Zero-Trust architecture and VLAN segmentation. |
| **MS-Access Database** | Insecure database with weak, shared credentials prone to cracking. | Migrate to **Azure SQL** with integrated Windows authentication. |
| **Third-Party Hosting** | Accounting systems hosted by external firms increase supply chain risk. | Monitor via TPRM platform and verify SOC 2 Type II/ISO 27001 compliance. |
| **File Server EOL** | Approaching end-of-life hardware with unencrypted local storage. | Migrate to **Azure Files** and enforce remote wipe via **Intune**. |

---

## ## Proposed System Architecture

The design moves all 445CyberCo operations to the **Microsoft Azure Cloud** to ensure centralized management and visibility.

[Image of a zero trust cloud network diagram featuring Microsoft Entra ID and Azure Virtual Desktop]

### ### Core Security Components
* **Identity & Access Management:** **Microsoft Entra ID** enforces MFA, strong password policies, and device health checks before granting access.
* **Secure Compute:** Staff use **Azure Virtual Desktop**, which keeps sensitive data in the cloud rather than on local hardware.
* **Network Segmentation:** Data for Web Backends, HR, and Clients is segmented into distinct storage vaults to prevent cross-contamination.
* **Centralized Monitoring:** **Microsoft Sentinel** (Cloud-Native SIEM) ingests all logs for automated incident detection and response.

---

## ## Threat Modeling

We used the **STRIDE** and **CAPEC** frameworks to identify and mitigate potential attack vectors
