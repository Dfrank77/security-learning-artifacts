# Security Learning Artifacts (IAM)

Practical IAM-focused artifacts built from hands-on labs in Microsoft Entra ID and related identity tooling.
This repo contains short, resume-friendly write-ups that document configuration decisions, validation steps, and security rationale.

---

## ✅ Start here (2 minutes)

1. **[PIM Role-Assignable Admin Group (Request + Approval + Audit Chain)](./entra/pim-role-assignable-admin-group.md)**
2. **[Conditional Access MFA Lab (Build + Validation)](./entra/conditional-access-mfa-lab.md)**

---
## Artifacts
- [Entra PIM Lab: Global Administrator as Eligible (JIT Access)](entra/pim-global-admin-lab.md)
- [Entra Sign-in Log Triage Checklist](entra/sign-in-log-triage-checklist.md)
- [Access Reviews: Interpretation Guide](entra/access-reviews-interpretation-guide.md)
- [Entra Lab 3: B2B Guest User & Group-based Access](entra/lab-3-b2b-guest-group-access.md)
- [Entra Lab 2: Simple SSO to a Gallery Application](entra/lab-2-simple-sso-gallery-app.md)
- [Entra Lab 0: Tenant Basics, Users & Groups](entra/lab-0-tenant-basics-users-groups.md)
- [Okta Admin MFA + Lifecycle Automation Lab](okta/admin-mfa-lifecycle-lab.md)
- [Okta SSO Build + Troubleshooting (SAML & OIDC)](okta/sso-build-troubleshooting.md)
- [Okta Lab 3: User Lifecycle & Deactivation](okta/lab-3-user-lifecycle-deactivation.md)
- [Okta Lab 0: Org Setup & Basic MFA](okta/lab-0-org-setup-basic-mfa.md)
- [Hybrid Lab 1: On-Prem AD Setup + OU/UPN Prep](hybrid/lab-1-ad-ous-upn-prep.md)
- [Hybrid Lab 2: Entra Connect (PHS) + Scoped OU Sync + Sign-in Validation](hybrid/lab-2-entra-connect-phs-scoped-sync.md)

- ## Scope / Notes
- Lab-tenant only. No employer or sensitive tenant data included.
- Goal: demonstrate real-world IAM patterns (least privilege, just-in-time elevation, auditability, access reviews).

## Next
- Break-glass accounts lab (build + validation)
- Guest access review with auto-removal for not-reviewed
- Okta group rules (attribute-driven access automation)
