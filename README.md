# 445CyberCo Secure Cloud Infrastructure Design

[cite_start]This project provides a comprehensive security overhaul for **445CyberCo**, transitioning from an insecure, flat network to a modern, cloud-native **Zero-Trust Architecture**[cite: 133, 166, 167]. [cite_start]The design focuses on mitigating high-impact risks through Microsoft-centric security solutions, automated threat modeling, and resilient incident response planning[cite: 167, 204, 393].

---

## Project Overview

[cite_start]The primary goal of this initiative was to identify critical vulnerabilities within the existing 445CyberCo system and propose a secure, scalable system and network design[cite: 11, 117]. [cite_start]We recommended 24 specific security requirements to ensure holistic protection across the enterprise[cite: 118].

### Key Objectives
* [cite_start]**Zero-Trust Implementation:** Establish a "never trust, always verify" environment using **Microsoft Entra ID**[cite: 167].
* [cite_start]**Data Centricity:** Secure sensitive PII and HR data at rest and in transit using Microsoft Purview[cite: 370, 371].
* [cite_start]**Asset Management:** Transition from high-risk BYOD (Bring Your Own Device) to a **COPE** (Corporate Owned Personally Enabled) policy[cite: 26, 362].
* [cite_start]**Resiliency:** Use Chaos Engineering to validate system recovery and maintain strict RPO/RTO standards[cite: 375, 376].

---

## Risk Assessment Summary

[cite_start]We identified five primary risks based on the current 455CyberCo system and used an open-source GitHub risk assessment matrix to generate a heatmap[cite: 11, 12].

| Risk | Description | Mitigation Strategy |
| :--- | :--- | :--- |
| [cite_start]**BYOD Vulnerabilities** [cite: 13] | [cite_start]Insecure staff laptops (unpatched OS, no AV)[cite: 14, 21, 22]. | [cite_start]Implement COPE policy with RBAC and NAC[cite: 26]. |
| [cite_start]**Flat Network** [cite: 30] | [cite_start]Lack of segmentation facilitates lateral movement[cite: 31, 33]. | [cite_start]Implement Zero-Trust architecture and VLAN segmentation[cite: 39, 40]. |
| [cite_start]**MS-Access Database** [cite: 41] | [cite_start]Weak, shared credentials that are easily cracked[cite: 42, 43]. | [cite_start]Migrate to **Azure SQL** with integrated Windows authentication[cite: 48]. |
| [cite_start]**Third-Party Hosting** [cite: 51] | [cite_start]Increased attack surface via accounting firms[cite: 51, 52]. | [cite_start]Use TPRM platforms and require SOC 2 Type II/ISO 27001 reports[cite: 58, 59]. |
| [cite_start]**Vulnerable File Server** [cite: 60] | [cite_start]EOL hardware with unknown vulnerabilities and unencrypted data[cite: 62, 63]. | [cite_start]Migrate to **Azure Files** and enforce BitLocker FDE[cite: 69, 70]. |



---

## System Architecture

[cite_start]The proposed network leverages the Microsoft ecosystem to provide integrated security controls[cite: 166, 167].



### Core Components
* [cite_start]**Identity Management:** **Microsoft Entra ID** serves as the primary Identity and Access Management (IAM) provider, enforcing MFA and device health checks[cite: 167, 170].
* [cite_start]**Compute:** Internal staff perform tasks via **Azure Virtual Desktop**, ensuring work data remains in the cloud if hardware is lost or stolen[cite: 171, 172].
* [cite_start]**Storage:** Data is segmented into Azure File storage with strict access controls for HR and Client data to prevent cross-contamination[cite: 174, 175].
* [cite_start]**Security Monitoring:** **Microsoft Sentinel** (Cloud-Native SIEM) centralizes logs and automates responses via Playbooks (SOAR)[cite: 182, 357, 360].

---

## Threat Modeling

[cite_start]We utilized the **STRIDE** and **CAPEC** frameworks to identify potential attack vectors[cite: 204, 312].

* [cite_start]**Spoofing:** Attackers pretending to be the CEO via phishing or hijacking Entra ID sessions[cite: 207, 209].
* [cite_start]**Information Disclosure:** Disgruntled insiders exfiltrating sensitive client or HR data[cite: 226, 289].
* [cite_start]**CAPEC-123 (Buffer Manipulation):** Manipulation of application buffers to read or modify unintended memory[cite: 322, 327].
* [cite_start]**CAPEC-125 (Flooding):** Denial of Service via rapid, high-volume interactions[cite: 340, 342].

### Automated Analysis
[cite_start]To generate professional reports, we used the **OWASP pytm** framework in a Kali Linux environment[cite: 347, 352].

```bash
# Command to generate the HTML threat modeling report
python tm4.py --report docs/advanced_template.md | pandoc -f markdown-tex_math_dollars -t html > 445CyberCo.html
