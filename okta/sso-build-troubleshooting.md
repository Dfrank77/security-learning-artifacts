# Okta Lab: SSO Build + Troubleshooting (SAML & OIDC)

## Goal
Configure SSO for a lab app using SAML and/or OIDC and validate end-to-end sign-in using Okta assignments and System Log evidence.

---

## 1) Pre-checks (before config)
- User is assigned to the app (directly or via group)
- Correct app sign-on mode selected (SAML vs OIDC)
- Test user has required MFA/enrollment if policy demands it

---

## 2) SAML SSO (Lab)
### What I configured
- IdP (Okta) metadata/certificate
- SP details:
  - **ACS URL** (Assertion Consumer Service)
  - **Entity ID / Audience URI**
- Attribute/claims mapping (basic)

### Validation
- Clicking the app tile initiates SSO and lands in the app (or at least reaches SP endpoint)
- Okta System Log shows:
  - Successful authentication
  - Assertion issued
  - App sign-on event

### Common failure modes I checked
- Wrong ACS URL → SP rejects assertion
- Wrong Entity ID/Audience → “invalid audience”
- Clock skew/cert issues → signature or timing errors
- User not assigned → app tile missing / access denied

---

## 3) OIDC SSO (Lab)
### What I configured
- Client ID / Client secret (if confidential client)
- Redirect URI(s)
- Grant type (Authorization Code / PKCE)
- Scopes (openid, profile, email as needed)

### Validation
- User authenticates and returns to app via redirect URI
- Token issuance succeeds (auth code → token)
- Okta System Log shows:
  - OAuth authorization request
  - Token grant success/failure

### Common failure modes I checked
- Redirect URI mismatch → immediate failure
- Wrong app type (public vs confidential) → token grant fails
- Missing scopes/claims → app login succeeds but authorization fails

---

## 4) Evidence (what I capture in a real ticket)
- App name + user + timestamp
- Error message / code (Okta + app side)
- System Log event(s) proving what happened:
  - auth policy evaluated
  - app sign-on attempt
  - assertion/token issued or denied

---

## What this demonstrates
- Correctly wiring SAML and OIDC at a lab level
- Assignment-driven access (group → app access)
- Log-driven troubleshooting (System Log as source of truth)
