# Multi-Factor Authentication (MFA) Policy — Contoso Financial Services

**Version:** 1.0
**Last Updated:** October 2026
**Owner:** IT Department
**Review Cycle:** Annual

---

## Purpose

This policy defines multi-factor authentication (MFA) requirements for all Contoso Financial Services users and systems. MFA is a foundational control that protects accounts even when passwords are compromised.

---

## Scope

This policy applies to all users with a Contoso Financial Services Microsoft Entra ID account, including employees, contractors, and vendors.

---

## MFA Requirement by Role

| Role | MFA Required | Accepted Methods | Notes |
|---|---|---|---|
| All Employees | Yes | Microsoft Authenticator app (push or TOTP), SMS (fallback only) | Required at every sign-in from unmanaged or new devices |
| Finance (all) | Yes | Microsoft Authenticator app only | SMS not permitted — phishing-resistant preferred |
| IT Support Technician | Yes | Microsoft Authenticator app | Required at every sign-in |
| IT Administrator | Yes | Microsoft Authenticator app + FIDO2 key preferred | Phishing-resistant MFA required for privileged role activation |
| Global Administrator (break-glass) | Yes | FIDO2 hardware security key only | No exceptions — Microsoft Authenticator not permitted for this account |
| Contractors / Vendors | Yes | Microsoft Authenticator app | Provisioned during onboarding |

---

## Accepted MFA Methods

Methods are listed in order of preference (most secure to least secure):

1. **FIDO2 Hardware Security Key** (YubiKey or equivalent) — Required for Global Admin; preferred for IT Administrators
2. **Microsoft Authenticator — Passwordless Phone Sign-in** — Preferred for all standard users
3. **Microsoft Authenticator — Push Notification with Number Matching** — Acceptable for all standard users
4. **Microsoft Authenticator — TOTP Code** — Acceptable fallback
5. **SMS one-time code** — Permitted only as a recovery fallback; not permitted as primary method for Finance or IT roles

---

## Conditional Access Enforcement

MFA enforcement is implemented through Microsoft Entra Conditional Access policies, not per-user MFA settings. The following policies are active:

### Policy 1 — All Users, All Apps
- **Who:** All users
- **What:** All cloud apps
- **Condition:** Any sign-in
- **Control:** Require MFA
- **Exclusion:** Break-glass accounts only

### Policy 2 — Require Compliant Device for Sensitive Apps
- **Who:** Finance users, IT Administrators
- **What:** Finance applications, IT admin consoles, Azure portal
- **Condition:** Any sign-in
- **Control:** Require MFA + require Intune-compliant device
- **Result:** Users on personal or non-compliant devices are blocked entirely

### Policy 3 — Block Legacy Authentication
- **Who:** All users
- **What:** All apps
- **Condition:** Legacy authentication protocols (basic auth, SMTP auth, IMAP, POP3)
- **Control:** Block access
- **Reason:** Legacy protocols cannot enforce MFA

### Policy 4 — High-Risk Sign-in Requires Password Reset
- **Who:** All users
- **What:** All apps
- **Condition:** Entra ID Identity Protection detects high-risk sign-in
- **Control:** Require secure password change before access is granted

### Policy 5 — Privileged Role Activation Requires Phishing-Resistant MFA
- **Who:** IT Administrators activating roles via PIM
- **What:** Azure portal, Microsoft 365 admin center
- **Condition:** PIM role activation
- **Control:** Require FIDO2 key or certificate-based authentication

---

## MFA Registration

- All new employees must register MFA during onboarding before their account is activated for application access
- MFA registration is done through the Microsoft My Security Info page (`aka.ms/mysecurityinfo`)
- IT walks new employees through registration on day one
- Employees are required to register a minimum of two MFA methods (primary + backup)

---

## MFA Reset Procedure

If an employee loses access to their MFA device:

1. Employee contacts the IT helpdesk by phone (identity must be verified via manager confirmation — not by email)
2. IT temporarily grants a one-time bypass (maximum 1 hour) to allow sign-in
3. Employee re-registers MFA immediately using the one-time bypass window
4. IT documents the reset in the helpdesk ticket system
5. If the lost device was a phone, IT advises the employee to remove the old device from `aka.ms/mysecurityinfo`

---

## MFA Exceptions

No permanent MFA exceptions are permitted. Temporary exceptions may be granted only under the following conditions:

- Medical or accessibility accommodation (reviewed by HR and IT, documented, reviewed quarterly)
- Service accounts (non-interactive accounts must use certificate-based authentication or managed identities instead of MFA — password-based service accounts with MFA bypass are prohibited)

All exceptions are documented and included in the quarterly access review.

---

## Non-Compliance

Accounts that have not completed MFA registration within 7 days of hire are disabled until registration is completed. Users who attempt to circumvent MFA controls are subject to disciplinary action under the Access Control Policy.
