# Role Definitions — Contoso Financial Services

## Overview

Contoso Financial Services uses Role-Based Access Control (RBAC) to assign access based on job function. Every employee is assigned one primary role in Microsoft Entra ID. Access to systems and data is granted through group membership tied to that role — not assigned to individuals directly.

---

## Role Matrix

| Role | Department | Entra ID Group | Access Level |
|---|---|---|---|
| Finance Analyst | Finance | GRP-Finance-Analyst | Finance applications, read-only reporting |
| Finance Manager | Finance | GRP-Finance-Manager | Finance applications, full read/write, approval workflows |
| Operations Coordinator | Operations | GRP-Ops-Coordinator | Operations tools, ticketing system, shared drives |
| Operations Manager | Operations | GRP-Ops-Manager | Operations tools, reporting, team management tools |
| IT Support Technician | IT | GRP-IT-Support | Helpdesk tools, endpoint management, user account support |
| IT Administrator | IT | GRP-IT-Admin | Full Microsoft 365 administration, Entra ID management |
| Global Administrator | IT (restricted) | GRP-IT-GlobalAdmin | Emergency break-glass only — see PIM policy |
| All Employees | All | GRP-AllEmployees | Microsoft 365 (Outlook, Teams, SharePoint intranet, OneDrive) |

---

## Role Descriptions

### Finance Analyst
Employees who prepare, analyze, and report on financial data.

**Access includes:**
- Accounting and ERP software (read/write to assigned cost centers)
- Finance SharePoint site (read/write)
- Shared Finance OneDrive folder (read/write)
- Power BI Finance reports (read)
- Microsoft 365 standard apps

**Access excluded:**
- HR systems
- IT administration tools
- Executive reporting dashboards

---

### Finance Manager
Senior finance employees who approve transactions and manage reporting.

**Access includes:**
- All Finance Analyst access
- Transaction approval workflows
- Full Finance SharePoint site (owner)
- Executive financial dashboards (read)
- Ability to request temporary elevated access via PIM for audit purposes

---

### Operations Coordinator
Employees who manage day-to-day operational workflows and logistics.

**Access includes:**
- Operations ticketing and workflow system
- Shared Operations SharePoint site (read/write)
- Microsoft 365 standard apps

**Access excluded:**
- Financial systems
- HR systems
- IT administration tools

---

### Operations Manager
Senior operations employees who oversee teams and reporting.

**Access includes:**
- All Operations Coordinator access
- Operations reporting dashboards
- Team management tools
- Ability to approve access requests for direct reports

---

### IT Support Technician
Help desk and endpoint support staff.

**Access includes:**
- Microsoft Intune (device management)
- Entra ID (password resets, MFA resets, account unlocks — scoped to non-admin users only)
- Helpdesk ticketing system (full access)
- Remote support tools
- Microsoft 365 admin center (limited — user and license management only)

**Access excluded:**
- Global Admin roles
- Security policy management
- Conditional Access policy management

---

### IT Administrator
Senior IT staff responsible for system and identity administration.

**Access includes:**
- All IT Support Technician access
- Full Entra ID administration
- Conditional Access policy management
- Microsoft Defender administration
- Microsoft Intune full administration
- Exchange Online administration
- SharePoint Online administration
- Eligible for temporary Global Admin via PIM (requires justification and approval)

---

### Global Administrator (Break-Glass)
Emergency access only. Not used for day-to-day operations.

**Access includes:**
- Full Microsoft 365 and Entra ID control

**Restrictions:**
- Assigned to maximum two accounts
- Accounts are cloud-only (not synced from on-premises AD)
- MFA enforced — hardware FIDO2 key required
- All activity logged and alerted in Microsoft Sentinel
- Access reviewed monthly by IT leadership
- Never used for routine tasks — PIM eligible roles used instead

---

## Access Request Process

Users who need access beyond their assigned role must submit a formal access request:

1. Employee submits request through the IT helpdesk ticketing system
2. Employee's direct manager approves or denies the request
3. IT reviews the request against least privilege principles
4. If approved, IT provisions access and documents the business justification
5. Temporary access is set with an expiration date when possible
6. Access is reviewed at the next quarterly access review cycle
