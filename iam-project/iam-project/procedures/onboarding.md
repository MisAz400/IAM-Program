# Identity Onboarding Procedure — Contoso Financial Services

**Version:** 1.0
**Last Updated:** October 2026
**Owner:** IT Department

---

## Purpose

This procedure ensures that every new employee at Contoso Financial Services receives the correct system access on their first day — no more, no less — and that all provisioning steps are documented.

---

## Trigger

HR submits a New Hire Request ticket to IT at least **3 business days** before the employee's start date. The ticket must include:

- Employee full name
- Job title and department
- Start date
- Manager name
- Work location (office / remote / hybrid)
- Whether the employee requires any access beyond the standard role assignment

---

## Provisioning Checklist

### Step 1 — Create Microsoft Entra ID Account
- [ ] Create account in Microsoft Entra ID with the standard naming convention: `firstname.lastname@contoso.com`
- [ ] Set a temporary password (meets complexity requirements)
- [ ] Set "User must change password at next sign-in" = Yes
- [ ] Record the account creation in the IT provisioning log

### Step 2 — Assign Role Group
- [ ] Add the user to the appropriate Entra ID security group based on their department and job title (see [Role Definitions](../roles/role-definitions.md))
- [ ] Confirm that group-based licensing automatically assigns the correct Microsoft 365 license
- [ ] Verify the user does NOT appear in any groups from a previous or unrelated role

### Step 3 — Assign Standard Access
Standard access is granted automatically via the `GRP-AllEmployees` group. Verify the following are available after group assignment:
- [ ] Microsoft Outlook (Exchange Online mailbox provisioned)
- [ ] Microsoft Teams
- [ ] SharePoint intranet site
- [ ] OneDrive

### Step 4 — Assign Role-Based Access
Based on the employee's role group, confirm the following are provisioned:
- [ ] Role-specific SharePoint sites
- [ ] Role-specific applications (Finance ERP, Operations ticketing system, etc.)
- [ ] Shared mailboxes or distribution lists if applicable
- [ ] Any additional access approved in the onboarding request

### Step 5 — Enroll Device (if applicable)
- [ ] If the employee is receiving a company-issued device, enroll it in Microsoft Intune before the start date
- [ ] Apply the appropriate Intune compliance policy for the employee's role
- [ ] Confirm the device appears as compliant in Intune before handing it to the employee

### Step 6 — MFA Registration
- [ ] On day one, IT walks the employee through MFA registration at `aka.ms/mysecurityinfo`
- [ ] Employee registers minimum two MFA methods (primary: Microsoft Authenticator app; backup: alternate phone or TOTP)
- [ ] For IT Administrators: also register a FIDO2 hardware key
- [ ] Confirm MFA is enforced before ending the onboarding session

### Step 7 — Account Verification
Before closing the onboarding ticket, IT verifies:
- [ ] Employee can sign in successfully
- [ ] MFA is working
- [ ] Employee has access to all expected applications
- [ ] Employee does NOT have access to systems outside their role
- [ ] No admin rights are present unless explicitly approved

### Step 8 — Manager Notification
- [ ] Send the manager a confirmation email listing the access that was provisioned
- [ ] Close the IT onboarding ticket with a summary of all provisioning steps completed

---

## Day One — Employee Experience

When the employee arrives on their first day, IT ensures they can complete the following before the end of the day:

1. Sign in to their account for the first time and set a new password
2. Complete MFA registration
3. Access their Outlook mailbox
4. Access Microsoft Teams
5. Locate the IT helpdesk contact information for future support requests

---

## Contractor and Vendor Onboarding

Contractor accounts follow the same process with these additional requirements:

- Account is created with an expiration date matching the end of the contract
- Contractor is added only to the specific groups required for their engagement
- Contractor access is documented with the business justification and approving manager
- A reminder is set in IT's ticketing system to review the account 2 weeks before expiration

---

## Exceptions

Any access request that falls outside the standard role assignment must be approved by the employee's manager before IT provisions it. Approved exceptions are documented in the onboarding ticket and flagged for the next quarterly access review.
