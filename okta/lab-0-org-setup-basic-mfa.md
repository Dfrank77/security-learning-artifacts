# Okta Lab 0: Org Setup & Basic MFA

## Objectives
- Learn the Okta Admin Console layout
- Create lab users and groups
- Enable basic MFA (Okta Verify / SMS) for interactive users

## Steps

### 1) Explore Admin Console
- Reviewed main areas: Directory, Security, Applications, Reports
- Confirmed admin role (Super Admin vs Admin)

### 2) Create Lab Users
- Directory → People → Add person
- Created:
  - `lab.user1` (standard user)
  - `lab.user2` (standard user)

### 3) Create a Basic Users Group
- Directory → Groups → Add group
- Created: `GRP-All-Employees-Lab`
- Added: `lab.user1`, `lab.user2`

### 4) Enable Authenticators
- Security → Authenticators → Setup
- Enabled for Authentication:
  - Password
  - Okta Verify
  - SMS (optional)

### 5) Basic MFA Policy (Global)
- Security → Authenticators → Policies
- Updated default policy / rule:
  - Target: `GRP-All-Employees-Lab`
  - Requirement: Password + 1 factor (Okta Verify or SMS)
  - Scope: all locations/devices (lab baseline)

### 6) Test / Validation
- Signed in as `lab.user1` in a private window
- Enrolled Okta Verify/SMS
- Confirmed MFA prompt at sign-in after enrollment

## Evidence (what I check)
- User is prompted for factor enrollment at first sign-in
- Subsequent sign-ins require MFA
- System Log shows authentication + factor challenge events
