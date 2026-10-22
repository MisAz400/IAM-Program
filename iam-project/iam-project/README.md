# Enterprise IAM Program — Contoso Financial Services

**Author:** Mishal Luce | [linkedin.com/in/mishalluce](https://linkedin.com/in/mishalluce) | [github.com/MisAz400](https://github.com/MisAz400)

---

## Overview

This project documents a complete Identity and Access Management (IAM) program designed for **Contoso Financial Services**, a fictional mid-sized financial services company with 300 employees across three departments: Finance, Operations, and IT.

The program is built on **Microsoft Entra ID (Azure AD)** and follows **Zero Trust** principles — verify explicitly, use least privilege access, and assume breach.

---

## What This Project Covers

| Document | Description |
|---|---|
| [Role Definitions](roles/role-definitions.md) | RBAC roles defined for each department and function |
| [Access Control Policy](policies/access-control-policy.md) | Who gets access to what, and how access is granted |
| [MFA Policy](policies/mfa-policy.md) | Multi-factor authentication requirements by role |
| [Onboarding Procedure](procedures/onboarding.md) | Step-by-step identity provisioning for new hires |
| [Offboarding Procedure](procedures/offboarding.md) | Account deprovisioning and access removal |
| [Access Review Procedure](procedures/access-review.md) | Quarterly access review process |

---

## Company Profile

**Contoso Financial Services**
- 300 employees
- Departments: Finance, Operations, IT
- Environment: Microsoft 365 E3, Microsoft Entra ID P2
- Compliance requirements: SOC 2, PCI-DSS
- Work model: Hybrid (office + remote)

---

## IAM Principles

This program is built on three core principles:

**1. Least Privilege** — Users receive only the access required to perform their job. No standing admin rights. Access is scoped to the minimum necessary.

**2. Zero Trust** — No user or device is trusted by default, even on the corporate network. Every access request is verified through identity, device compliance, and location signals.

**3. Lifecycle Management** — Access is provisioned on day one and fully deprovisioned on the last day. Quarterly reviews catch access that has drifted beyond what a role requires.

---

## Technologies Referenced

- Microsoft Entra ID (Azure AD)
- Microsoft Entra ID P2 (Privileged Identity Management, Identity Protection)
- Conditional Access Policies
- Role-Based Access Control (RBAC)
- Microsoft 365
- Microsoft Defender for Identity

---

## Skills Demonstrated

- Identity and Access Management program design
- RBAC role modeling
- Zero Trust policy application
- Onboarding and offboarding process design
- Access review governance
- Microsoft Entra ID / Azure AD concepts
- SC-900 and SC-300 level identity concepts
