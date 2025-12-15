# Entra Conditional Access Lab: MFA Policy (Build + Validation)

## Goal
Implement a baseline Conditional Access policy requiring MFA and validate its behavior using Entra sign-in logs.

## Build (What I configured)
- Policy name: CA-Require-MFA-(Pilot)
- Users: pilot group (test users)
- Cloud apps: (e.g., All cloud apps or selected apps)
- Grant control: Require multi-factor authentication
- Exclusions: break-glass accounts excluded
- Rollout: started in Report-only, then enforced for pilot

## Validation (What I tested)
1. Signed in as a pilot user while policy was Report-only
2. Checked sign-in logs to confirm the policy evaluated as expected
3. Switched policy to On (pilot only)
4. Signed in again and confirmed MFA was required
5. Confirmed successful sign-in after completing MFA

## Evidence captured (from Entra logs)
- Sign-in log shows policy applied (Report-only phase)
- Sign-in log shows MFA required (enforced phase)
- Sign-in log shows success after satisfying MFA
- Verified break-glass excluded (policy not applied to break-glass account)

## Notes / Lessons learned
- Report-only + log validation prevented accidental lockouts
- Pilot scoping reduced blast radius before broader rollout
