# Entra ID PIM Lab: Global Administrator as Eligible (Just-In-Time Access)

## Goal
Implement Privileged Identity Management (PIM) for Global Administrator (GA) so GA is **eligible-only** and requires a time-bound activation with controls.

## Environment
- Platform: Microsoft Entra ID (lab tenant)
- Users: test admin account(s) only
- Scope: Role-based access via PIM

## Configuration
- Role: Global Administrator
- Assignment type: Eligible (no permanent active)
- Activation duration: 1 hour
- Activation requirements:
  - MFA required
  - Justification required

## Validation Steps
1. Attempted to access privileged admin capabilities **without activation**
2. Activated GA via PIM
3. Re-attempted access after activation
4. Confirmed activation events appear in PIM audit history

## Results / Evidence
- Before activation: privileged access **blocked / not available**
- After activation: privileged access **available for 1 hour**
- Auditability: activation recorded (who/when/role)

## Why this matters (real-world)
- Reduces standing privilege (limits blast radius of account compromise)
- Enforces “just in time” elevation with accountability
- Improves audit readiness (provable admin access trail)

## What I’d improve next
- Add approval for GA activation (if required)
- Add Conditional Access policy coverage for admin portals
- Alerting: notify on GA activation and unusual activation patterns
