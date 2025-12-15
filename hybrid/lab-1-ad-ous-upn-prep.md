# Hybrid Lab 1: On-Prem AD Setup + OU/UPN Prep for Entra Sync

## Goal
Build a minimal AD domain and prepare clean OUs/users for hybrid identity syncing into Microsoft Entra.

## Build
- Created lab AD domain (ex: `corp.local`) on Windows Server (AD DS + DC promotion)
- Created dedicated OUs (instead of default Users container):
  - `OU=Lab Users`
  - `OU=Lab Groups`
- Created lab users in `OU=Lab Users`:
  - `alice`
  - `bob`
- Created security group in `OU=Lab Groups`:
  - `GRP-LAB-CloudUsers` (Global Security)

## UPN Suffix Alignment (critical)
- Added a routable UPN suffix (ex: `corpcloud.net`)
- Updated users to:
  - `alice@corpcloud.net`
  - `bob@corpcloud.net`

## Validation
- Users exist under the intended OUs
- Users have routable UPNs (not `@corp.local`)
- Group membership is correct (`GRP-LAB-CloudUsers` contains Alice/Bob)

## Why this matters (real-world)
- You almost never sync an entire domain—OU scoping reduces risk
- Routable UPNs prevent broken cloud sign-ins and confusion during SSO
