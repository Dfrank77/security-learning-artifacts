# Entra ID Lab: Tenant Hardening & Access Governance (Overview)

## Summary
Hardened a Microsoft Entra ID lab tenant using enterprise IAM patterns: break-glass access, baseline Conditional Access (MFA), just-in-time admin via PIM (roles + groups), and guest access governance.

> Lab tenant only (no production data). Focus is on design choices + validation evidence.

## What I Implemented
- Break-glass emergency access (2 accounts, CA-excluded)
- Baseline Conditional Access (Report-only → validated → enforced)
- PIM for directory roles (eligible-only JIT activation)
- PIM for role-assignable admin groups (request + approval + audit chain)
- B2B guest access reviews (auto-apply removals)
- Intro: Access Packages + basic SSO integration

## Evidence I Validated
- PIM audit history (role activations and justifications)
- PIM group activation chain (eligible → request → approval → activation)
- Entra sign-in logs showing Conditional Access policy evaluation
- Access review results showing removals applied
