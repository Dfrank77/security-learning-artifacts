# Hybrid Lab 2: Entra Connect (PHS) + Scoped OU Sync + Sign-in Validation

## Goal
Install Entra Connect (Azure AD Connect) in a lab, enable Password Hash Sync (PHS), scope sync to specific OUs, and prove cloud sign-in works.

## Build
### 1) Tenant prep
- Confirmed tenant admin access in Entra admin center
- (Optional) Added/verified routable domain for UPN alignment (lab permitting)

### 2) Entra Connect install
- Installed Entra Connect / Azure AD Connect on a domain-joined server
- Used **Custom** install (not Express)

### 3) Sign-in method
- Selected **Password Hash Synchronization (PHS)**
- Left Seamless SSO off (kept lab simple and controlled)

### 4) Sync scope (OU filtering)
- Scoped directory sync to only:
  - `OU=Lab Users`
  - `OU=Lab Groups`
- Avoided syncing entire domain

## Validation
### Users and groups appear in Entra
- Confirmed `alice@corpcloud.net` and `bob@corpcloud.net` appear as **Synced from Active Directory**
- Confirmed group `GRP-LAB-CloudUsers` exists and includes Alice/Bob

### Password hash sync behavior (proof)
- Baseline: signed into a Microsoft cloud portal as `alice@corpcloud.net` using AD password
- Reset Alice password in AD
- After delta/scheduled sync:
  - Old password fails
  - New AD password succeeds

## What this demonstrates
- Minimal hybrid identity build (AD → Entra) using PHS
- Controlled OU-scoped sync (safer, enterprise pattern)
- Logically validated authentication behavior via password change + sign-in results
