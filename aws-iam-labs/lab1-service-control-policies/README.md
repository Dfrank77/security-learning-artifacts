# AWS IAM Labs - Service Control Policies (SCPs)

## Overview
This directory contains Service Control Policies (SCPs) I built as part of my AWS Identity and Access Management learning path. These policies enforce organization-wide security guardrails, similar to Conditional Access policies in Microsoft Entra ID.

## Lab Environment
- AWS Organizations structure with Production and Non-Production OUs
- Policies created and attached via AWS CLI
- Focus on least-privilege access and defense-in-depth

## Policies

### 1. Require MFA for IAM Actions (`require-mfa-for-iam.json`)
**Purpose:** Prevents privilege escalation without multi-factor authentication

**What it does:**
- Denies creation of IAM users, roles, and access keys without MFA
- Blocks policy attachment and modification without MFA
- Reduces risk from compromised credentials

**Real-world application:**
- Protects against credential theft leading to privilege escalation
- Enforces MFA for administrative actions
- Common in SOC 2 and compliance frameworks

### 2. Deny Root Account Usage (`deny-root-account.json`)
**Purpose:** Effectively disables the AWS root account for daily operations

**What it does:**
- Blocks ALL actions when using root account credentials
- Forces use of IAM users/roles with proper permissions
- Enforces AWS security best practices

**Why this matters:** Root account compromise = complete account takeover

## How SCPs Work

Service Control Policies set **maximum permissions** for accounts in an AWS Organization:

**Policy Evaluation Order:**
1. Explicit Deny (from SCP or IAM) → DENIED ❌
2. Explicit Allow (from IAM) + No SCP Deny → ALLOWED ✅
3. No Explicit Allow → DENIED ❌

## Skills Demonstrated

- AWS Organizations and OU structure
- Service Control Policy design and implementation
- IAM policy evaluation logic
- Security guardrails and least-privilege principles
- CLI-based infrastructure management
- Compliance control implementation (SOC 2, PCI-DSS)

## Related Experience

These AWS SCPs map directly to my Microsoft Entra ID experience:
- **Entra ID Conditional Access** → **AWS SCPs**
- **Entra ID PIM** → **AWS temporary role elevation**
- **Entra ID Access Reviews** → **AWS IAM Access Analyzer**
