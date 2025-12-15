# Entra Sign-in Log Triage Checklist (Lab)

## Goal
Quickly determine whether a sign-in is benign, misconfiguration, or suspicious—using Entra sign-in logs and basic context.

## What I check first (60 seconds)
- User: expected account? (admin vs standard vs guest)
- Status: Success / Failure (error code + reason)
- App: expected application?
- Client: Browser vs Mobile vs Legacy
- IP/location: expected geography? impossible travel?
- Device: compliant/managed? new device?
- MFA: performed? satisfied by CA? bypassed?

## Common outcomes + what they mean
### "MFA required" failures
- Likely: Conditional Access applied correctly, user not enrolled or using wrong method
- Next: confirm MFA methods + CA policy targeting

### "Invalid username/password"
- Likely: user error or password spray attempt
- Next: check frequency, IP reputation, multiple users hit?

### "Sign-in blocked by Conditional Access"
- Likely: CA working as intended
- Next: verify policy, user risk, device compliance requirement

### Suspicious patterns (escalate)
- Many failures across multiple users from same IP
- New country + admin account
- Legacy auth attempts (IMAP/POP/SMTP AUTH) if enabled
- Repeated MFA challenges (MFA fatigue)

## Evidence to capture (for notes)
- Timestamp (UTC/local), user, app, IP, location
- Error code + failure reason
- CA policy result (applied / not applied / report-only)
- MFA details (method, requirement, satisfied?)

## Closing criteria
- If benign: document reason + user guidance
- If misconfig: document policy/app issue + remediation
- If suspicious: contain (reset creds, revoke sessions, block IP/geo, review logs)
