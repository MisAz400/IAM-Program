# Access Control Policy — Contoso Financial Services

**Version:** 1.0
**Last Updated:** October 2026
**Owner:** IT Department
**Review Cycle:** Annual

---

## Purpose

This policy defines how access to Contoso Financial Services systems, applications, and data is requested, granted, reviewed, and revoked. The goal is to ensure that every user has exactly the access they need to do their job — no more, no less.

---

## Scope

This policy applies to:
- All full-time and part-time employees
- Contractors and temporary workers
- Third-party vendors with system access
- All systems hosted in Microsoft 365, Microsoft Azure, and on-premises environments

---

## Principles

### Least Privilege
Users are granted the minimum level of access required to perform their job function. Access is not granted speculatively or "just in case."

### Need to Know
Access to sensitive data (financial records, HR data, customer PII) is restricted to employees whose job function requires it.

### Separation of Duties
No single user should have the ability to both initiate and approve a transaction or access request. Finance users who can create transactions cannot also approve them.

### Zero Trust
Access is never granted based on network location alone. Every access request — including from inside the corporate office — is evaluated based on:
- Verified user identity (MFA required)
- Device compliance status (managed and compliant device required for sensitive systems)
- Location and risk signals (evaluated through Conditional Access)

---

## Access Categories

| Category | Description | Examples |
|---|---|---|
| Standard Access | Granted to all employees automatically upon hire | Microsoft 365, Teams, Outlook, SharePoint intranet |
| Role-Based Access | Granted based on job function | Finance applications, Operations tools, IT admin consoles |
| Privileged Access | Elevated access for IT administration | Entra ID admin, Conditional Access, Intune |
| Sensitive Data Access | Access to regulated or sensitive data | Financial records, customer PII, HR data |
| Emergency Access | Break-glass accounts for critical outages | Global Administrator (two accounts, hardware MFA only) |

---

## Access Provisioning

### New Employees
- IT provisions a Microsoft Entra ID account within 24 hours of receiving a completed onboarding request from HR
- Account is added to the appropriate role group(s) based on the employee's job title and department
- Standard access (Microsoft 365) is provisioned automatically via group assignment
- Role-based access is provisioned before the employee's start date
- The employee receives account credentials and MFA setup instructions on day one

### Role Changes and Transfers
- When an employee changes roles or departments, the hiring manager submits a change request to IT at least 3 business days before the effective date
- IT removes access associated with the old role and provisions access for the new role
- Access is never cumulative — old role access is removed when new role access is granted

### Contractors and Vendors
- Contractor accounts are created with an expiration date matching the end of the contract
- Contractors receive only the access explicitly required for their engagement
- Contractor accounts are reviewed at 90-day intervals regardless of contract length
- Vendor access to production systems requires a signed third-party access agreement

---

## Access Requests

Requests for access beyond the standard role assignment follow this process:

1. **Submit** — Employee submits a request through the IT helpdesk system with a written business justification
2. **Manager Approval** — The employee's direct manager reviews and approves or denies within 2 business days
3. **IT Review** — IT evaluates the request against least privilege principles and compliance requirements
4. **Provision** — If approved, IT provisions access and documents the justification in the ticket
5. **Expiration** — Temporary access is assigned an expiration date; permanent access exceptions are logged and included in the next quarterly review

---

## Privileged Access Management

IT Administrators who require elevated privileges for administrative tasks must use **Microsoft Entra Privileged Identity Management (PIM)**:

- Privileged roles (e.g., Global Administrator, Security Administrator) are not permanently assigned
- Administrators request role activation through PIM with a business justification
- Activations are time-limited (maximum 8 hours)
- All PIM activations are logged and reviewed monthly by IT leadership
- Permanent standing Global Admin access is prohibited except for break-glass accounts

---

## Prohibited Access Behaviors

The following are prohibited and subject to disciplinary action:

- Sharing account credentials with any other person, including coworkers
- Using another employee's account to access systems
- Accessing systems or data outside the scope of your role without prior approval
- Attempting to escalate your own privileges without authorization
- Using personal devices to access sensitive systems without IT-managed device enrollment

---

## Policy Violations

Violations of this policy are reported to IT leadership and HR. Depending on severity:
- Minor violations result in a documented warning and mandatory security awareness training
- Serious violations (unauthorized data access, credential sharing) may result in termination and legal action

---

## Policy Review

This policy is reviewed annually by the IT department and updated to reflect changes in technology, regulations, or business requirements. All employees are notified of material policy changes.
