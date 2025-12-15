# Entra Lab 2: Simple SSO to a Gallery Application

## Objectives
- Add a gallery enterprise application to Entra
- Assign access via group (no direct user assignment)
- Validate SSO from My Apps portal

## Steps

### 1) Create App Access Group
- Entra ID → Groups → New group
- Name: `GRP-App-WebPortal-Lab`
- Members: Alice only (Bob used as a control user)

### 2) Add an Enterprise Application
- Entra ID → Enterprise applications → New application
- Selected a gallery app (SAML or password-based)
- Named: `WebPortal-Lab`

### 3) Configure SSO (High Level)
- **SAML apps**
  - Exchanged metadata (upload/download as required)
  - Configured Identifier (Entity ID) and Reply URL (ACS)
  - NameID mapping: UPN by default (`user.userprincipalname`) or email if required
- **Password-based apps**
  - Configured credentials per app capability (shared or per-user)

### 4) Assign Users via Group
- `WebPortal-Lab` → Users and groups → Add user/group
- Assigned: `GRP-App-WebPortal-Lab`
- No direct user assignments

### 5) Test SSO
- As Alice: https://myapps.microsoft.com
  - Confirmed `WebPortal-Lab` tile visible and launches
- As Bob: confirmed tile does not appear

### 6) Cleanup Check
- Removed Alice from `GRP-App-WebPortal-Lab`
- Confirmed tile disappears after next sign-in/refresh

## Evidence (what I check)
- Enterprise app assignment shows group-based access
- My Apps tile visibility matches group membership
- Entra sign-in logs show successful/failed sign-in attempts as expected
- (If SAML) SAML sign-in events appear under Enterprise Application sign-in logs
