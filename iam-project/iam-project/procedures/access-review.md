# Quarterly Access Review Procedure — Contoso Financial Services

**Version:** 1.0
**Last Updated:** October 2026
**Owner:** IT Department
**Review Frequency:** Quarterly (January, April, July, October)

---

## Purpose

Access creep is one of the most common IAM risks — users accumulate permissions over time through role changes, project assignments, and one-off requests, and that excess access is never cleaned up. This quarterly access review ensures that every user's access remains appropriate for their current role.

---

## Scope

The quarterly access review covers:
- All active Entra ID user accounts
- All security group memberships
- All privileged role assignments (PIM eligible and active)
- All access exceptions granted outside the standard role assignment
- All contractor and vendor accounts

---

## Review Schedule

| Quarter | Review Period | Completion Deadline |
|---|---|---|
| Q1 | January 1–15 | January 15 |
| Q2 | April 1–15 | April 15 |
| Q3 | July 1–15 | July 15 |
| Q4 | October 1–15 | October 15 |

---

## Roles and Responsibilities

| Role | Responsibility |
|---|---|
| IT Department | Pulls and distributes access reports; executes approved changes; documents outcomes |
| Department Managers | Reviews access for their direct reports; approves or flags for removal |
| IT Leadership | Reviews all privileged access (IT Administrators, PIM assignments) |
| HR | Provides current employee roster to validate no terminated employees have active accounts |

---

## Review Procedure

### Step 1 — Pull Access Reports (IT, Day 1)
IT generates the following reports from Microsoft Entra ID:

- [ ] Full list of active user accounts with their assigned groups
- [ ] All users with privileged role assignments (permanent or PIM eligible)
- [ ] All active access exceptions (non-standard access approved outside role assignment)
- [ ] All contractor and vendor accounts with expiration dates
- [ ] Sign-in activity report for the past 90 days (to identify inactive accounts)

Reports are exported to a secure SharePoint folder accessible only to IT and department managers.

### Step 2 — Cross-Reference with HR Roster (IT, Day 1)
- [ ] Compare the active Entra ID account list against the current HR employee roster
- [ ] Flag any accounts belonging to employees no longer on the roster (potential missed offboarding)
- [ ] Disable any flagged accounts immediately and open an investigation ticket

### Step 3 — Distribute Manager Review (IT, Day 2)
- [ ] Send each department manager a filtered report showing only their direct reports' access
- [ ] Managers are asked to review and respond within 5 business days
- [ ] Managers certify one of the following for each user:
  - **Approve** — Access is appropriate for the user's current role
  - **Modify** — Access needs to be changed (specify what to add or remove)
  - **Remove** — User should no longer have this access

### Step 4 — IT Leadership Reviews Privileged Access (IT Leadership, Days 2–5)
- [ ] Review all IT Administrator role assignments
- [ ] Review all PIM eligible role assignments
- [ ] Review all PIM activation logs from the past 90 days for anomalies
- [ ] Confirm break-glass accounts are still limited to two accounts with hardware MFA only
- [ ] Remove any privileged access that is no longer justified

### Step 5 — Review Inactive Accounts (IT, Days 3–5)
From the sign-in activity report:
- [ ] Identify accounts with no sign-in activity in the past 90 days
- [ ] Confirm with HR whether the user is still active
- [ ] For active users with no recent sign-in: notify manager and request confirmation the account is still needed
- [ ] Disable accounts with no sign-in in 90+ days that cannot be confirmed as needed

### Step 6 — Execute Approved Changes (IT, Days 6–10)
- [ ] Process all manager-approved modifications (add or remove group memberships)
- [ ] Remove access flagged for removal
- [ ] Disable or delete accounts flagged as inactive or no longer needed
- [ ] Document every change made with the approving manager's name and the business reason

### Step 7 — Review Contractor and Vendor Accounts (IT, Days 6–10)
- [ ] Confirm each contractor account still has an active contract
- [ ] Remove access for any contractor whose contract has ended
- [ ] Update expiration dates for contractors with extended contracts
- [ ] Confirm vendor accounts are scoped to only the access required for the current engagement

### Step 8 — Complete and Document (IT, Day 10)
- [ ] Compile a summary of all changes made during the review cycle
- [ ] Document the number of accounts reviewed, changes made, accounts disabled, and exceptions resolved
- [ ] Store the completed review report in the IT Security SharePoint folder
- [ ] Send a summary to IT leadership confirming the review is complete

---

## Access Exception Handling

Access exceptions granted in the previous quarter are reviewed during the quarterly cycle:
- If the business need still exists, the exception is renewed with manager re-approval
- If the business need no longer exists, the access is removed
- Exceptions that have been renewed for more than two consecutive quarters are escalated to IT leadership to determine if the role definition should be updated instead

---

## Findings and Escalation

If the review uncovers any of the following, IT escalates immediately to IT leadership and HR:
- Active accounts belonging to terminated employees
- Users with access significantly outside their role that cannot be explained
- Privileged accounts with no documented justification
- Evidence of access being shared between users

---

## Metrics Tracked Each Quarter

| Metric | Target |
|---|---|
| Accounts reviewed | 100% of active accounts |
| Manager response rate | 100% within 5 business days |
| Access exceptions resolved or renewed | 100% |
| Inactive accounts (90+ days) disabled | 100% |
| Review completion on time | By the 15th of each quarter month |
