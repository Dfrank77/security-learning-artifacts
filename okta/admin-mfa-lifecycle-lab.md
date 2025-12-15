# Okta Lab: Admin MFA Hardening + Group-Based Roles + Lifecycle Automation

## Goal
Harden Okta admin access using strong MFA and group-based admin roles, and validate policy execution via System Log. Also implemented basic app SSO (SAML/OIDC) and lifecycle automation using groups/rules.

## 1) Group-Based Admin Role Assignment
- Created group: `GRP-Okta-Admins-Lab`
- Assigned an Okta admin role to the **group** (not directly to users)
- Added lab admin user (`Admin1`) to the group

## 2) Strong MFA for Okta Admin Console
- Verified authenticators (Password, Okta Verify, WebAuthn/FIDO2 where supported)
- Created Authentication Policy: `POL-Okta-AdminConsole-StrongAuth`
- Rule: if user in `GRP-Okta-Admins-Lab` → require password + strong MFA; challenge every Admin Console sign-in
- Attached policy to **Okta Admin Console** app
- Validation:
  - `Admin1` prompted for strong MFA when accessing Admin Console
  - System Log shows correct policy + rule evaluation

## 3) App SSO (Lab)
- Integrated at least one app:
  - SAML: issuer, ACS URL, certificate exchange
  - OIDC: client ID/secret, redirect URI, scopes
- Validation:
  - Group assignment grants app access
  - Removing from group revokes app access

## 4) Lifecycle Automation (Groups + Rules)
- Created group/profile rules (example: department = HR → add to `GRP-HR-Apps`)
- Validation:
  - Attribute change updates group membership automatically
  - Group membership change updates app access

## What this demonstrates
- Admin hardening via app-specific auth policy
- Group-based admin governance (roles via groups)
- Practical SSO wiring + access lifecycle automation
- Log-driven validation (System Log proves what actually executed)
