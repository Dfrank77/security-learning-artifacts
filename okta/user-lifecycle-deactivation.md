# Okta Lab 3: User Lifecycle & Deactivation

## Objectives
- Understand Okta user statuses (Active, Suspended, Deactivated)
- Verify how lifecycle changes impact sign-in and app access

## Lab Objects (from prior labs)
- Users: `lab.user1`, `lab.user2`
- Group: `GRP-App-WebPortal-Lab`
- App: `WebPortal-Lab` (assigned to the group)

## Steps

### 1) Verify Baseline
- Confirmed `lab.user1` is in `GRP-App-WebPortal-Lab`
- Confirmed `lab.user1` can see and launch `WebPortal-Lab`

### 2) Suspend User
- Directory → People → `lab.user1` → More actions → **Suspend**
- Validation:
  - `lab.user1` sign-in fails
  - Existing app access/session behavior stops working as expected

### 3) Deactivate User
- Directory → People → `lab.user1` → More actions → **Deactivate**
- Validation:
  - Status shows **Deactivated**
  - App assignments removed (Applications tab reflects removal)

### 4) System Log Evidence
- Reports → System Log → filter on `lab.user1`
- Observed events:
  - `user.lifecycle.suspend`
  - `user.lifecycle.deactivate`
  - Sign-in failures after suspension/deactivation

### (Optional) Reactivate
- Reactivated `lab.user1`
- Re-assigned group/app and confirmed access restored

## What this demonstrates
- Practical joiner/mover/leaver lifecycle handling
- How user status affects authentication and authorization
- Using System Log to validate lifecycle actions and outcomes
