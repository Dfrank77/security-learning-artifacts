# Entra Lab 0: Tenant Basics, Users & Groups

## Objectives
- Get familiar with the Microsoft Entra admin center layout
- Create lab users and groups
- Practice the basic pattern: user → group → app/role

## Steps

### 1) Explore Entra Admin Center
- Visited: https://entra.microsoft.com
- Reviewed main areas:
  - Entra ID
  - Protection / Security
  - Identity Governance
  - Roles & admins
  - External Identities

### 2) Create Lab Users
- Entra ID → Users → All users → New user
- Created:
  - `alice.lab@...` (standard user)
  - `bob.lab@...` (standard user)
- Set temporary passwords + required password change at first sign-in

### 3) Create a Lab Group
- Entra ID → Groups → New group
- Type: Security group
- Name: `GRP-LAB-All-Employees`
- Members: Alice, Bob

### 4) (Optional) Assign a Low-Privilege Directory Role to the Group
- Entra ID → Roles & admins → selected a low-priv role (e.g., Reports Reader)
- Assigned the role to `GRP-LAB-All-Employees` (group-based assignment)

### 5) Validate
- Signed in as Alice
- Confirmed successful sign-in and user appears in Entra directory/sign-in context

## Evidence (what I check)
- User object exists and shows sign-in activity in logs
- Group membership reflects correctly
- Role assignment shows “assigned to group” (not directly to user)
