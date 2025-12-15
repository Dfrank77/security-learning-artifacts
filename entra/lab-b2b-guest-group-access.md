# Entra Lab 3: B2B Guest User & Group-based Access

## Objectives
- Invite an external (B2B) guest user
- Grant app access via group membership
- Verify how guests appear and are governed in Entra

## Steps

### 1) Invite a Guest
- Entra ID → Users → All users → New user → Invite external user
- Sent invitation to an external email address

### 2) Create Guest Access Group
- Entra ID → Groups → New group
- Name: `GRP-Guest-App-Lab`
- Added:
  - Guest user (once accepted/appeared)
  - Alice (internal comparison)

### 3) Assign Group to an App
- Re-used enterprise app `WebPortal-Lab` (or another test app)
- Enterprise applications → App → Users and groups → Add
- Assigned: `GRP-Guest-App-Lab`

### 4) Guest Experience
- Guest accepted invitation from external mailbox
- Guest signed in to app portal
- Confirmed guest can see app tile and launch the app

### 5) Visibility in Entra
- Entra ID → Users → filter User type = Guest
- Confirmed guest shows as B2B and is a member of `GRP-Guest-App-Lab`

### 6) Remove Guest Access (Manual Cleanup)
- Removed guest from `GRP-Guest-App-Lab` and confirmed access is removed
- Optional: blocked sign-in or deleted guest to observe lifecycle behavior

## Evidence (what I check)
- Guest user object appears as User type = Guest (B2B)
- Group membership drives app tile visibility/access
- Removing from group removes app access
- Sign-in logs show guest authentication events under the enterprise app
