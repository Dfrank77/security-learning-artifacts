# Security Learning Artifacts (IAM)

Practical IAM-focused artifacts built from hands-on labs in Microsoft Entra ID, AWS, Okta, and hybrid identity scenarios. This repo contains short, resume-friendly write-ups that document configuration decisions, validation steps, and security rationale.

---

## 🔥 Featured: AWS IAM Labs

### [AWS Service Control Policies (SCPs)](aws-iam-labs/lab1-service-control-policies/)

Organization-wide security guardrails built in AWS Organizations. These policies enforce least-privilege access and defense-in-depth principles across multi-account environments.

**Policies Implemented:**
- **Require MFA for IAM Actions** - Prevents privilege escalation without multi-factor authentication
- **Deny Root Account Usage** - Effectively disables root account for daily operations

**Skills Demonstrated:**
- AWS Organizations and OU structure
- Service Control Policy design and implementation
- IAM policy evaluation logic (Explicit Deny → Allow + No Deny → Default Deny)
- CLI-based infrastructure management
- Compliance control implementation (SOC 2, PCI-DSS)

**Entra ID Parallel:** These AWS SCPs map directly to Conditional Access policies in Entra ID - both enforce policy-based access control at the organization level.

[→ View AWS IAM Labs](aws-iam-labs/lab1-service-control-policies/)

---

## ✅ Start Here (2 minutes)

1. [PIM Role-Assignable Admin Group (Request + Approval + Audit Chain)](entra/)
2. [Conditional Access MFA Lab (Build + Validation)](entra/)

---

## Artifacts by Platform

### Entra (IAM / Governance)

- [Entra PIM Lab: Global Administrator as Eligible (JIT Access)](entra/)
- [Entra Sign-in Log Triage Checklist](entra/)
- [Entra Lab 3: B2B Guest User & Group-based Access](entra/)
- [Entra Lab 2: Simple SSO to a Gallery Application](entra/)
- [Entra Lab 0: Tenant Basics, Users & Groups](entra/)

### AWS (IAM / Security Controls)

- [AWS Service Control Policies - MFA Enforcement & Root Account Denial](aws-iam-labs/lab1-service-control-policies/)

### Okta

- [Okta Admin MFA + Lifecycle Automation Lab](okta/)
- [Okta SSO Build + Troubleshooting (SAML & OIDC)](okta/)
- [Okta Lab 3: User Lifecycle & Deactivation](okta/)
- [Okta Lab 0: Org Setup & Basic MFA](okta/)

### Hybrid AD → Entra

- [Hybrid Lab 1: On-Prem AD Setup + OU/UPN Prep](hybrid/)
- [Hybrid Lab 2: Entra Connect (PHS) + Scoped OU Sync + Sign-in Validation](hybrid/)

---

## Cross-Platform IAM Concepts

Understanding how identity and access management patterns translate across platforms:

| **Concept** | **Entra ID** | **AWS IAM** | **Okta** |
|------------|-------------|------------|---------|
| Policy-based access control | Conditional Access | Service Control Policies | Sign-On Policies |
| Just-in-time privileged access | PIM | Temporary role elevation | Workflow automation |
| Periodic access reviews | Access Reviews | IAM Access Analyzer | Access Certifications |
| MFA enforcement | CA policies | IAM condition keys | MFA policies |
| Organization structure | Management groups | AWS Organizations | Okta groups |

---

## Scope / Notes

- Lab-tenant only. No employer or sensitive tenant data included.
- Goal: demonstrate real-world IAM patterns (least privilege, just-in-time elevation, auditability, access reviews).

---

## Next Labs

- [ ] AWS: IP-based access restrictions (trusted locations)
- [ ] AWS: CloudTrail protection (prevent audit log deletion)
- [ ] AWS: Cross-account IAM roles
- [ ] Entra: Break-glass accounts lab (build + validation)
- [ ] Entra: Guest access review with auto-removal for not-reviewed
- [ ] Okta: Group rules (attribute-driven access automation)

---

## About This Repo

Built as part of a career transition from hospitality management to cybersecurity, with a focus on Identity and Access Management (IAM). These labs demonstrate:

- Hands-on implementation of security controls
- Understanding of least-privilege principles
- Multi-cloud IAM knowledge (Entra ID, AWS, Okta)
- Compliance and audit readiness (SOC 2, PCI-DSS)
- CLI-based infrastructure management

**Contact:** [GitHub Profile](https://github.com/Dfrank77)
