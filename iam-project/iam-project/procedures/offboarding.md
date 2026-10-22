# Identity Offboarding Procedure — Contoso Financial Services

**Version:** 1.0
**Last Updated:** October 2026
**Owner:** IT Department

---

## Purpose

This procedure ensures that when an employee leaves Contoso Financial Services, all system access is fully revoked on the last day of employment — eliminating the risk of unauthorized access from former employees.

---

## Trigger

HR notifies IT of a separation at least **3 business days** in advance when possible. For involuntary terminations, IT is notified at the same time as the employee and the offboarding is executed immediately. The notification must include:

- Employee full name and account (`firstname.lastname@contoso.com`)
- Last day of employment
- Type of separation (voluntary resignation, involuntary termination, retirement, contract end)
- Manager name
- Whether the employee had any privileged or elevated access

---

## Offboarding Checklist

### Immediate Actions (Day of Departure)

#### Step 1 — Disable the Account
- [ ] In Microsoft Entra ID, set the account to **Disabled** — do NOT delete the account yet
- [ ] Revoke all active sessions immediately (Entra ID → User → Revoke Sessions)
- [ ] Confirm the account cannot sign in (test with a separate browser session)
- [ ] Record the time of account disable in the offboarding ticket

#### Step 2 — Remove from All Groups
- [ ] Remove the user from all Entra ID security groups
- [ ] Remove the user from all Microsoft 365 groups and Teams
- [ ] Remove the user from all distribution lists
- [ ] Confirm that all role-based application access is removed as a result of group removal
- [ ] Document the list of groups the user was removed from

#### Step 3 — Revoke Privileged Access (if applicable)
- [ ] If the user had any PIM-eligible roles, remove all role eligibility assignments
- [ ] If the user was a Global Administrator or held any permanent admin role, remove immediately
- [ ] Verify no active PIM role activations are in progress at the time of offboarding
- [ ] Remove the user from any break-glass or emergency access documentation

#### Step 4 — Handle the Mailbox
- [ ] Convert the Exchange Online mailbox to a **shared mailbox** (prevents future sign-in while preserving email)
- [ ] Grant mailbox access to the former employee's manager for a period of 90 days
- [ ] Set an auto-reply on the mailbox informing senders that the employee is no longer with the company and providing an alternate contact
- [ ] After 90 days, remove manager access and archive or delete the mailbox per the retention policy

#### Step 5 — OneDrive and Files
- [ ] Grant the former employee's manager access to their OneDrive for a period of 30 days to retrieve any business files
- [ ] Manager is responsible for moving any needed business files to a shared location
- [ ] After 30 days, OneDrive is deleted per Microsoft's retention policy

#### Step 6 — Device Management
- [ ] If the employee had a company-issued device, confirm the device has been returned
- [ ] Perform a remote wipe of the device in Microsoft Intune if the device has not been returned within 24 hours of departure
- [ ] Remove the device from Intune enrollment
- [ ] If the employee used a personal device (BYOD), perform a selective wipe (corporate data only) in Intune

#### Step 7 — MFA and Credential Cleanup
- [ ] Clear all MFA methods registered to the account in Entra ID
- [ ] Revoke any registered FIDO2 keys
- [ ] Confirm no application passwords or legacy auth tokens remain active

#### Step 8 — License Reclamation
- [ ] Remove the Microsoft 365 license from the account (license is reclaimed automatically when the account is disabled and removed from license groups, but verify)
- [ ] Document the license reclamation date for IT asset records

---

## Post-Offboarding Actions (Within 30 Days)

- [ ] Manager confirms all business-critical data has been retrieved from the employee's OneDrive and mailbox
- [ ] IT removes manager delegate access from the shared mailbox after 90 days
- [ ] IT deletes the Entra ID account after 30 days (account is preserved in disabled state for 30 days to allow for any audit or HR needs)
- [ ] IT documents account deletion in the offboarding log

---

## Involuntary Termination Protocol

For involuntary terminations, speed is critical. IT follows this expedited sequence:

1. IT receives notification from HR and manager simultaneously
2. Account is disabled **within 15 minutes** of notification
3. Active sessions are revoked immediately
4. Manager is granted mailbox and OneDrive access within 1 hour
5. Device remote wipe is initiated if the device is off-premises
6. Full offboarding checklist is completed within 24 hours

---

## Contractor and Vendor Offboarding

- Contractor accounts with an expiration date are automatically disabled on the expiration date by Entra ID
- IT verifies automatic expiration occurred and documents it in the offboarding log
- If a contract ends early, HR or the engagement manager notifies IT and the standard offboarding process is followed immediately
- Any contractor-issued devices are recovered before or on the last day

---

## Audit and Documentation

Every offboarding is documented in the IT ticketing system with:
- Date and time of account disable
- Complete list of groups removed
- Mailbox and OneDrive disposition
- Device return or remote wipe confirmation
- License reclamation date
- Account deletion date

This documentation is retained for a minimum of 3 years per Contoso's data retention policy.
